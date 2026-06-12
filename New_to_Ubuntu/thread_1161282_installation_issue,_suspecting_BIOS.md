---
title: "installation issue, suspecting BIOS"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by a77ssii on 2009-05-16
My antique desktop running windows 98 finally went down. Stuck another hardrive in it and it boots right into DOS with no problem. Set it up to boot from CD first and due to the age am installing 7.10 on it (Intel MMX 333Mhz) since it nowhere near meets the requirements for 9.04 or 8.04. I get the install screen and select install, I then get the installing kernel screen which runs to 100% and the system then reboots only to start back at the beginning again. I went through all the BIOS setting on the install instructions part and they match but I am assuming I'm missing something. I have gotten so tired of XP on my laptop I got Ubuntu on my new Dell Mini 9 and once this issue is dealt with I'm headed to the install of 9.04 onto this laptop eliminating XP so the antique installation is kind of a primer/learning experience for me without risking my primary system. I'm now having flashbacks of learing DOS/BASIC on an Apple IIe back in middle school](*,) (I know I'm dating myself)

---

### Post by Aaardwark on 2009-05-16
Gutsy isn't as fast as Feisty, and after that I don't believe the speed has changed that much between the releases. Jaunty is the first in a while to be both faster and more stable than it's predecessors. If possible I recommend it.

If you want a system adapted for an older computer I'd go with Xubuntu, rather than an older release. I'd recommend trying Xubuntu 9.04 alternate. With the alternate install, 256 MB ram is all that's needed even for Ubuntu (the install, won't say it will be fun using it).

Depending on how old your computer is, you could try Tinyme or Slitaz. None of them is as user friendly as Xubuntu, but both are easy to try/install, and generally works great with most hardware. If you know your way around BIOS, they probably aren't that much of a problem. :D

---

### Post by NHArticleTen on 2009-05-16
Damn Small Linux and Puppy Linux have worked well for me with dozens of legacy machines.

---

### Post by Didius Falco on 2009-05-16
> **a77ssii said:**
> My antique desktop running windows 98 finally went down. Stuck another hardrive in it and it boots right into DOS with no problem. Set it up to boot from CD first and due to the age am installing 7.10 on it (Intel MMX 333Mhz) since it nowhere near meets the requirements for 9.04 or 8.04. I get the install screen and select install, I then get the installing kernel screen which runs to 100% and the system then reboots only to start back at the beginning again. I went through all the BIOS setting on the install instructions part and they match but I am assuming I'm missing something. I have gotten so tired of XP on my laptop I got Ubuntu on my new Dell Mini 9 and once this issue is dealt with I'm headed to the install of 9.04 onto this laptop eliminating XP so the antique installation is kind of a primer/learning experience for me without risking my primary system. I'm now having flashbacks of learing DOS/BASIC on an Apple IIe back in middle school](*,) (I know I'm dating myself)

I'm digging around in the Ubuntu forum and docs, and I've seen a mention of an "only-ubiquity" option to run just the installer. It's supposed to help with low-ram machines. 

Have you tried that?

Regards,

Didius

On Edit: You could also try the Alternate Installer, which is available here:

[http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/)

Note also that I saw this warning regarding 7.10:

> [COLOR=red]These images are vulnerable to [USN-612-1]("http://www.ubuntu.com/usn/usn-612-1"), a very serious flaw in the cryptographic library used to generate encryption keys. It is essential that you apply all security updates after installation before making any use of your system.[/COLOR]

---

### Post by a77ssii on 2009-05-16
aardwark, I will look into those.  That's one of the reasons I was dropping windows for Linux is the infinite posibilities that are available.
 
NHArticleTen, see above):P
 
Didius Falco, "only-ubiquity" .  Um...  I can run the valves on a 6BT Cummins, rebuild a chainsaw but know just enough to be dangerous and really screw something up when it comes to this but have no choice but to learn because all the local comp shops don't want to deal with the install and tell me I'm nuts for not wanting a windows OS.
 
I also have tried the install of 9.04 and it comes up thinks for a bit and reboots.  Same problem just without the kernel installation.

---

### Post by Didius Falco on 2009-05-16
Hey, we all have our weak points. Me + Chainsaw = Death By Misadventure. ;)

---

### Post by psy-moon on 2009-05-16
I have just expirienced a similar event i.e failier to boot a previously working machine.
To cut a long tail short.
If you can run the memory test option in GRUB,  check all your RAM is good.

---

### Post by a77ssii on 2009-05-16
I thought about that when I saw on the install troubleshoot how important it is and paid a bit more attention on boot.  The machine does a check when it starts up and it's clearing 250Meg which is what I have installed.  Your all gently nudging me toward buying the Linux for dummies aren't you?;)

---

### Post by snowpine on 2009-05-16
Hi a77ssii, a 10 year old computer is probably not up to the task of running Ubuntu, which is a full-featured linux distro for modern hardware. (You haven't posted your system specs, though, so I am just guessing). It is foolish to install any Ubuntu version prior to 8.04, because they are no longer supported. 

Check out the link below for some good suggestions; my personal favorite for old hardware is SliTaz. DSL and Puppy also seem to be popular.

ubuntuforums.org/showthread.php?t=575456

---

