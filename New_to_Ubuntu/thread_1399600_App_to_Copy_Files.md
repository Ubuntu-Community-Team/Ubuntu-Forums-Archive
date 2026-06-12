---
title: "App to Copy Files"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by FerretDefunct on 2010-02-05
I'm looking for an application to copy files from one location to another, something similar to Windows' TeraCopy. I frequently transfer large files from a Windows box to my netbook (running Ubuntu 9.10) across the network. My problem when using the basic copy/paste in Ubuntu is that the transfer can fail or hangup if there's a hiccup or something on the network.

I'd really like to find something that has the ability resume transfers and check for errors. I'm a complete newbie to Linux, so there's probably already a utility in place to do this. If it's command line based I'd appreciate it if somebody could throw the syntax at me for accessing networked PCs. If it helps the files are stored in a PC named "Minion" on the network in a folder named "Data".

Thanks in advance for any help you can give.

---

### Post by Ankka7 on 2010-02-08
How about Grsync

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by t0p on 2010-02-08
I've seen a lot of people on these forums suggest a program called **rsync**.  I don't know if it's installed on Ubuntu by default - I've got it on my computer and I can't remember installing it; but that doesn't mean much!  You can find out if it's installed on your machine by opening a terminal and typing in the command:

```
which rsync
```If it's already installed you'll get output something like this:

```
t0p@phobos:~$ which rsync
/usr/bin/rsync

```If it isn't already installed, you can get it with the command:

```
sudo apt-get install rsync
```To see its syntax, check out the manpage; command:

```
man rsync
```

**grsync**, as suggested by Ankka7 above, is basically a graphical front-end for rsync.  According to Synaptic: "It currently supports only a limited set of the most important rsync features, but can be used effectively for local directory synchronization."  You can install it with the command:

```
sudo apt-get install grsync
```

---

