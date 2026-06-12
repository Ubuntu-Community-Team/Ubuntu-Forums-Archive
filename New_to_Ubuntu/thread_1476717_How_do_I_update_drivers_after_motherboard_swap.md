---
title: "How do I update drivers after motherboard swap?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by marktebbutt on 2010-05-08
Hi all,
I have had to rebuild my PC as my motherboard burnt out. I have managed to get it running again but I am not sure if all my drivers are updated - I guess it is not done automatically(?) I can only select maximum screen resolution of 1024*768 so I think it needs updating.
Can anyone please tell me how to check and update drivers for e.g. graphics card...?
Is there some way of checking and updating all drivers in one go?
Thanks in advance.

---

### Post by 3rdalbum on 2010-05-08
> **marktebbutt said:**
> Hi all,
I have had to rebuild my PC as my motherboard burnt out. I have managed to get it running again but I am not sure if all my drivers are updated - I guess it is not done automatically(?)

Incorrect guess :-)  The Linux kernel detects and loads drivers at boot time and plug-in time, not at install time, so most of your drivers are correct for your hardware.

> I can only select maximum screen resolution of 1024*768 so I think it needs updating.
Can anyone please tell me how to check and update drivers for e.g. graphics card...?

What graphics card is it? For Nvidia or recent ATI cards you go to the Hardware Drivers program under System > Administration.

---

### Post by marktebbutt on 2010-05-10
Thanks for the response - I guess I should give up guessing! 

Considering your reply, I did a few hours of fiddling it looks like the problem lies with the onboard graphics not being supported in linux - SIS. Unfortunately my old NVIDIA card does not seem to fit. It looks like I'm stuck with it for now unless I get a new graphics card. 

Oh, and just to make things worse, my fiddling has resulted in me losing the 1024*768 resolution and I can now only get 800*600! Grrr!!

---

### Post by 3rdalbum on 2010-05-10
Yeah, if you've got an old AGP-based graphics card, it won't fit in today's PCI-E-based motherboards.

---

### Post by Paqman on 2010-05-10
Luckily however, even the cheapest PCI-E graphics card is likely to have significantly better performance than your old AGP card. You shouldn't have to spend much, and you'll get a nice upgrade in your graphics performance.

---

### Post by 3rdalbum on 2010-05-10
> **Paqman said:**
> Luckily however, even the cheapest PCI-E graphics card is likely to have significantly better performance than your old AGP card. You shouldn't have to spend much, and you'll get a nice upgrade in your graphics performance.

I recommend the Nvidia GT220 - it's quite dinky but it probably outperforms your old card, it doesn't require extra power cables from your PSU and the model listed on [my website]("http://www.chrislees.info") is low-profile (which means it uses up only one of your case's slots).

---

### Post by marktebbutt on 2010-05-10
Thanks for the advice - looks like a night on eBay for me :-)

---

### Post by Sylslay on 2010-05-10
I swap yesterday hdd 2.5" from one laptop to other (2 diffrnet unit with Award and Compaq bios), Neither Windows XP sp3 or Linux Ubuntu 9.10 booted up on second machine. Surprise?

---

