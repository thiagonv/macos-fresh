# <img src="https://cdn.rawgit.com/d3v1an7/fresh/master/logo.svg" alt="fresh" width="30%" />

A super opinionated Ansible playbook (with bash bootstrap) that gets me up and running after a fresh install of OS X (and soon macOS!) :ok_hand:

It's unlikely that the applications and system defaults will suit your purposes exactly, but hopefully you'll find it easy enough to follow along and customise on your own fork.

[Pull requests](https://help.github.com/articles/creating-a-pull-request/) welcome!

## Installation
Open terminal and run
``` sh
$ curl -L https://git.io/vzL6I | bash -s -- --first-run
```
> Hold on... isn't piping to shell a super [bad idea](http://www.seancassidy.me/dont-pipe-to-your-shell.html)?

Correct! But it is also pretty convenient :)  
I highly recommend reading and understanding what these scripts do prior to installing.

If the Ansible playbook ends early, you can safely kick it off again
``` sh
$ fresh --install
```

## Notes
- Has only been tested on OS X 10.11
- Many of the 10.11 updates were made on an established machine, so fresh installs may be bumpy
- Have considered (but not tested) zsh
- Requires at least Ansible 2

## WIP
### Misc
- Check out https://github.com/guarinogabriel/Mac-CLI
- Ansible organisation leaves a lot to be desired
  - Variables and tags not consistent
  - No link between applications and their configuration (if you remove iTerm from the homebrew cask array, the playbook will still try to configure it)
- Various race conditions need to be addressed (licence files are not available on first run, etc)
- Should detect if running script offline
- Update ~/.gitconfig
- Installation command is... not very pretty

### Manual steps
`System Preferences > Displays > Display`
- Resolution
  - Select `Scaled`
  - Change scale to `More Space`
    - Have tried `brew/screenresolution` and `brew/cask/cscreen`.
    - Both seem to change the resolution for the current session only, and do not scale the screen properly (text and edges are blurry)

`Finder > Preferences > Sidebar`
- Uncheck all, except the following
  - Favorites: iCloud Drive, AirDrop, Desktop, Home
  - Shared: Connected servers
  - Devices: Hard disks, External disks, CDs

`[New Finder window]`
- Add `~/Applications`
- Set order of sidebar
  - Desktop
  - Home
  - ~/Applications
  - AirDrop

## FAQ
### In summary, what does this actually do?
##### 1. [`install`](install)
- Ensure your system meets base requirements
- Install
  - [Xcode Command Line Tools](https://developer.apple.com/xcode/downloads/)
  - [Homebrew](http://brew.sh/)
  - [Git](http://git-scm.com/downloads/)
  - [Ansible](http://docs.ansible.com/intro_installation.html)
- Clone this repo into `~/.fresh/`
- Run the Ansible playbook below

##### 2. [`ansible/playbook.yml`](ansible/playbook.yml)
- Symlink `bin/fresh` to `/usr/local/bin/fresh`
- Install tools and applications
- Update system configuration files
- Update application configuration files



## Contributing
If you have any questions or suggestions, please either submit a pull request, create an issue ticket, or catch me on [Twitter](https://twitter.com/d3v1an7).

## Acknowledgements
Shout out to the many who have tread this ground before:
- boxen [our-boxen](https://boxen.github.com/)
- ptb [osx-setup](https://github.com/ptb/Mac-OS-X-Lion-Setup)
- mathiasbynens [dotfiles](https://github.com/mathiasbynens/dotfiles)
- necolas [dotfiles](https://github.com/necolas/dotfiles)
- rafeca [dotfiles](https://github.com/rafeca/dotfiles)
- pongstr [dotfiles](https://github.com/pongstr/dotfiles)
- paularmstrong [dotfiles](https://github.com/paularmstrong/dotfiles)

And these are the bee's knees:
- [homebrew](https://github.com/Homebrew/homebrew)
- [homebrew-cask](https://github.com/caskroom/homebrew-cask)
- [base16](https://github.com/chriskempson/base16)
