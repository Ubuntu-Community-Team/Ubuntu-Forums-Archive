---
title: "help with terminal"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by hopeless8009 on 2010-05-27
Im still kind of new to Linux, but i have some time put into terminal. I would like to learn some new commands. could someone maybe give me a link to a refrence or tell me some cool commands. So far i know shut down and reboot.

---

### Post by patchwork on 2010-05-27
The Bash man pages are chock full o' good stuff.  Be prepared for a long read, though.

```
man bash
```

---

### Post by BoneKracker on 2010-05-27
Browse around in here:
[http://tldp.org/](http://tldp.org/)

You'll find some tutorials as well as documentation for commands.

Some basic commands.  To find out what these are, open the terminal and type man and then the command.  To learn how to use man, type man man.

For example, to learn about the "cd" command, you would type:
```
man cd
```

(documentation)
man
apropos
whatis

(navigation)
cd
ls
cp
mv

(viewing and editing text files)
less
nano


(finding and viewing properties of files)
which
file
ls -al
stat
locate
find

(networking)
ifconfig
ping
whois
traceroute

---

### Post by candtalan on 2010-05-27
One I use a lot on various machines to list what pci items are available is
lspci

similarly, for usb information
lsusb

---

### Post by EssexEagle on 2010-05-28
> **hopeless8009 said:**
> Im still kind of new to Linux, but i have some time put into terminal. I would like to learn some new commands. could someone maybe give me a link to a refrence or tell me some cool commands. So far i know shut down and reboot.

I learnt to use the terminal using [http://www.linuxcommand.org](http://www.linuxcommand.org) - good site IMO.

---

### Post by madmax75 on 2010-05-28
Check out the free online book "RUTE - Rute User's Tutorial and Exposition":

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

A pretty good source for Linux terminal commands IMHO.

---

### Post by BoneKracker on 2010-05-28
> **madmax75 said:**
> Check out the free online book "RUTE - Rute User's Tutorial and Exposition":

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

A pretty good source for Linux terminal commands IMHO.
++
I had forgotten about about rute.  That's an excellent introductory tutorial, if somewhat dated (goes into depth about uucp, for example).

---

