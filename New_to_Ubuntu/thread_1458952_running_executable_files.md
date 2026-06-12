---
title: "running executable files"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by dwhite on 2010-04-20
hi i'm new to linux and ubuntu i am currently using Ubuntu 9.10 on a one year old HP Pavilion with a 2GHz Pentium Dual Core.  I am having trouble running software i download from **synaptic package manager**.

the latest example is... i have downloaded the programs** morse** and **aldo** from the symaptic package manager (amateur universe).  I find the programs (executable files) morse and aldo in **usr/bin,** double clicking etc. won't make them run.  do i have to download all the packages in amateur universe to make sure i have all the associated files needed? someone suggested that i needed to change the names of the files...right now the files are simply usr/bin/aldo and usr/bin/morse.

any help would be appreciated O:)

---

### Post by sisco311 on 2010-04-20
Hi and welcome to the forums!

morse & aldo are [CLI]("http://en.wikipedia.org/wiki/Command-line_interface") applications. You have to run them from a terminal (Applications -> Accessories -> Terminal), i.e.:

```
morse -i
```
or
```
aldo
```

For more info, see:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[uhelp]community/UsingTheTerminal[/uhelp]
[thread=801404]New to Ubuntu? Start here...[/thread]

---

### Post by lisati on 2010-04-20
Moved to "Absolute Beginner Talk"

---

### Post by kinkajou45 on 2010-05-06
Aldo works fine but morse wants chmod on /dev/console. 

Terminal Output:
morse -i
You have no permissions to use /dev/console (chmod a+w).
Can't access speaker.

I've been through the Morse manual and note that permissions on /dev/console need to be changed to a+w.  I've been through the forum (checked out puntercam's thread from today) and gone into launchpad, the resource page for morse 2.1(2005), learnlinux.tsf.org,linuxreviews.org and a few other sites for specific instructions on how to format a script to deal with the problem.  

BTW, is /dev/console tied into grub? I'm reluctant to go any further without some advice.

---

### Post by NT_CRASH on 2010-05-06
Have you tried running the app as root.

I installed morse and got the same error about /dev/console permissions.

Executed as root and no error. Not really sure what morse is meant to do but no further error messages.

sudo -s morse -i

---

### Post by Mike'sHardLinux on 2010-05-06
Running apps as root is generally not good practice. I would follow kinkajou45's advice first and see if that works.

---

### Post by kinkajou45 on 2010-05-08
Hi, all. Let me clarify: I found the chmod a+w reference in the morse manual. I was hoping someone on the forum would post a script to do the chmod change on /dev/console permissions (I'm not lazy, just chicken when it comes to altering system scripts without specific guidance from Those Who Know)).  I received the distinct impression that the settings for /dev/console  reside somewhere in grub, which is why I won't go any farther on my own. 

So in addition to the original problem, getting morse to run, we now have questions on  (1)the terminal script for chmod for /dev/console permission change, and (2) are /dev/console settings put into place at boot (part of grub):  if so, are there caveats to altering default.

I hope I asked the questions properly. BTW jmrweb has a multipage thread on a ham question and has a link to explore.ttps://wiki.ubuntu.com/UbuntuHamsMembers

---

