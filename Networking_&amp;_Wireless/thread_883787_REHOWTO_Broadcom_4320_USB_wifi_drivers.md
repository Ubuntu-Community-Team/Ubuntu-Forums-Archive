---
title: "RE:HOWTO: Broadcom 4320 USB wifi drivers"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by Dav Tir Luthier on 2008-08-08
Hi Guys,

I'm trying to follow this procedure:

[http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)

to get my Belkin F5D7051 Wireless USB Adapter set up.

The problem I have is probably very simple, I cannot connect directly to the internet with the system (Xubuntu Hardy) I'm setting it up on.

So where it says in the post to follow these steps:

mkdir bcm4320drivers
cd bcm4320drivers
wget [http://jooz.net/rndis/rndis_wlan-snapshot-20080509.tar.gz](http://jooz.net/rndis/rndis_wlan-snapshot-20080509.tar.gz)
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
cd rndis_wlan

I cannot directly implement the wget http:  step.

I can download, and have done, the .tar.gz file, and copy it onto the system, but as I'm a hopeless noob, I have no idea how to open it up and put it in the right place so I can then carry on with the rest of this solution.

If this makes any sense to you and you can help me, I would really appreciate it as I'm getting a bit frustrated with it.

Thanks in advance,

Dav.

---

### Post by Ayuthia on 2008-08-08
> **Dav Tir Luthier said:**
> Hi Guys,

I'm trying to follow this procedure:

[http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)

to get my Belkin F5D7051 Wireless USB Adapter set up.

The problem I have is probably very simple, I cannot connect directly to the internet with the system (Xubuntu Hardy) I'm setting it up on.

So where it says in the post to follow these steps:

mkdir bcm4320drivers
cd bcm4320drivers
wget [http://jooz.net/rndis/rndis_wlan-snapshot-20080509.tar.gz](http://jooz.net/rndis/rndis_wlan-snapshot-20080509.tar.gz)
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
cd rndis_wlan

I cannot directly implement the wget http:  step.

I can download, and have done, the .tar.gz file, and copy it onto the system, but as I'm a hopeless noob, I have no idea how to open it up and put it in the right place so I can then carry on with the rest of this solution.

If this makes any sense to you and you can help me, I would really appreciate it as I'm getting a bit frustrated with it.

Thanks in advance,

Dav.

The wget step is the downloading of the file so you have completed that step.  You just need to go to the next step which is to extract the file:
```
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
```That should create a folder called rndis_wlan where you will cd into.  Hope that helps.

EDIT:
In case you have not moved the downloaded file to bcm4320drivers, you will need to do this.  Assuming that you copied the file onto your Desktop and that you created bcm4320drivers in your home directory:
```
mv ~/Desktop/rndis_wlan-snapshot-20080509.tar.gz ~/bcm4320drivers
```
The ~ is a shortcut to your home directory.  The mv command is the move command.  It will move the file from the destop to bcm4320drivers.  If you would rather copy the file instead of move it, use cp instead of mv.

---

### Post by Dav Tir Luthier on 2008-08-08
Hi, and thanks.

Excuse the lack of knowledge here, but, when

```
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
```

what does 

```
-xvzf
```

represent?

In other words, how do I know I'm pointing to the downloaded file in the location I copied it to.

I hope this isn't really dumb, but I suspect it is..

Thanks a mil anyway,

Dav.

Just saw your edit above, disregard, and thanks again.

---

### Post by Ayuthia on 2008-08-08
> **Dav Tir Luthier said:**
> Hi, and thanks.

Excuse the lack of knowledge here, but, when

```
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
```

what does 

```
-xvzf
```

represent?

In other words, how do I know I'm pointing to the downloaded file in the location I copied it to.

I hope this isn't really dumb, but I suspect it is..

Thanks a mil anyway,

Dav.

Just saw your edit above, disregard, and thanks again.
I'all answer the xvzf command anyway:
x - extract
v - verbose
z - use gzip
f - file

If you are not for sure of a command that you are using in the Terminal, you can find some of the explanations by using the man command.  For example:
```
man tar
```This will display a manual page for that command.  You can press q to quit.  Another helpful command that some developers use is the --help extension.  For example:
```
tar --help
```This will usually list out the options that are available for that command.  

There are a lot of applications that use the man pages and have the --help option, but you will encounter a few that don't also.  Hope that helps you a little in the Terminal world!

---

### Post by Dav Tir Luthier on 2008-08-08
Great stuff!

I will spend the time learning the terminal when I'm up and running, and getting the wireless connection going is not a bad intro to it anyway, but your help has been invaluable and thanks for that explanation.

If you have any good links for further learning when I'm settled, it would be much appreciated too.

Thanks again,

Dav.

---

### Post by Ayuthia on 2008-08-08
> **Dav Tir Luthier said:**
> Great stuff!

I will spend the time learning the terminal when I'm up and running, and getting the wireless connection going is not a bad intro to it anyway, but your help has been invaluable and thanks for that explanation.

If you have any good links for further learning when I'm settled, it would be much appreciated too.

Thanks again,

Dav.
You might check out this link:
[http://ubuntuforums.org/showthread.php?t=426622](http://ubuntuforums.org/showthread.php?t=426622)
The third post in there has a link to some courses in linux.

Here is also another link that is helpful in getting started:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Dav Tir Luthier on 2008-08-16
OK!

Hi again,

I have followed this procedure:

[http://ubuntuforums.org/showthread.php?t=847226](http://ubuntuforums.org/showthread.php?t=847226)

all the way, and I still cannot connect with my Belkin F5D7051.

I am now wondering if I can undo all of the changes I have made by following that thread?

Why?

Well I have found this:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_&_v2?highlight=(f5d7051](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_&_v2?highlight=(f5d7051))

and would like to try it, and hope it works.

So can somebody please help me,

1: with recovering from the changes the first thread has had me make, and

2: with any advice on the second thread.

Thanks in advance,

Dav.

P.S. I also have a problem with the Network Settings interface, in that every time I open it it askes for authentication, then won't accept my password...:confused:

---

### Post by Ayuthia on 2008-08-16
> **Dav Tir Luthier said:**
> 

1: with recovering from the changes the first thread has had me make, and

It looks like you just compiled the rndis_wlan module.  You should be able to remove the module by doing the following:
```
echo blacklist rndis_wlan | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe -r rndis_wlan
sudo update-initramfs -u
```The first command will add "blacklist rndis_wlan" to the end of /etc/modprobe.d/blacklist.  This will prevent the module from loading.  The second command will remove the module that is currently loaded.  The third command will update the system so that it will not try to load rndis_wlan when booting.

> 2: with any advice on the second thread.
The only thing that I saw in the instructions is that it says to use ndiswrapper -d in version 1 and version 2.  That command does not seem to exist.  I think it is supposed to be ndiswrapper -a.  To see the list of commands for ndiswrapper, you can use ndiswrapper --help.  To verify that you have the right device, you will want to use:
```
lsusb
``` and see if it is a 13b1:000e or 13b1:0014.  If it is not, there is a chance that this set of instructions will not work.

If you have not installed ndiswrapper, you should be able to do this if you have the Ubuntu live CD.  You will need to install the liveCD to the repositories, update the repository package lists, and then install ndiswrapper.  When you do the first command, it will ask you to load the CD:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9

```

Hope that helps!

---

