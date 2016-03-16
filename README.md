# yada
Yet Another Dotfiles Arranger

# Installation

In your dotfiles' folder:

    git clone https://github.com/nobe4/yada.git .yada

Then, to install all links, binaries and run the install files:

    .yada/install

# What is this ?

I used for quite a time the [holman](https://github.com/holman/dotfiles)'s
dotfiles manager. I really liked the organisation around topics and custom file
extensions.

But I didn't like to have his whole configuration to fetch on installation, I
think the dotfiles manager should be separated from the actual dotfiles. So I
started working on this.

It follows roughly the same principles:

- One folder per topic (git, vim, tmux, ...)
- The `install` scripts are run on installation
- The `*.link` and `*.bin` are linked on install

That's all. Now, depending on your preferences, you may want to setup a `.zshrc`
sourcing all `*.zsh`, adding the `.yada/bin` folder to your path like in [this
file]().

By default, and for the seek of simplicity, during the link step, if a file
already exists, it backups it with another name, so you can manage by hand
afterwards.

# "Syntax"

### *.link
The file will be linked direcly into your `$HOME` folder, removing the trailing
`.link`.

e.g.

     vim/.vimrc.link -> ~/.vimrc
     tmux/.tmux.conf.link -> ~/.tmux.conf

### *.bin
The file will be linked into the `.yada/bin` directory, which I recommand you
add into your path to use all defined scripts. The same naming transformation applies:

e.g.

    git/git-time.bin -> .yada/bin/git-time
    zsh/ctrl-z.bin -> .yada/bin/ctrl-z

### install
The file will be run when you run the install script.

e.g.

    vim/install
    tmux/install

# Wait, but ... (aka FAQ)

- How about the dependencies, if I have to run a specific install file before
    all others (e.g. install homebrew) ?

    Just name your folder `0_homebrew`, it will be used first when searching all
    the install files.

- How do I configure my `.*shrc` file to work with this ?

  The structure follows the same as Holman's one, so you can clearly inspire
  yourslef with this
  [.zshrc.symlink](https://github.com/holman/dotfiles/blob/master/zsh/zshrc.symlink).
  I don't want to add this file into the yada project because you may not want
  it, it really depends on your needs.

_Other questions ..._

# Contribute

This is clearly a work in progress, it only works for `zsh` right now, but I
plan on adding some new features as well as being able to use on other shells.

Fell free to open an issue or a pull request, any contribution is welcome!

# License

[MIT](https://github.com/nobe4/yada/blob/master/LICENSE)
