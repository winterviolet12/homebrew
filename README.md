## HomeBrew

### 0. site
#### 1) homepage : [https://brew.sh](https://brew.sh)
#### 2) formulae : [https://formulae.brew.sh](https://formulae.brew.sh)


### 1. install

#### 1) Homebrew - packages (wget, cask, mas ...)
~~~bash
➜  ~ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
~~~
#### 2) cask - applications from Web (VSCode, Chrome, Firefox ...)
~~~bash
➜  ~ brew install cask
~~~
#### 3) mas - applications from AppStore (Xcode, KakaoTalk ...)
~~~bash
➜  ~ brew install mas
~~~
#### 4) file [[brew_install.sh](./files/brew_install.sh)]
~~~bash
#!/bin/bash
# homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
# cask
brew install cask
# mas
brew install mas
~~~


### 2. commands

#### 1) brew
~~~bash
➜  ~ brew
Example usage:
  brew search [TEXT|/REGEX/]
  brew info [FORMULA...]
  brew install FORMULA...
  brew update
  brew upgrade [FORMULA...]
  brew uninstall FORMULA...
  brew list [FORMULA...]

Troubleshooting:
  brew config
  brew doctor
  brew install --verbose --debug FORMULA

Contributing:
  brew create [URL [--no-fetch]]
  brew edit [FORMULA...]

Further help:
  brew commands
  brew help [COMMAND]
  man brew
  https://docs.brew.sh
~~~
#### 2) cask
~~~bash
➜  ~ brew cask
Homebrew Cask provides a friendly CLI workflow for the administration
of macOS applications distributed as binaries.

Commands:

    --cache    display the file used to cache the Cask
    audit      verifies installability of Casks
    cat        dump raw source of the given Cask to the standard output
    create     creates the given Cask and opens it in an editor
    doctor     checks for configuration issues
    edit       edits the given Cask
    fetch      downloads remote application files to local cache
    home       opens the homepage of the given Cask
    info       displays information about the given Cask
    install    installs the given Cask
    list       with no args, lists installed Casks; given installed Casks, lists staged files
    outdated   list the outdated installed Casks
    reinstall  reinstalls the given Cask
    style      checks Cask style using RuboCop
    uninstall  uninstalls the given Cask
    upgrade    upgrades all outdated casks
    zap        zaps all files associated with the given Cask

See also "man brew-cask"
~~~
#### 3) mas
~~~bash
➜  ~ mas
Available commands:

   account     Prints the primary account Apple ID
   help        Display general or command-specific help
   home        Opens MAS Preview app page in a browser
   info        Display app information from the Mac App Store
   install     Install from the Mac App Store
   list        Lists apps from the Mac App Store which are currently installed
   lucky       Install the first result from the Mac App Store
   open        Opens app page in AppStore.app
   outdated    Lists pending updates from the Mac App Store
   reset       Resets the Mac App Store
   search      Search for apps from the Mac App Store
   signin      Sign in to the Mac App Store
   signout     Sign out of the Mac App Store
   uninstall   Uninstall app installed from the Mac App Store
   upgrade     Upgrade outdated apps from the Mac App Store
   vendor      Opens vendor's app page in a browser
   version     Print version number
~~~

### 3. backup & restore

##### 1) brew bundle

~~~bash
➜  ~ brew bundle --help
Usage: brew bundle subcommand

Bundler for non-Ruby dependencies from Homebrew, Homebrew Cask, Mac App Store
and Whalebrew.

brew bundle [install]

Install or upgrade all dependencies in a Brewfile.

brew bundle dump

Write all installed casks/formulae/images/taps into a Brewfile.

brew bundle cleanup

Uninstall all dependencies not listed in a Brewfile.

brew bundle check

Check if all dependencies are installed in a Brewfile.

brew bundle exec command

Run an external command in an isolated build environment.

brew bundle list

List all dependencies present in a Brewfile. By default, only Homebrew
dependencies are listed.

        --file                       Read the Brewfile from this file. Use
                                     --file=- to pipe to stdin/stdout.
        --global                     Read the Brewfile from ~/.Brewfile.
    -v, --verbose                    install output is printed from commands
                                     as they are run. check prints all missing
                                     dependencies.
        --no-upgrade                 install won't run brew upgrade on
                                     outdated dependencies. Note they may still
                                     be upgraded by brew install if needed.
    -f, --force                      dump overwrites an existing Brewfile.
                                     cleanup actually perform the cleanup
                                     operations.
        --no-lock                    install won't output a
                                     Brewfile.lock.json.
        --all                        list all dependencies.
        --brews                      list Homebrew dependencies.
        --casks                      list Homebrew Cask dependencies.
        --taps                       list tap dependencies.
        --mas                        list Mac App Store dependencies.
        --whalebrew                  list Whalebrew dependencies.
        --describe                   dump a description comment above each
                                     line, unless the dependency does not have a
                                     description.
        --no-restart                 dump does not add restart_service to
                                     formula lines.
        --zap                        cleanup casks using the zap command
                                     instead of uninstall.
    -h, --help                       Show this message.

~~~

##### 2) backup

~~~bash
➜  ~ brew bundle dump
➜  ~ more Brewfile
more Brewfile
tap "adoptopenjdk/openjdk"
tap "caskroom/cask"
tap "caskroom/fonts"
...
brew "apktool"
brew "apr"
brew "apr-util"
...
cask "adoptopenjdk11"
cask "adoptopenjdk12"
cask "adoptopenjdk8"
...
mas "KakaoTalk", id: 869223134
mas "Keynote", id: 409183694
mas "Xcode", id: 497799835
...
~~~

##### 3) restore

~~~bash
➜  ~ brew bundle
Installing adoptopenjdk/openjdk
Installing caskroom/cask
Installing caskroom/fonts
...
~~~

