---
title: "hardware (?) problem - keeps rebooting"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by lila on 2009-11-09
Hello,

my computer keeps rebooting.  It regularly does it when I try to turn it off, always has done.  Last year, we sort of fixed the problem for a while with a new harddisk (it was indeed faulty).  But it came back, and now does it even "out of the blue", just like that (no obvious link to type of aps running). 

Things I have tried in the last few days (it got too bad):

After a thorough data backup, I tried to upgrade xubuntu 8.10 to 9.04.  Rebooted halfway through, leaving me with a very botched system that wouldn't recognise the dsl modem.  Nor for that matter a PS2 port, so to find out that I had no internet to try to continue the upgrade, I had to go out and buy a usb mouse first...  
Not much else seemed to work either.  Dug out the install CD of 8.10, to re-install.  
6 attempts and several hours later (spontaneous re-boot each time) I had a system running in low-graphics mode.  I used this to download and burn the 9.10 version.  My 8.10 CD was a bit scratched and it told me this might cause problems.

After several more attempts to install 9.10, it did it!

I got the same error message during both CDs: 

/target/usr/lib/locale/ja_IP.utf8/LC_COLLATE
does not correspond to its original copy on the CD.

It then went on to tell me this might be due to a problem with the CD, the player or the harddisk (but the latter is quite new, as said).

Due to this, I changed my CD-Rom player set-up (took out the one I had set as master, set the slave as master), disconnected an old floppy drive (just to exclude any interference), and generally de-dusted the inside of the tower with compressed air (very necessary).

None of that made any difference whatsoever, I still got the same message.  It didn't stop the installs, I just had to click "retry" a few times.  The reboots were later, somewhere between 80 and 95 % on average.

Any ideas?  I sometimes think it's me - all computers I have ever had under all operating systems have had a tendency to reboot for no apparent reason.  But I know that on the whole it's not personal...  But this time it's gotten a bit much.

Thanks in advance!
Lila

---

### Post by lila on 2009-11-09
It does get urgent, while reading other threads to pass time waiting for a response, it rebooted twice on me in twenty minutes...

---

### Post by yanceypd on 2009-11-09
Other things to check. Cpu cooling fan is it clean and spinning.  Try some different ram.  Could be hardware.

---

### Post by QIII on 2009-11-09
> **yanceypd said:**
> Could be hardware.

Agreed.

Likely something hot.

Install lm-sensors (if you can do that with Xfce), put an applet on your panel and monitor your CPU temp and fan speed.

Run memtest overnight (hmmm... if it doesn't reboot on you!)

Is your machine placed somewhere so that it is getting plenty of air circulation?  Does your BIOS allow for altering fan speed based on CPU temp?

What are your specs?

---

### Post by lila on 2009-11-10
Thanks for the answers - I went to bed meanwhile, due to the time difference.

The Specs (hope this does it, never quite sure what is asked):  
1.2 GB RAM (1GB + 256MB) - the 256 MB came with the machine, the 1 GB is added. 
Intel Celeron 2.26 GHz processor.

The fan is clean since yesterday, but was VERY dusty before.  Will open up to check it's spinning, but obviously need to turn off the machine first and unplug.

Environement: well ventilated with not too hot (max 20 degree C) air, which has a tendency to be very dusty - located in a woodwork shop (machines next door, handtools only in here).  Normally we de-dust regularly, but the last few months have been a bit chaotic due to the birth of our first child (8 weeks old yesterday).  By the way, it's quite a challenge to take apart a tower while breastfeeding! :D

Right, see you in a bit.
Lila

---

### Post by yanceypd on 2009-11-10
Some versions run a higher cpu usage rate you could try an older version say 8.04 or 8.10 see if happens with those.  Also there are smaller versions like Xbuntu.  Then you could be beating a dead horse.

---

### Post by atomizer on 2009-11-10
It could be a faulty power supply or something overheating.
I don't think it is a software problem.

---

### Post by lila on 2009-11-10
Thanks again,

... CPU fan spinning nicely.
Already using Xubuntu.
Did the same under 8.10 (that's why I installed 9.10).
Indeed, it did the same under Breezy Badger (remember that?)...

Theory:
since I already changed the harddisk once, and the power unit once (two weeks after buying the computer it just died outright, no juice!), and added extra RAM for precisely this problem, and it did each time get better (though not solved), could it be that it's the motherboard which is somehow faulty and messing up other components?

I just don't want to change it on the off chance, as I've never done that before, and it sounds like a potentially time-consuming and/or expensive thing to do...

Lila

---

### Post by lila on 2009-11-10
> **QIII said:**
> Agreed.

Likely something hot.

Install lm-sensors (if you can do that with Xfce), put an applet on your panel and monitor your CPU temp and fan speed.

Run memtest overnight (hmmm... if it doesn't reboot on you!)

Is your machine placed somewhere so that it is getting plenty of air circulation?  Does your BIOS allow for altering fan speed based on CPU temp?

What are your specs?

... I have no idea what my BIOS allows me to do, how do I find out?

Meanwhile, I'll try to find out what an lm-sensor is, and if I can install one with Xfce.

See you later.

---

### Post by fatcrab on 2009-11-10
Hi,try removeing one stick of memory at a time.You might have a bad one.

---

### Post by lila on 2009-11-11
Hello,

.........  ok, it's in bits.  We tried out the RAM.  We unmounted everything to see if there wasn't a dustflake somewhere.

I'm writing on my husband's old computer which I dug out of the attic (Windows  95 was the original OS!)

Mine now restarts during the boot and never actually gets booted at all. (this was before the RAM taking-out trial)

The thing is:  we've spent days and days on this computer since buying it, and it always more or less had this problem.

We are self-employed artisans with a new born baby, and it is our business computer as well.  We are on a budget, but time is not unlimited either!

The shops are closed today, but tomorrow we'll go out and buy a new one, unless someone comes up with something else to try (without having to switch it on, as it won't!).

Thanks for trying everyone... much appreciated!

Lila:KS

---

### Post by lila on 2009-11-11
Oh yes, forgot to say: it can't be a heat problem - it rebooted within 15 seconds of switching on after a near 20 h break!  And kept rebooting ever since...

---

