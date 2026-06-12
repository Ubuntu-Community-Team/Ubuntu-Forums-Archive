---
title: "creating an alias"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by SINZAR on 2009-04-27
I'm using my ubuntu distro as a media center with ftp. 

I upload the files to it and then I have to move those uploaded files into their proper directory. The paths to the directories are long and I don't like having to type it out each time. 

How would I create an alias of a path so that rather than typing mv file long/path/to/dir it could be something easier like mv file alias ?

---

### Post by mgranet on 2009-04-27
[http://www.tuxradar.com/content/linux-tips-every-geek-should-know](http://www.tuxradar.com/content/linux-tips-every-geek-should-know)

See #27

---

### Post by lavinog on 2009-04-27
you could also make a symlink to the folder on your home folder
```
 ln -s long/path/to/dir /home/user/shortname
```
this way you can just 
```
mv filename ~/shortname
```

---

### Post by lavinog on 2009-04-27
I don't think aliases will do what you want them to do, but if you want to know a trick about setting up aliases:
```
gedit .bashrc
```
scroll down till you see this:
```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

```
You can add the alias here this way it stays everytime you login to a bash terminal
also remove the # for ll. It is pretty handy

---

