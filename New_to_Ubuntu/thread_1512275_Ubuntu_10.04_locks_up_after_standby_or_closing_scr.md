---
title: "Ubuntu 10.04 locks up after standby or closing screen"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by BGGcategoryO on 2010-06-17
Hello,

When I attempt to lock the screen for a significant amount of time (or let it go into screensaver mode) on my laptop, the system does not respond (and in fact, shows a blank screen rather than the screensaver I have chosen). The only option seems to be a hard reboot.  The same happens after I close the screen.

I am using Ubuntu 10.04 on a Dell Latitude e6410 with an nVidia graphics card. 

I have experienced the same problem with Windows 7 (with which I dual boot).  Friends with the same laptop have told me that they have run into it as well, and I don't know whether it has to do with the hardware.

Any advice will be appreciated.

---

### Post by requeth on 2010-06-18
I recommend checking Dell's website for a firmware upgrade. Run the upgrade and see if the issue goes away. Otherwise there's a small chance you can check to see if a proprietary video card driver will help, but I wouldn't count on it. If it's happening in both OS's and on multiple laptops of the same type, it's probably a hardware issue. You may have to call Dell support and try to get a resolution. Hopefully there's a firmware patch for ya though.

---

### Post by astembridge on 2010-08-21
Same thing is happening with my laptop - a Dell Studio 1735.  

Please let me know if you find a resolution.. I am getting email notices of replies to this.

---

### Post by astembridge on 2010-10-15
I am also having this problem.. very annoying.

---

### Post by texla on 2010-10-15
Just a thought - if you have an SD card reader and an SD card in your laptop when you suspend or close the lid, this bug can occur.  But here is the fix:  
 					
Originally Posted by **bravebear** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9815337#post9815337") 				
 				[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/560384]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384")

The solution is in comment [31]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384/comments/31")

I did everything listed in comment 31 and it solved this problem immediately.  However, the SD card still seems to effect hibernation and whenever I see the blinking cursor, I remove the SD card and restart.  BUT suspend is fixed completely - go figure.

---

### Post by astembridge on 2010-10-15
Yeah, that was it.   Removed the SD card and the problem went away.
thx

---

### Post by texla on 2010-10-15
cool [U]
[/U][]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384/comments/31")

---

### Post by WaveMyBlackFlag on 2010-10-17
Same problem, but no SD card in slot and have an acer aspire 5535 with ATI card.  Goes into suspend, when trying to wake up, it seems to come back to life but no video at all, have to hard reboot.  have suspend/hibernate disabled for now, but would like to fix the problem

---

### Post by amjjawad on 2010-10-17
Just curious ... what's the size of your SWAP Partition?

---

### Post by Lupajz on 2011-04-10
The problem with acer 5535 is not in the size of swap :/

---

