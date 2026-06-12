---
title: "64 Bit Problems."
date: 2009-04-29
forum: New to Ubuntu
---

### Post by CCCody on 2009-04-29
Hi, I'm having a couple of problems with my fresh Ubuntu install on a new laptop.

There is no sound when I do the sound test but if I use headphones there is sound, but no flash sounds (Youtube, etc.) 

Another problem is that my external hard drive won't "mount" 

I'm fairly new to Ubuntu so I don't know what to. I tried googling but couldn't find anything for my version of Ubuntu (8.04)

All help is appreciated, thank you.


P.S. The error for the mount is "Cannot Mount Volume. Invalid mount option when attempting to mount the volume 'WD Passport'."

---

### Post by Kosimo on 2009-04-29
Hi!

There is any particular reason why you are not using the latest Ubuntu Jaunty Jackalope 9.04?  It has a much better pulseaudio implementation that can lucky make your soundcard working out of the box.

---

### Post by CCCody on 2009-04-29
No this is no specific reason, other than 8.04 being supported longer, or does that not currently matter?

---

### Post by Kosimo on 2009-04-29
> **CCCody said:**
> No this is no specific reason, other than 8.04 being supported longer, or does that not currently matter?

Yes, 8.04 is a Long Term Release. Which means that it will be supported and maintained for security patches for a long time.(In fact only 6 months more than Jaunty) Anyway, the improvements that you get in Jaunty which is supported until October 2010 are so many in almost all areas, but anyway Karmik Koala 9.10 will be even better, and you will probably want to move forward in just 6 months time.

Again, give it a try to 9.04! ;)

---

### Post by CCCody on 2009-04-29
I would have to update twice, to get to 9.04, correct? (I'm thinking I have to install 8.10 first.) Or is there a way to skip it and upgrade directly to 9.04?

---

### Post by Kosimo on 2009-04-29
> **CCCody said:**
> I would have to update twice, to get to 9.04, correct? (I'm thinking I have to install 8.10 first.) Or is there a way to skip it and upgrade directly to 9.04?


I would do a clean install if possible.
But as far as I'm concert you could upgrade from 8.04 directly to 9.04 by entering in Software Sources and chosse: Show upgrades (normal releases).

But as I've said, get a USB stick or a blank CD and create a new installation. In my opinion is always better than upgrading a current distro.

---

### Post by skymera on 2009-04-29
A fresh install with EXT4 would be best.

Less chance of errors. Remember to backup any needed data :D gl

---

### Post by Kosimo on 2009-04-29
> **skymera said:**
> A fresh install with EXT4 would be best.

Less chance of errors. Remember to backup any needed data :D gl

100% agree.

You will have to manually create the ext4 partition during the installation process. Have you ever did it?

If you need any help we can give you a hand! ;)

---

### Post by Paqman on 2009-04-29
> **CCCody said:**
> 
There is no sound when I do the sound test but if I use headphones there is sound, but no flash sounds (Youtube, etc.) 


Do you know what sound system you're using? PulseAudio?

> 
P.S. The error for the mount is "Cannot Mount Volume. Invalid mount option when attempting to mount the volume 'WD Passport'."

What filesystem is the drive formatted as, and how are you trying to mount it?

---

