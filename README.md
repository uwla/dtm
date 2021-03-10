# DTWM - DOT FILES MANAGER

A simple script to manage dot files.

## DESCRIPTION

dtm is a shell script to manage configuration files (also known as dot files) in your home directory. It is simple, flexible, and can be extended to be used with GIT.

dtm aims to track only files in the user's home directory. It tracks configuration files by keeping a list of the path of those files relative to the $HOME directory.

## COMMANDS

**add PATH**: Start tracking one or more files.

**rm PATH FLAGS**: Stop tracking the given files. If the flag '--all' is present, remove all files from the track list.

**list, ls **: List which files are being tracked

**ln, link, DIR FLAGS**: Create links of all files being tracked to DIR. If the flag '--symbolic' is present, then it will create symbolic links. Otherwise, it will create hard links

**cp, copy DIR**: Copy all files being tracked to the specified directory.

**sync DIR**: Copy (or create links to) all files in DIR whose relative path to DIR is in the list of tracked files. If the flag '--symbolic' is present, then it will create symbolic link

**edit, -e**: Edit the list of files being tracked manually.

## EXAMPLES

Add single file to track list:

```
dtm add ~/.bashrc
```

Add multiple files to track list:

```
dtm add ~/.config/ranger/*
```

Remove file from track list:

```
dtm rm .config/i3/config
```

Remove files from track list:

```
dtm rm ~/.vimrc/*
```

Remove all tracked fiels from track list:

```
dtm rm --all
```

Create hard links of tracked files to specified dir:

```
dtm ln my-projects/github/dotfiles
```

Create symbolic links of tracked files to specified dir:

```
dtm ln my-projects/github/dotfiles --symbolic
```

Copy tracked files to specificied dir:

```
dtm cp my-projects/github/dotfiles
```

Copy files from DIR to `$HOME` directory whose path relative to DIR is in the track list:

```
dtm sync my-projects/github/dotfiles --copy
```

Create hard links of file from DIR to `$HOME` directory whose path relative to DIR is in the track list:

```
dtm sync my-projects/github/dotfiles 
```

Create symbolic links of file from DIR to `$HOME` directory whose path relative to DIR is in the track list:

```
dtm sync my-projects/github/dotfiles 
```

## ENVIRONMENT VARIABLES

**DTM_CONFIG_HOME**: The path where to store data files, such as the list of tracked files. By default it is `$XDG_CONFIG_HOME/dtm`. If `$XDG_CONFIG_HOME` is unset, then `$DTM_CONFIG_HOME` default to `$HOME/.local/share/dtm`.

**DTM_GIT_DIR**: The path of the default git directory. This is used as a fallback if DIR is not specified for the dtm's commands ln, cp, and sync.

## LICENSE

Do whatever you wish with the code of dtm.

## AUTHOR

Andre Souza Abreu.
