---
title: "What's Happened?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by grekei on 2009-01-17
I have been running a clean install of 8.10 on a Dell laptop, their are no other systems on the machine.It has not had any Windows system on it since I scrubbed out Vista over a year ago.It has had A few GNU linux systems on it mainly Ubuntu or cousins of Ubuntu.Always full installs,always wiped the hard disk I have never partitioned the hard drive.
2 days ago I tried to boot up and got a Windows error message (YES a Windows error message!)can't remember what it was, I got such a shock I powered off and rebooted.Yes you guessed it, Grub error  message 17 (I now know what this means)but it is usually associated with dual boot systems as far as i can tell.Tried to get in via CD and command line to be told their is no shell!
I have reinstalled (did not have time to waste,needed the machine and my data was backed up on another HD) no partitions were detected on reinstall and I cannot find any obvious damage to the HD.
Can any one tell me where this Windows crap came from.Was it always on the drive/still on the drive?Have I been attacked in some way or am I just paranoid.
Would appreciate a few clues/solutions to this 

Cheers Greg

---

### Post by Terl on 2009-01-17
Do you recall the message?  It may have been a BIOS related message.

Also, Grub 17 error indicates grub did not recognize the format of the partition you tried to boot.  It does not necessarily relate to windows.  

I am thinking something else may have affected your partitioning setup.  Did you make any other changes possibly?

---

### Post by grekei on 2009-01-17
Thanks for the reply.
The message definitely started "Windows can't find...... and possibly .dll something" so I am pretty confident it was not the bios.The message did not go onto run Grub.Grub only appeared with the error message after I rebooted from powering off.I went into the bios after this and ran a system check all was reported OK including the hard drive.My fresh install has been running faultlessly for 2 days now and I made no changes in the bios.
The alternate CD in rescue mode could not detect a shell,I assumed this to mean I had a much bigger problem than just the bootloader.
The only thing I can think of that I was doing that might have been 'dodgy' was I had been installing xxamp and Joomla (Joomla says in its docs. it has some issues with Linux systems).It was up and running but I may have shut down without stopping the Apache server (set to localhost for trying to sort out Joomla locally).As I think you have to be root to start and stop xxamp ( and by default Apache, Mysql and PHP myadmin.) can a server with root access bugger up the bootloader?I am a bit out of my depth with webservers and have been trying to learn.
Why was their a scrap of a Windows OS on my HD ? The bios is not Windows is it?
The whole thing has made me paranoid enough to experiment with plone/Zope CMS's and only install from the repositories if it cannot be installed locally. 
Hope this offers more clues, Cheers

---

### Post by scottro on 2009-01-17
I wonder if there was some sort of recovery partition that hadn't been removed when you wiped Vista?  The only other guess is that perhaps Dell's BIOS is keyed to MS somehow, but why it would suddenly surface, I have no idea. 

Maybe there's some malware you picked up, targeted at Linux users?

All of these are stabs in the dark though, it's quite odd.

---

### Post by grekei on 2009-01-17
I agree, very odd! I reckon I have installed linux systems at least 4 times wiping the whole drive every time.I may have run a dual boot for a short time when I first bought the machine but I lost patience with Vista quickly and could see no point in keeping it.I have run Vista in "Virtual Box" but I cant see how this could effect the HD, it would ruin the whole point of running a virtual machine.
I am not very familiar with security issues apart from a basic understanding of why Linux/Unix based computing is inherently very secure and I have never had a problem before but my logic is telling me to be very wary until some one can fully explain it.
Is it possible something web based could get at the boot loader if I am connected to the Web downloading and running as root (well sudo anyway)

---

### Post by scottro on 2009-01-17
As changing the time in Ubuntu will affect the machine's BIOS, it does strike me as possible. There are, of course, all sorts of exploits that can and do affect Linux systems. 

I fear I don't have knowledge enough to tell you how to check that though.  Things like chkrootkit and tripwire are usually designed to be run before, rather than after, something's happened.

---

### Post by grekei on 2009-01-17
might look into those, don't really enjoy installing new systems on a regular basis.

---

### Post by billgoldberg on 2009-01-17
> **scottro said:**
> As changing the time in Ubuntu will affect the machine's BIOS, it does strike me as possible. There are, of course, all sorts of exploits that can and do affect Linux systems. 

I fear I don't have knowledge enough to tell you how to check that though.  Things like chkrootkit and tripwire are usually designed to be run before, rather than after, something's happened.

It's highly unlikely this is malware related.

There might have been a hidden parition with a vista system restore image on it.

But I can 't see why that would produce a error at boot up.

I have no idea, as does anyone here what's going on.

--

Boot from the Ubuntu live cd, open gparted and delete and reformat the drive.

That's all I can think of.

--

Or put in a new, empty hdd and install Ubuntu in that.

---

