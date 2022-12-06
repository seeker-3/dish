# Rush

A simple package for integrating shell scripts into deno, because sometimes you want a full programming language when working with shell scripts.

## Examples

Predefined shells include: `bash`, `fish`, `sh`, `zsh`

```ts
import { bash } from 'rush'

const world = 'World'

const stdout = await bash`
  echo Hello ${world}
`

console.log(stdout) // Hello World
```

Or for custom commands

```ts
import exec from 'rush'

const stdout = await exec('nu')`
  ls | sort-by size | reverse
`
```

```ts
import exec from 'rush'

const stdout = await exec('python3.11')`
print("Hello ${world}")
`

console.log(stdout) // Hello World
```

Basically the template string gets piped into whatever command is specified in the `exec` function. If you can pipe code into it, you can run it with rush.

```sh
echo 'print("Hello World")' | python3.11
```
