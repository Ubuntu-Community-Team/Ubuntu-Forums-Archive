---
title: "More BCM4306 Issues"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by Sweet Mercury on 2007-05-20
I'm at the end of my rope with the wireless issues here.

For background:

I tried [This walk-through](http://ubuntuforums.org/showthread.php?t=201902) about a week ago to insall ndiswrapper to get my wireless card to work. Each step went off seemingly without an issue (or at least without an error message). Unfortunately, the only result was that Ubuntu no longer recognized that my laptop had a built in wireless card.

My next step was to uninstall the ndiswrapper using this code:
```
sudo aptitude remove ndiswrapper-common
```

But Ubuntu still doesn't see that I have a wireless when I go into my wireless settings. The system *does*, however, recognize that I have the card under **System --> Preferences --> Hardware Information** as well as when I use the *lspci* command.

I then tried to reinstall ndiswrapper (in case I had done anything wrong) and I got this error message:
```
mason@mason-laptop:~$ sudo rmmod bcm43xx
Password:
ERROR: Module bcm43xx does not exist in /proc/modules
mason@mason-laptop:~$ sudo rmmod bcm4306
ERROR: Module bcm4306 does not exist in /proc/modules
mason@mason-laptop:~$
```

I'm now at a loss. I'm reluctant to do the firmware flash because I need to be able to dual boot in windows and still have wireless capabilities there.

So, what's next? Can I reinstall the kernel for Feisty without too much hassle, to at least start back with a clean slate? Or do I have to uninstall Ubuntu entirely and start from scratch? I'm new to Linux as well, so I'm sketchy as to exactly how that works.

I don't mind reinstalling if I must. I'm still experimenting with Linux and I haven't done anything of value with it yet. And I can lose the crap I've put on here (it's backed up on my desktop anyway).

---

### Post by Kobalt on 2007-05-20
The error message you get is actually good : we don't want the bcm43xx modules, if you chose ndiswrapper. The *sudo rmmod bcm43xx* command is supposed to deactivate this module in case it's there.
You can go on to the next step.

---

### Post by Sweet Mercury on 2007-05-20
> **Kobalt said:**
> The error message you get is actually good : we don't want the bcm43xx modules, if you chose ndiswrapper. The *sudo rmmod bcm43xx* command is supposed to deactivate this module in case it's there.
You can go on to the next step.

Hmm, I didn't get that error the first time, maybe that was the issue?

The walk-through isn't specific, but is the command *sudo rmmod bcm43xx* or is it *sudo rmmod bcm4306* (my specific module)?

Either way, thanks, I'll try this when I get home.

---

### Post by Sweet Mercury on 2007-05-20
Ok more issues.

Here's where I'm at so far

```
mason@mason-laptop:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
mason@mason-laptop:~$ sudo rmmod bcm43xx
Password:
mason@mason-laptop:~$ ech 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
bash: ech: command not found
mason@mason-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
mason@mason-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.1kB of archives.
After unpacking 225kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ndiswrapper-common ndiswrapper-utils-1.9
Install these packages without verification [y/N]? y
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 93215 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
mason@mason-laptop:~$ ndiswrapper -l
mason@mason-laptop:~$ 
mason@mason-laptop:~$ sudo ndiswrapper -i ~/home/mason/bcmwl5.zip_FILES/bcmwl5.inf
installing bcmwl5 ...

couldn't open /home/mason/home/mason/bcmwl5.zip_FILES/bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

mason@mason-laptop:~$ sudo ndiswrapper -i /home/mason/bcmwl5.zip_FILES/bcmwl5.inf
driver bcmwl5 is already installed
mason@mason-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
mason@mason-laptop:~$ 
```

Why would the driver be invalid?

According to the walk-through, this is what it should say on the *ndiswrapper -l* should bring this result:

```
mason@mason-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5                      driver present, hardware present
```

So what now? I downloaded the right dirver (32 bit) and I made sure that the .sys file was there as well.

The ZIP file with the driver came with a bcmlw5a.inf and .sys file as well, should those be what I use for the driver in Feisty?

---

### Post by Sweet Mercury on 2007-05-20
> **Sweet Mercury said:**
> 
The ZIP file with the driver came with a bcmlw5a.inf and .sys file as well, should those be what I use for the driver in Feisty?

That was it! I tried it on a whim and it worked!

I had to manually configure (roaming mode was detecting my network, but not connecting, I'll deal with that issue later).

This is what the *ndiswrapper -l *command gives me now:

```
mason@mason-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
bcmwl5a : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
mason@mason-laptop:~$ 
```

Not that it's that important, but can I delete the original files I unzipped, or do I have to leave them in the home folder I created for them, and how do I delete the "bcmwl5" driver?

Thanks in advance for any help!

---

### Post by Count Doofus on 2007-10-21
TYPE THE DRIVER NAME IN THE CORRECT CASE !!!!!

 had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#! I hate Case Sensitive !!!

I only Wasted three days figuring it out .:mad:

---

