---
title: "sudo path?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Ansible on 2009-03-02
So ubuntu supports ghc 6.8.2, but I want 6.10.1 in order to use some libraries.  I compiled that from source and installed it, ok.  But when I typed 'ghc', nothing happened.  So I added this to my path:

/usr/local/ghc-6.10.1/bin

Now I can type 'ghc' or 'runhaskell' and it works.  BUT, I need to type this:

sudo runhaskell Setup install

and sudo doesn't see runhaskell or ghc.  I can only run those commands without sudo.  

I tried adding code into the .profile of the root account to modify the PATH, but that doesn't work.  Any hints??

---

### Post by Temposs on 2009-03-02
It seems like you'd only have to run this once, so why don't you navigate directly to that path and run the executable:

```
cd /usr/local/ghc-6.10.1/bin
sudo ./runhaskell Setup install
```

---

### Post by Ansible on 2009-03-02
Heh good call.  I had to run that cmd in another folder though, but then this worked:

sudo /usr/local/ghc-6.10.1/bin/runhaskell Setup.hs install

Unfortunately now I need to sudo run a script which uses ghc.  I guess I could go through the script and edit every reference to ghc to have the full path, but there's got to be a better way!  Plus any time I install a haskell package it will try to build it, and the install will need to be sudo, so argh.

---

### Post by asmoore82 on 2009-03-02
how did you add to your PATH? - did you `export` your new PATH?

after compiling and installing software manually, it couldn't hurt to run ldconfig:
```
sudo ldconfig -v
```

for the sudo scripts, worst-case scenario you would just have to add a PATH line at the beginning of the script

Edit:
from `man sudo` - sudo does some "path" magic of it's own for security purposes -
you may simply need to edit "/etc/profile" to "have it your way"

---

### Post by Ansible on 2009-03-02
I put this stuff at the end of my .profile file:

[CODE]# set PATH so it includes .cabal private bin if it exists
if [ -d ~/.cabal/bin ] ; then
    PATH=~/.cabal/bin:"${PATH}"
fi

# set PATH so it includes .cabal private bin if it exists
if [ -d /usr/local/ghc-6.10.1/bin ] ; then
    PATH=/usr/local/ghc-6.10.1/bin:"${PATH}"
fi

export PATH
[/CODE

Although actually I had the export PATH before these statements to begin with.  I moved "export PATH" to the end and logged out and back in again, but still no sudo ghc...

---

### Post by asmoore82 on 2009-03-02
Ahaa!! - I've found something new I've not seen before - "/etc/login.defs"
the relevant section:
```
#
# *REQUIRED*  The default PATH settings, for superuser and normal users.
#
# (they are minimal, add the rest in the shell startup files)
ENV_SUPATH  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV_PATH PATH=/usr/local/bin:/usr/bin:/bin:/usr/games


```

at this point (knee-deep in /etc) ...
I'm liking my "tweak PATH in the actual script" suggestion more and more.

---

### Post by asmoore82 on 2009-03-02
quick testing for fun...

an interesting quirk of life is that you have to be careful with "sudo echo ..." statements -
they can mislead you because any $variables in those statements are substituted
by your unprivileged shell before sudo is invoked.
So, here I have a bare-bones shell script to poke the PATH: "~/bin/path"
```
#!/bin/sh

echo "$PATH"
```

and the simple but intriguing tests:
```
**asmoore@ubuntu-lenovo:~$** echo "$PATH"
/home/asmoore/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
**asmoore@ubuntu-lenovo:~$** sudo echo "$PATH"
/home/asmoore/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
**asmoore@ubuntu-lenovo:~$** path
/home/asmoore/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
**asmoore@ubuntu-lenovo:~$** sudo path
sudo: path: command not found
**asmoore@ubuntu-lenovo:~$** sudo ./bin/path 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```

and an amended test script, to make sure my solution is simple and workable: "~/bin/path"
```
#!/bin/sh

PATH="${PATH}:/home/asmoore/bin"
#^not exporting here is intentional - for security
# **this PATH is for this script only**

echo "$PATH"
```

and testing this:
```
**asmoore@ubuntu-lenovo:~$** path
/home/asmoore/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/asmoore/bin
**asmoore@ubuntu-lenovo:~$** sudo ./bin/path 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/home/asmoore/bin
```

---

