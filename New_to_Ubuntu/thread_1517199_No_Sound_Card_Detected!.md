---
title: "No Sound Card Detected!"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by thepompano on 2010-06-24
Hey guys!  I was hoping somebody here could help me out; I've tried other forum posts, Launchpad, and IRC to no avail.

I'm using a Sound Blaster Creative X-Fi sound card that Ubuntu cannot read.  The aplay -l command yields the following error message: "The program 'aplay' is currently not installed.  You can install it by typing:
sudo apt-get install alsa-utils".  Using that command yields:```
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```I heard that there's no drivers for this sound card with ALSA and that I would need to install a beta driver using OSS.  An installation of OSS constantly yields errors.  The "sudo lshw" command shows this: ```
           *-multimedia
                description: Multimedia audio controller
                product: SB X-Fi
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:05:01.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=oss_sbxfi latency=32 maxlatency=5 mingnt=4
                resources: irq:22 ioport:1000(size=32) memory:90000000-901fffff memory:90200000-903fffff

```  I don't know what to do.

---

### Post by snip3r8 on 2010-06-24
can you play sound through rhythmbox ?

---

### Post by thepompano on 2010-06-24
Nope, no luck with that.

---

