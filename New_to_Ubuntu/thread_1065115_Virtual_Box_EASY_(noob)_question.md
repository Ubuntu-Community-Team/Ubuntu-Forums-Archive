---
title: "Virtual Box EASY (noob) question"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-09
Just installed virtualbox 2.1.2 and it installed with no issues.  It's running fine.

But the question is it's asking for some kind of BOOTABLE MEDIUM and when it doesn't find it, it halts.

So, like a noob, I was thinking it had some kind of built in way of running Windows programs but now it seems it needs to load WindowsXP in order to run programs.

So, do I put my winXP disc in the CD drive (because it tries to install WinXP) or is that what it supposed to happen?  Do I need to install WinXP in my Virtual machine just like on another PC or do I just need a WinXP Boot Disc?

A little confused.

Thx

---

### Post by kestrel1 on 2009-02-09
You need the CD of what ever OS you want to install or you can even choose an ISO file to boot from. Just go to the CD-Rom section & select the internal CD drive or an ISO image.

---

### Post by Therion on 2009-02-09
You install Virtual Box then you create virtual machines.  Each of these is called a "Guest".  For instance your "Host" operating system (I'm assuming) is Ubuntu, so Windows XP would be the "guest" OS, which runs in a virtual machine created by Virtual Box.  Clear as mud?

To create a Windows XP "Guest" you need a Windows XP install CD.  This "install" will look pretty much like any other.  You'll partition and format a "drive" and then do the full blown install of Windows XP; complete with activation, WGA, hundreds of updates, etc.  

w00t!

---

### Post by mistypotato on 2009-02-09
So I'm gonna put my WinXP OEM installation CD in the CD drive and run the installation JUST AS IF I WERE INSTALLING WinXP ON another PC for the first time for example?

[COLOR="Red"]
Thanks Therion...saw you post AFTER I posted this..[/COLOR]

---

### Post by Therion on 2009-02-09
> **mistypotato said:**
> So I'm gonna put my WinXP OEM installation CD in the CD drive and run the installation JUST AS IF I WERE INSTALLING WinXP ON another PC for the first time for example?

[COLOR="Red"]
Thanks Therion...saw you post AFTER I posted this..[/COLOR]
That's 'xactly what you're gonna do.  Might wanna see this tutorial though:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by mistypotato on 2009-02-09
Awwwwwwww......:confused:

[COLOR="Blue"]Setup Cannot Format the Partition.
Your computer may not have enough memory to perform this operation.
Setup cannot continue.[/COLOR]

Guess I need to add RAM?
How much is the minimum needed?
How do I find out how much RAM memory I currently have?

---

### Post by mistypotato on 2009-02-09
anyone?

---

### Post by howefield on 2009-02-09
How much RAM have you allocated ? XP will perform ok in as little as 256, maybe even a bit less.

You need enough memory to keep the host and guest systems happy.

---

### Post by mistypotato on 2009-02-09
Hello!

I only have 1 gb of Ram (max for this HP desktop (dated)).

I allocated as much as 500 to Virtualbox but it was warning me that I was using too much of the total and the host OS might crash.

Should I try it again using more RAM to Virtualbox?

---

### Post by Paqman on 2009-02-09
> **mistypotato said:**
> 
Guess I need to add RAM?
How much is the minimum needed?
How do I find out how much RAM memory I currently have?

In Virtualbox, click on Settings for your virtual machine. You'll be able to change how much of your machine's RAM to allocate to the virtual machine. XP will probably want at least 512MB, but you can run it down to about 256MB. Obviously, you need to have at least this much spare RAM that Ubuntu isn't using, or else everything will slow to a crawl.

You can also change the settings for how much RAM to allocate to graphics, and which hardware to give the VM access to. For example, Virtualbox doesn't let the VM use sound in it's default setup, so you'll probably want to enable that.

Also, XP doesn't have the right drivers for Virtualbox's virtual network adaptor. You'll need to get those from the AMD site. Easiest way to get them into the VM is to enable sharing in the VM and have it pick the driver files up from somewhere like your home folder.

Once you've got XP installed in the VM, don't forget to install antivirus, etc. The Virtualbox "guest additions" are also well worth installing.

---

### Post by Cypher on 2009-02-09
You can bump up the RAM up to 768, but that might have a negative impact on the Ubuntu installation while the Virutal OS is running.

I have 2 GB of RAM and when I allocate 768MB to XP in the virutal machine, both my Ubuntu machine and XP inside VirtualBox work perfectly fine..

---

### Post by mistypotato on 2009-02-09
I bumped up the RAM allocated to Virtual Box to 700 which left 300 for ubuntu....

it's halfway through installation.....

Fingers crossed  :P

---

### Post by Paqman on 2009-02-09
I'm surprised XP wouldn't install with 500MB, it was designed to work on machines with a lot less. Once it's installed you should definitely be able to drop that back down. I run an XP VM on 512MB and it works fine.

---

### Post by mistypotato on 2009-02-09
The comment about viruses is closer to home than you realized.

This entire journey BACK to ubuntu was BECAUSE I had 4 WinXP machines all brought to their knees by a virus so bad that it renders a WinXP machine useless within a few hours, sets up a HTTP server, kills the Network connection, opens back doors, and generally does all kinds of nasty stuff.  I cannot get rid of it so I cannot use Windows at all at this point.  On my desk is a PURCHASED (from NewEgg) WinXP SP3 that is defenseless against this thing whatever it is.

Not ONE antivirus or spyware program that I've tried can find a trace of this super bug.  I've watched it (or tried to with Process Monitor and it's a killer.

So, Im afraid it's infected all my files including DATA because when I try to install even a back up data file, the machine starts bogging down doing the malware's dirty work.

I'm just bidding time hoping that eventually ONE antivirus company finds it and creates a signature to kill it.

:(

---

### Post by marco123 on 2009-02-09
> **mistypotato said:**
> The comment about viruses is closer to home than you realized.

This entire journey BACK to ubuntu was BECAUSE I had 4 WinXP machines all brought to their knees by a virus so bad that it renders a WinXP machine useless within a few hours, sets up a HTTP server, kills the Network connection, opens back doors, and generally does all kinds of nasty stuff.  I cannot get rid of it so I cannot use Windows at all at this point.  On my desk is a PURCHASED (from NewEgg) WinXP SP3 that is defenseless against this thing whatever it is.

Not ONE antivirus or spyware program that I've tried can find a trace of this super bug.  I've watched it (or tried to with Process Monitor and it's a killer.

So, Im afraid it's infected all my files including DATA because when I try to install even a back up data file, the machine starts bogging down doing the malware's dirty work.

I'm just bidding time hoping that eventually ONE antivirus company finds it and creates a signature to kill it.

:(

Sounds like it's infected the mbr.   DBAN is good for nuking your entire drive including the mbr.  JUst use ubuntu to backup your music etc.. then use that and try re-installing XP then, might work?

[http://www.dban.org/](http://www.dban.org/)

Cheers, Marco.

---

### Post by theozzlives on 2009-02-09
> **mistypotato said:**
> The comment about viruses is closer to home than you realized.

This entire journey BACK to ubuntu was BECAUSE I had 4 WinXP machines all brought to their knees by a virus so bad that it renders a WinXP machine useless within a few hours, sets up a HTTP server, kills the Network connection, opens back doors, and generally does all kinds of nasty stuff.  I cannot get rid of it so I cannot use Windows at all at this point.  On my desk is a PURCHASED (from NewEgg) WinXP SP3 that is defenseless against this thing whatever it is.

Not ONE antivirus or spyware program that I've tried can find a trace of this super bug.  I've watched it (or tried to with Process Monitor and it's a killer.

So, Im afraid it's infected all my files including DATA because when I try to install even a back up data file, the machine starts bogging down doing the malware's dirty work.

I'm just bidding time hoping that eventually ONE antivirus company finds it and creates a signature to kill it.

:(

Well hopefully, having Ubuntu as a host will prevent that from happening.

---

### Post by Paqman on 2009-02-09
> **theozzlives said:**
> Well hopefully, having Ubuntu as a host will prevent that from happening.

It probably won't. A guest OS should be considered independent from the host for security purposes. XP VMs running on Ubuntu hosts will get infected with all the usual Windows malware if you don't take the appropriate precautions.

---

### Post by mistypotato on 2009-02-09
Thanks Marco :P

I've used Acronis to wipe the drive(s) each time before I reinstall but as soon as I try to reload any backed up files or data, the re-infection occurs so this thing has actually appended code to practically every file (including all types of data) on my WinXP computers.

By the way, VirtualBox finished installing WinXP on my Intrepid 8.10 without a glitchand is running perfectly.  (it's actually amazing to see a FULL copy of WinXP running in a Window ON Ubuntu :)

But, now I'm wondering....why did I install VirtualBox?  I can't use any of my data because it's just a vulnerable to infection as my other standalone WinXP boxes..

---

### Post by Paqman on 2009-02-09
> **mistypotato said:**
> 
But, now I'm wondering....why did I install VirtualBox?  I can't use any of my data because it's just a vulnerable to infection as my other standalone WinXP boxes..

Because now you can take a backup of the virtual machine. So you don't have to reinstall from scratch if it gets infected. Just delete it and break out a fresh copy of your backed-up VM. Quick and easy.

---

### Post by theozzlives on 2009-02-09
Just copy the *.vdi file to *.bak. It's in the ~/.VirtualBox folder. If you disable the networking for Windows and just surf the net with Ubuntu, you should be okay from malware. BTW: Right Ctrl+F will put the window in "full-screen" mode. Install clamwin and enable your firewall.

---

### Post by mistypotato on 2009-02-09
Couldn't find any file with *.vdi extension on my system ?

Just downloaded from their site today...ver 2.1.2

Maybe no more vdi files ?

---

### Post by Shazaam on 2009-02-09
> **mistypotato said:**
> Couldn't find any file with *.vdi extension on my system ?

Just downloaded from their site today...ver 2.1.2

Maybe no more vdi files ?

Location...
/home/yourusername/.VirtualBox/VDI

---

