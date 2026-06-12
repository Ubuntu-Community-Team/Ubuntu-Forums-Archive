---
title: "Ubuntu 10.04 and Compatability with VirtualBox OSE"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Starhunter on 2010-07-31
Greetings.

I've encountered a bit of trouble in getting a Virtual Box program to work properly with my computer.  (I'm running Ubuntu 10.04.)  I'm hoping that someone can offer me some advice that will help me solve my problems.

I recently bought a new computer, and for several reasons I opted to install Linux as my OS.  (Previously, I've been a Windows user all my life.)  Having done so, I discovered that there are a few key software compatibility issues between my old system and my new one.  Specifically, that there is no support for iTunes on Linux.

(Now, before people begin suggesting that there is a veritable cornucopia of applications available that will replace iTunes, let me be clear: I use iTunes to BUY music.  That feature is not supported on any other application that I have discovered, which means iTunes remains the only game in town if I want to support the artists I like by buying their songs.)

This being the case, I installed the version of VirtualBox OSE (3.1.6) that is available from the Software Center.  I believed that this would allow me to run XP on a Vbox, which would give me access to iTunes and a few other Windows-Based programs without being stuck with Windows as my OS.  

For the most part, this worked.  I was able to install the program, and got my old XP disks to load.  I installed iTunes, and attempted to upload my Library from my External Drive.  It was here I hit the major snag - the VirtualBox cannot detect my USB ports.  After some forum-searching, I was able to figure out how to 'mount' my external drive so I could copy my Library into Windows using the Run command.  The problem now became that I have been totally unable to do the same with my iPod.  

Basically, I'm at a loss for what to do next, so I'm here looking for help.

Is there a way to get OSE to 'see' my USB ports, or is there a way I can 'mount' an iPod so that OSE can 'see' it?  Or is the problem systemic, and solvable by switching to a different VBox program?  

Any advice that could be offered in this matter would be much appreciated.

---

### Post by jerenept on 2010-07-31
the ose version cannot use USB ports, uninstall it and install the PUEL version here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by Kevuntu on 2010-07-31
> **jerenept said:**
> the ose version cannot use usb ports, uninstall it and install the puel version here: [http://www.virtualbox.org/wiki/linux_downloads]("http://www.virtualbox.org/wiki/linux_downloads")

+1

---

### Post by JC Cheloven on 2010-07-31
> **Kevuntu said:**
> +1

Ha! Just noticed that the quote you inserted has changed all letters to lowercase. So the link in your quote is wrong. 

jerenept's link is fine though :)

---

### Post by Starhunter on 2010-08-01
Ah.  Typical of my luck with software.  :p 

So if I un-install the OSE version, will I also have to re-install the Windows, or will the new Vbox be able to find and use that chunk of hard-drive space?

(I figure it's best to know before I go ahead and un-install.)

---

### Post by Plumtreed on 2010-08-01
You should be able to use the .VDI files already set up!

---

### Post by rob_38 on 2010-08-01
Rhythm Box has Ubuntu One music store and a bunch of other things.

---

### Post by Starhunter on 2010-08-01
[QUOTE=Plumtreed] 	 		 		You should be able to use the .VDI files already set up! 	[/QUOTE]


That's a relief.  Doing a full re-install would have been an epic pain.

Thanks very much to everyone who posted in this thread.  You were a big help.  

Cheers,
S.

---

### Post by Starhunter on 2010-08-01
Alright, I'm back.

So I've gotten the program linked above installed, and it's up and running.  However, when I plug in my iPod, there is still no communication with the Windows, nor iTunes.  Is there a special trick to this that I'm missing?

---

### Post by Starhunter on 2010-08-01
...Never mind.  I figured it out.

All this enabling is very new to me.  :p

---

