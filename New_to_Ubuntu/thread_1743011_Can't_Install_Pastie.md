---
title: "Can't Install Pastie"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by perito on 2011-04-29
I'm trying > sudo add-apt-repository ppa:hel-sheep/pastie

but im getting

> ubuntu@ubuntu-laptop:~$ sudo add-apt-repository ppa:hel-sheep/pastie
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 68B9B7F6B51298512D6B5A8993B9ADE3DE4CA452
gpg: requesting key DE4CA452 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


any idea what's wrong ? how to install it ?

---

### Post by Lateralis on 2011-04-29
As far as I know, you're doing nothing wrong.  The command is correct.  But it looks like there is a problem with that particular ppa key server.

---

### Post by perito on 2011-04-29
any other way to install pastie ?

---

### Post by oldos2er on 2011-04-29
I don't know if add-apt-repository adds the repository if it fails to connect with the keyserver, but you could try ```
sudo apt-get update && sudo apt-get install pastie
```

---

### Post by madjr on 2011-04-29
you could also try glipper

[http://www.webupd8.org/2011/04/glipper-gets-ubuntu-appindicator.html](http://www.webupd8.org/2011/04/glipper-gets-ubuntu-appindicator.html)

---

### Post by mork_on_tour on 2011-05-03
Me too, I am trying to install Pastie.

add-apt-repository works, but the repository has no package for natty, so apt-get update fails ("Not found"). Not sure if i'll try to modify the repository line in order to let it use maverick

Glippy won't be installed in my system because of Mono...

EDIT: I just noticed that glipper has been updated (before sometimes it failed to start at boot): it has all I need and I am acquainted with it, so I will use the old glorious glipper!

---

