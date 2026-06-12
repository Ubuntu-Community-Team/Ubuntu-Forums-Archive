---
title: "To Small Lower Memory in  Karmic Koala"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by bluespider on 2010-04-30
Hello I am a new user of Ubuntu, currently running Karmic koala (64 bit) which I just installed. I noticed that the computer was doing everything really slowly, so at the boot up screen I ran the memtest, and here is the message I saw : To small lower memory 0x99100 > 0x8f000  I do not know what that means but It seems to mean something is not right. If anyone does know what this means and what I should do to fix it, I would greatly appreciate the help, thank you.

Computer specs are as follows:

Core duo 2.4 gig 3 gb of ram
dual boot system
Nvidia 9500 gt pci express video card

---

### Post by Paqman on 2010-04-30
Have you installed the drivers for your Nvidia card? Go to System > Admin > Hardware Drivers to get them if you haven't.

---

### Post by bluespider on 2010-04-30
> **Paqman said:**
> Have you installed the drivers for your Nvidia card? Go to System > Admin > Hardware Drivers to get them if you haven't.

Yes I have installed the Nvidia drivers

---

### Post by Sealbhach on 2010-04-30
I would upgrade to Lucid if I were you. I don't know why your system is so slow, could be any number of reasons.

---

### Post by RTrev on 2010-04-30
Is this computer one that was working fine before?  Did you recently add or change the 3G of memory in it?  Seems like the memtest routine is not happy with the hardware.

---

### Post by bluespider on 2010-04-30
> **RTrev said:**
> Is this computer one that was working fine before?  Did you recently add or change the 3G of memory in it?  Seems like the memtest routine is not happy with the hardware.

Right after install it seemed to  be working fine, it's possible I didn't notice though because I wasn't really doing anything too intensive for the computer. Everything runs fine in windows. As far as the memory everything is the same as it was on install. I have performed tests on the ram which indicate everything is fine.

---

### Post by Sealbhach on 2010-04-30
> **bluespider said:**
> Right after install it seemed to  be working fine, it's possible I didn't notice though because I wasn't really doing anything too intensive for the computer. Everything runs fine in windows. As far as the memory everything is the same as it was on install. I have performed tests on the ram which indicate everything is fine.

Go for Lucid dude. It's an LTS. In my experience, it's way better than 9.10.

.

---

### Post by RTrev on 2010-04-30
It would seem that there is some sort of BIOS and Memtest interaction, and bug reports have been filed, but you may want to explore it a bit:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)

Or just Google on "memtest too small lower memory" without the quotes.

Maybe somebody will come along that knows how to deal with this.  I guess, if you're so inclined, I'd second the suggestion to try installing the newest version (released yesterday) and see how that works.  Maybe they've worked around this problem.

Good luck!  Wish I could help more...

---

### Post by Sealbhach on 2010-04-30
> **RTrev said:**
> It would seem that there is some sort of BIOS and Memtest interaction, and bug reports have been filed, but you may want to explore it a bit:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)

Or just Google on "memtest too small lower memory" without the quotes.

Maybe somebody will come along that knows how to deal with this.  I guess, if you're so inclined, I'd second the suggestion to try installing the newest version (released yesterday) and see how that works.  Maybe they've worked around this problem.

Good luck!  Wish I could help more...

I googled a bit too. I suspect this Memtest result is not much to worry about.

.

---

### Post by bluespider on 2010-04-30
> **Sealbhach said:**
> Go for Lucid dude. It's an LTS. In my experience, it's way better than 9.10.

.


Thanks to all for their help, I appreciate it. I decided to move to Lucid. I installed it and it seemed to be moving much faster, I was even able to render a file which had crashed on Karmic, it rendered amazingly fast as well. One thing though, maybe this is just due to the size of the drive I am not sure, I have a terabyte drive, it takes a long time for the file manager to open, its a usb drive (I don't know if that matters) is this normal ? Otherwise I am pleased with Lucid.

---

### Post by leomelo on 2011-03-31
I have same problem.It seem to be a bug in Memtest86+.Apparently,it has been solved in Memtest86+ version 4.20.The Ubuntu repository version is 4.10.I made the memory test by downloading the bootable iso (version 4.20) from Memtest86+ website amd copied to a cd and booting it.Everything was ok.

---

