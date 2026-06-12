---
title: "Xbmc"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by majnu on 2010-02-26
Hi Please forgive me first of all if I have not only posted in the wrong section but ultimately in the wrong forum.
 
I have installed XBMC Live to use on my Acer Revo R3600 NetTop which I believe uses Ubuntu.
 
I am trying to install an the wireless application and get the following:-
 
" To run a command as administrator (user "root"), use "sudo <commad>". See "man sudo_root" for details.
 
E: could not open lock file /var/lib/dpkg/lock - open (13: permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/), are you root?
 
What do I do please, as I am trying to get the wireless drivers/application using:-
 
"apt-get install wicd"
 
Sorry but I am a complete noob and don't even know where to turn.

---

### Post by Nimless on 2010-02-26
try with 

```


sudo apt-get install wicd


```

---

### Post by spectralblue on 2010-02-26
> **Nimless said:**
> try with 

```


sudo apt-get install wicd


```

Also make sure to get a copy of the Ubuntu Pocket Guide at: [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

It sure helped me a lot!

---

### Post by majnu on 2010-02-26
> **Nimless said:**
> try with 
 
```

 
sudo apt-get install wicd
 

```
 
when i typed in "sudo apt-get install wicd" the reply was

E: couldn't find package wicd

---

### Post by majnu on 2010-02-26
> **spectralblue said:**
> Also make sure to get a copy of the Ubuntu Pocket Guide at: [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
 
It sure helped me a lot!
 
Thanks I will check that out. ;)

---

### Post by majnu on 2010-02-26
Sorry to be a pain but I have advanced a bit and thought I'd share the joy. This is what I did:-
 
Sudo Su (Switched User to Admin) - This was the important bit.
 
First, make sure you got all your files up to date. Type in a terminal:
apt-get update
 
Let that run, and once its done, type into terminal:
apt-get upgrade
 
Once that finished, restart your computer. Again open up terminal and type:
apt-get install wicd
 
Reboot 
 
It all installed but now where do I see my wireless options in xbmc?
 
Thanks
 
By the way I am using XBMCLive Freak version 13.

---

### Post by spectralblue on 2010-02-28
Great!

I'm not sure if you know but the command

```
sudo su
```means that you're switching to the root account. It's pretty handy if you don't want to type "sudo" a lot with administrative commands. 

But if you're doing just a handful of things, I'd recommend typing the regular commands like "sudo apt-get update" and "sudo apt-get install ..."  just so you don't make any accidental changes to your system.

If you type sudo su, you're switching to the root account and you can delete pretty much any file in the system and make changes that you otherwise wouldn't be able to do to crucial system files. So make sure you log off the root account by typing "exit" or "su username"

Oh yes ALWAYS type

```
sudo apt-get update
```first, before running any apt-get commands. This updates the repository list in your system, so it knows where to get the software. You just need to do this once, and not before each apt-get command, or if you added a new repository. The Pocket Guide also explains this, and root powers and synaptic and even command lines. :D

Sorry I don't really know how XBMC desktop works? Try opening a command line and type 

```
gksu wicd
```perhaps that works to open the GUI of wicd?

---

