# pythoneda-tools-artifact/git-hook

Definition of <https://github.com/pythoneda-tools-artifact/git-hook>.

## How to run it

``` sh
nix run 'https://github.com/pythoneda-tools-artifact-def/git-hook/[version]'
```

## Usage

To run this tool, check the latest tag of this repository, and use it instead of the `[version]` placeholder below:

``` sh
nix run https://github.com/pythoneda-tools-artifact-def/git-hook/[version] [-h|--help] [-r|--repository-folder folder] [-e|--event event] [-t|--tag tag]
```
- `-h|--help`: Prints the usage.
- `-r|--repository-folder`: The repository folder the git hook is triggered.
- `-e|--event`: The event to send. Usually `StagedChangesCommitted`. See <https://github.com/pythoneda-shared-artifact/events>.
- `-t|--tag`: If the event is `TagPushed`, specify the tag.

## post-commit hook

``` sh
#!/usr/bin/env sh

REPO_DIR=$(command git rev-parse --show-toplevel)
command nix run https://github.com/pythoneda-tools-artifact-def/git-hook/[version] -- -r ${REPO_DIR} -e StagedChangesCommitted
```
