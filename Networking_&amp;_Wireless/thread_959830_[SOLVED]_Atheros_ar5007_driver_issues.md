---
title: "[SOLVED] Atheros ar5007 driver issues"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by riminicat on 2008-10-26
I know a lot of people are having issues with this but none of the other threads can solve my problem.

I'm on a shared wifi router with the other tenants in my apartment complex and we don't have access to the router.  As a result I cannot hook my laptop to the router to install the driver using an Ethernet cable.  Here's my question:

Can anyone provide a step by step walk through on how to download the files needed through windows so that I can mount the drive and install them when I'm in Ubuntu?  I can't connect to the internet without an Ethernet cable in Ubuntu!

Some information that might help:

I have an HP laptop.
It's 64 bit 
AMD processor
And again I cannot download the files using Ubuntu, only windows.

Please help and thanks in advance!

---

### Post by brigadoon on 2008-10-26
I did a quick google search and came across this tutorial...

[http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/ubuntu-804-enabling-atheros-ar5007-based-wireless/)

You can download build-essential from...

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

In place of the wget command you can download the driver by pasting the following into your browser...

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

I don't have your driver so I can't test it out. The instructions seem simple enough once you get the files. As with anything that requires experimentation, make sure you back up the important stuff. Good luck.

---

### Post by riminicat on 2008-10-26
Hey thanks, the driver file link is no longer valid, it only contains a readme file but I'll google for the new link and see what I can do!

---

### Post by brigadoon on 2008-10-26
The build-essential i386 link takes you to a list of servers. Just click on a server from North America and the file should download.

I am able to download the driver file.

I am using Firefox for a browser. Windows Explorer may be a problem if that's what you are using. You may be able to right click the link and use the save target as option if it pops up.

Hope this helps.

---

### Post by riminicat on 2008-10-26
Hey thanks I'm downloading the new version of the driver now, I've got every thing else.  Maybe I can dump window$ tonight!

---

### Post by riminicat on 2008-10-26
Alright now I get this:

Error: Dependency is not satisfiable: libc|libc-dev

I'm going to try and download the libc-dev file through windows too.  Here we go again.

---

### Post by riminicat on 2008-10-27
Hey thanks for the help.  After six months of being without Ubuntu (three of them without a computer) I am now online with Ubuntu again!  Funny thing, a lot of the files I needed were on the Ubuntu install disk.  I changed the some stuff to look in the cd drive for updates and installed all the files and programs I needed off of it!  Now if I could just remember the commands I used I can write a guide for others in the same boat as me.

---

