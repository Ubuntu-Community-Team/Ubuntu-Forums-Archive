---
title: "Trouble installing gparted"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by card_ace on 2009-01-30
I'm used to windows XP pro, so ubuntu is taking some getting used to.  I installed Ubuntu 8.10 to an external USB hard drive and I can't seem to figure out how to install gparted to it.  The main problem is that i can't get it on a computer that has internet access.  The only internet access i've managed to get it on is heavily filtered using Lightspeed Systems and it won't let me update it.  So my question is this:
1.) Is it possible to install gparted without internet access?
2.) If its not, is there a way for me to bypass the filter in ubuntu so i can update it?

---

### Post by drs305 on 2009-01-30
I am assuming this is a normal install and not wubi from within windows.

gparted should be on your ubuntu install. To start it you should be able to either go to System, Administration, Partition editor (which is gparted) or simply run:
```

gksudo gparted

```
When you hit ENTER, it will ask for your password. As you type, you won't see it being entered but that is for security reasons. Just type it and hit ENTER.

If you can't get it to run or don't think it is installed, it should be on the live CD. System, Administration, Synaptic Package Manager. Settings > Repositories. In the bottom pane the CdROM should be enabled. If it is, open a terminal and type:
```
sudo apt-get install gparted
```

---

### Post by card_ace on 2009-01-31
You're right, its a normal install i did from booting to the live cd.  Partition Editor isn't under the System, Administration, and when i tried to run it through the terminal it didn't do anything at all.  Then I tried to use the cd and I set it to check the cd in the package manager and when i typed in "sudo apt-get install gparted" this is what it said:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate

---

### Post by drs305 on 2009-01-31
I just booted to an Intrepid LiveCD without an internet connection and Partition Editor is 'installed' and listed. When you go to System, Administration, do you see about 20 items, beginning with "Authorizations" and ending with "Users and Groups"?  Partition Editor is listed about halfway down on mine...

:confused:

---

### Post by MarblePanther on 2009-01-31
On an Ubuntu Intrepid install, gparted is removed (as a part of the Ubiquity installer) and Parted (CLI) is left after the installation is complete.

I believe he wants the gparted GUI not parted's CLI.

Gparted used to stay after an installation, but I guess this changed with Intrepid.

If he has the livecd it will, of course be on there.

---

### Post by card_ace on 2009-02-01
If i boot from the LiveCD, then i can use the GParted Partition Editor.  If i boot from my hard drive i can't seem to find it.  Gparted isn't included in the 8.10 install, but its on the cd for when you're installing it.  Is there a way to install GParted onto my hard drive straight from the LiveCD?  Or can i download something on a windows computer to a small USB drive and install from there?

---

### Post by MarblePanther on 2009-02-01
Download this package of gparted on your windows machine (pick one of the closest mirrors) and move it to your usb key.  Just move it from the usb key to your ubuntu desktop and click on it and install.  It should appear in System, Administration, Partition Editor.

[http://packages.ubuntu.com/intrepid/i386/gpart/download](http://packages.ubuntu.com/intrepid/i386/gpart/download)

---

### Post by card_ace on 2009-02-02
ok i got it now.  i went to packages.ubuntu.com and found the download.  thanks to all that helped!

---

### Post by SanoTwo on 2009-09-30
Solved some of my problem, thanks. I've played with a live boot a few times.

Live boot- gparted is there, but now after an install (of 8.10) to P3 Intel board -nada.

I searched for gparted, found some 5 similar named files, three with .mo extensions - then navigated to /usr/share/app-install/desktop

No files before pyshell.desktop. Plenty after, all the way to zynaddsubfx.desktop

Did (Future) Linux Mag sell me a crap dvd? Thanks for any input. Whatta a pia.

---

### Post by drs305 on 2009-09-30
Sanotwo,

Welcome to Ubuntu and the Ubuntu forums.

In 8.10 gparted is on the LiveCD but you have to install it yourself after accomplishing a normal installation. It's in the *main* repository, which is enabled by default.

With an Internet connection:
```

sudo apt-get update
sudo apt-get install gparted

```

Once installed, in 8.10 it is located in the System, Administration menu under "Partition Editor".

---

### Post by SanoTwo on 2009-09-30
> **drs305 said:**
> Sanotwo,

Welcome to Ubuntu and the Ubuntu forums.

In 8.10 gparted is on the LiveCD but you have to install it yourself after accomplishing a normal installation. It's in the *main* repository, which is enabled by default.

With an Internet connection:
```

sudo apt-get update
sudo apt-get install gparted

```

Once installed, in 8.10 it is located in the System, Administration menu under "Partition Editor".drs305, thank you for the welcome!

Like the OP, I'm still trying to grasp the file structure for linux.  I don't have an internet connection for that machine yet. I'll use this machine.

Otherwise, fwiw, it just seems odd that there are no files in  /usr/share/app-installed/desktop that have alphabetical names before *pyshell.desktop*. Thanks.

---

### Post by drs305 on 2009-09-30
> **SanoTwo said:**
> Otherwise, fwiw, it just seems odd that there are no files in  /usr/share/app-installed/desktop that have alphabetical names before *pyshell.desktop*. Thanks.

I just checked both a clean install and a LiveCD running system and both have hundreds of entries in /usr/share/app-install prior to pyshell.desktop, so your suspicions are well founded.

If you can download a fresh copy of an Ubuntu .iso you would probably have better luck.

---

### Post by SanoTwo on 2009-09-30
Thanks for the feedback drs305.

---

### Post by SanoTwo on 2009-10-07
drs305,
Linux Pro mag returned my mail and they're sending me a new dvd. Should arrive in the next few days. Thanks again.

---  I'm installing on an Intel board, P3, 700Mhz, and a (mm, ata66 20 GB hdd -it's old  :) 512 MB of ram.

I got the DVD (8.10), same as previously, no install for gparted. 

I did manage to use a buddy's high speed connection and d/led the 9.04 release. It certainly installed faster on the same hardware. But it still doesn't care to install gparted.

FWIW, I'm fooling around with some data recovery on some windows hdds with testdisk and photorec. Nothing of any particular importance.  Thanks again.

---

### Post by rjmoon7 on 2013-04-07
i removed gparted and can not reinstall.  I tried rebooting GRUB but this error message comes out
~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gparted' has no installation candidate

Please Help

---

### Post by wildmanne39 on 2013-04-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

