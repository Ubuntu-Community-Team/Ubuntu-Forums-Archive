---
title: "MN-720 wireless PCMCIA card on Edgy"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by bieber on 2007-02-08
Hello, all.  Sorry to bother y'all with another wireless setup thread, but I'm having some troubles getting my MN-720 wireless adapter working on my Edgy laptop.  I thought I was done with wireless for good when I got a proper wired network in my house, but now I find myself with a laptop, for which wireless would be mighty handy.  The last thing I set up was a Linksys USB adapter on my desktop, and the process pretty much consisted of blacklisting the driver that *tried* to handle the card, but failed, then setting up ndiswrapper to replace it.  On this machine, the first thing I did was rmmod bcm43xx, which I *think* is the only thing that was trying to handle the card, but I can't remember which file I edit to blacklist it.  Then I installed ndiswrapper and the ankh drivers for my card.  Now it won't let me modprobe ndiswrapper, though: I get this ```
bieber@bieber-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
mn720-ankh      driver present, hardware present 
bieber@bieber-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```
Does anyone know what the problem is?  Also, on the last machine where I set ndiswrapper up, it didn't work with network-manager, which I didn't care about at the time because I was only ever connected to one network, but with a machine that I'll be moving about, it'd be *really* handy.  Is there any way to get network-manager to play nice with ndiswrapper cards?

---

### Post by Corvo78 on 2007-02-08
Have you tried using ndiswrapper-utils-1.18 package instead of the 'regular' ndiswrapper-utils?
I remember that solved my 'Invalid argument' problem.

(Follow this link [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902) and have a look at 'problem 2'.)

---

### Post by bieber on 2007-02-08
Thank you!  Posting from a laptop wirelessly now.  Network manager's handling it like a champ, and all is well.  The only question I have now is, is there a way to remove the card while the system is running safely?  I've tried just pulling the card, and pulling it after rmmod'ing ndiswrapper, and in both cases my system's just froze beyond all recovery (had to reboot forcibly both times).  Is there some proper procedure for removing a PCMCIA card? (I've been using Ubuntu for ~1 year now, but this is the first time on a laptop)

---

### Post by Corvo78 on 2007-02-09
Glad it helped!
I have an internal wireless card... so I don't know how to disconnect a PCMCIA card.

Allthough I'd like to know too :)

---

### Post by jubane on 2007-02-09
I am using the same card on my laptop and am having the hardest time getting this to work. I went ahead and installed  sudo apt-get install ndiswrapper-utils-1.8

Once that is done i tried installing the drivers but this is where the problem starts the message I get is;

makoto@GhostShell:~$ sudo ndiswrapper -i /home/makoto/Files/mn720-ankh
Installing mn720-ankh
couldn't copy /home/makoto/Files/mn720-ankh at /usr/sbin/ndiswrapper-1.8 line 144.I

I uninstalled ndiswrapper-utils-1.8 and installed 1.1

It went better but not I am getting;

mn720-ankh      invalid driver!

I am new to Linux and have tired almost everything to get this card to work but no matter what I try it never works. Would you be able give me a step by step process of what you did to get your card??? 

Version of Utubu that I am using is 6.10 

Thanks

---

### Post by jubane on 2007-02-09
Also one more thing the place I got this driver that I am using is from;

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

They had a driver for mn720 card

Should I be using the drivers from the Microsoft cd would that work better???

---

### Post by sloarch07 on 2007-02-23
> **jubane said:**
> makoto@GhostShell:~$ sudo ndiswrapper -i /home/makoto/Files/mn720-ankh
Installing mn720-ankh
couldn't copy /home/makoto/Files/mn720-ankh at /usr/sbin/ndiswrapper-1.8 line 144.I

I uninstalled ndiswrapper-utils-1.8 and installed 1.1

It went better but not I am getting;

mn720-ankh      invalid driver!

I had this same problem.  Reinstall 1.8 and then use the command ```
sudo ndiswrapper -i /home/makoto/Files/mn720-ankh**.inf**
```

---

### Post by tclinus1 on 2007-12-20
I have installed the ndiswrapper common and utils and get the message that mn720-ankh is installed and then it list the device and the alternate driver.  If I type iwconfig it list the eth0 and shows the setting I put in.  However, I don't ever get a power or activity light on the pcmcia card like I did when it was installed in windows.  Does anyone have advice for getting this to work?

---

