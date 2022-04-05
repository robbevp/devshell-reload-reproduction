# Cached devshell isn't loaded

1. Open a terminal and cd into project
2. direnv runs, but devshell is not loaded
```
direnv: loading ~/Code/github-contributions/devshell/.envrc
direnv: using flake
direnv: using cached dev shell
direnv: export +IN_NIX_SHELL +NIX_BUILD_CORES +NIX_STORE +builder +dontAddDisableDepTrack +name +out +shellHook +stdenv +system ~PATH ~XDG_DATA_DIRS
```
3. Run `direnv reload` and see that devshell correctly loads
```
direnv: loading ~/Code/github-contributions/devshell/.envrc
direnv: using flake
warning: Git tree '/Users/robbevp/Code/github-contributions/devshell' is dirty
warning: Git tree '/Users/robbevp/Code/github-contributions/devshell' is dirty
direnv: renewed cache
🔨 Welcome to devshell

[general commands]

  devshell - Per project developer environments
  menu     - prints this menu

direnv: export +DEVSHELL_DIR +IN_NIX_SHELL +MY_VAR +NIXPKGS_PATH +PRJ_DATA_DIR +PRJ_ROOT ~PATH ~XDG_DATA_DIRS
```
3. Type `echo $MY_VAR` to verify devshell loaded

# Renewed cache breaks other shell
1. Open a new shell
2. direnv runs, but devshell is not loaded
3. Run `direnv reload` and see that devshell correctly loads
4. Go back to first shell and type any command
4. See that direnv reloads (but without ` +DEVSHELL_DIR`)
5. Run `echo $MY_VAR` and notice missing output

https://user-images.githubusercontent.com/48474670/161829397-0e0f9ecd-356c-4237-85a9-221b402becf3.mov
