---
title: "problem networking with winxp"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by donjo on 2008-08-30
i already setup networking and file sharing..


on winxp machine, i can see and get the file from ubuntu machine,
so it's ok laa

but the problem is i can't transfer the file from winxp while i'm using ubuntu,
error message said that it can't mount the folder on winxp...
so what is the solution to this problem?
and sometimes it not appear any folder of winxp that shared

---

### Post by donjo on 2008-08-30
no one can help me???

---

### Post by GepettoBR on 2008-08-30
do you have smbmount and the gvfs packages installed?

---

### Post by donjo on 2008-08-31
> **GepettoBR said:**
> do you have smbmount and the gvfs packages installed?

smbmount yes,
but what is gvfs ??
it's important?

---

### Post by GepettoBR on 2008-08-31
gvfs is the GNOME virtual filesystem, which should allow you to mount the shares via Nautilus. If that doesn't work, I can guide you through mounting them using the command line, which is a little more troublesome but not too much.

---

### Post by donjo on 2008-08-31
> **GepettoBR said:**
> gvfs is the GNOME virtual filesystem, which should allow you to mount the shares via Nautilus. If that doesn't work, I can guide you through mounting them using the command line, which is a little more troublesome but not too much.

how to install gvfs??
and how about the command line?
just tell the step ok?
thanks

---

### Post by donjo on 2008-08-31
> **GepettoBR said:**
> gvfs is the GNOME virtual filesystem, which should allow you to mount the shares via Nautilus. If that doesn't work, I can guide you through mounting them using the command line, which is a little more troublesome but not too much.

how to install gvfs??
and how about the command line?
just tell the step ok?
thanks

---

### Post by nero1111 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by GepettoBR on 2008-08-31
The command-line interface (CLI) is accessed via the Terminal. Click the Applications menu, then go to Accesories>Terminal to open it.

To install GVFS, just type the following into the Terminal, press Enter, then type your password and press Enter again: ```
sudo apt-get install gvfs gvfs-bin gvfs-fuse
```

Apt-Get wil take care of all the dependencies for you. When it asks if you want to continue, type Y and the press Enter. That will download and install the GVFS packages.

---

### Post by donjo on 2008-08-31
> **GepettoBR said:**
> gvfs is the GNOME virtual filesystem, which should allow you to mount the shares via Nautilus. If that doesn't work, I can guide you through mounting them using the command line, which is a little more troublesome but not too much.

how to install gvfs??
and how about the command line?
just tell the step ok?
thanks

---

### Post by GepettoBR on 2008-08-31
I have already answered your current question, please don't triple-post.

---

### Post by donjo on 2008-09-01
well,i got this error mesej

$ sudo apt-get install gvfs gvfs-bin gvfs-fuse
[sudo] password for scorps: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs is already the newest version.
gvfs-fuse is already the newest version.
The following NEW packages will be installed:
  gvfs-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.6kB of archives.
After this operation, 246kB of additional disk space will be used.
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) intrepid/main gvfs-bin 0.99.5-0ubuntu1 [41.6kB]
Fetched 41.6kB in 49s (846B/s)                                                 
Selecting previously deselected package gvfs-bin.
(Reading database ... 218480 files and directories currently installed.)
Unpacking gvfs-bin (from .../gvfs-bin_0.99.5-0ubuntu1_i386.deb) ...
Setting up gvfs-bin (0.99.5-0ubuntu1) ...
W: Duplicate sources.list entry [http://apt.wicd.net](http://apt.wicd.net) gutsy/extras Packages (/var/lib/apt/lists/apt.wicd.net_dists_gutsy_extras_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
scorps@scorps-laptop:~$

---

### Post by GepettoBR on 2008-09-01
Okay, it looks like you have repositories for both Intrepid and Gutsy on your sources.lst... that's messy.

Did you run sudo apt-get update like the error message instructed?

---

### Post by donjo on 2008-09-01
scorps@scorps-laptop:~$ sudo apt-get install gvfs gvfs-bin gvfs-fuse
[sudo] password for scorps: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs is already the newest version.
gvfs-bin is already the newest version.
gvfs-fuse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scorps@scorps-laptop:~$ 

how about this one???

---

### Post by GepettoBR on 2008-09-01
Like the output says, it means you've already managed to install them. If it's still not working, we'll have to try using smbmount. Does the computer you're trying to connect to have a static IP?

---

### Post by donjo on 2008-09-07
> **GepettoBR said:**
> Like the output says, it means you've already managed to install them. If it's still not working, we'll have to try using smbmount. Does the computer you're trying to connect to have a static IP?
not have static ip.
all using auto ip.
so what ?

---

### Post by GepettoBR on 2008-09-07
> **donjo said:**
> not have static ip.
all using auto ip.
so what ?

So, if we want to easily access your shares, static IPs will make things really easy. The simplest way to do that would be to reserve the IPs with your router's DHCP server, but if you don't know how to do that you can assign static IPs directly in your computers. Here's a site explaining how to do that in Windows:

[http://www.portforward.com/](http://www.portforward.com/)

---

### Post by gregphil on 2008-09-07
You might look at the end of this thread:

[http://ubuntuforums.org/showthread.php?t=909453](http://ubuntuforums.org/showthread.php?t=909453)

You have not specified enough details yet to know if your problem is exactly the same as the formum related issue with the nautilus network file browser.

---

