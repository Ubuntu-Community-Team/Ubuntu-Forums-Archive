---
title: "Intel i3-2100T (1155) Build"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by pablolie on 2011-05-10
I need some advice - I am replacing my current D510 Atom based system with what I hope to be a much higher performance, low power and quiet system based on
- Intel DH61 mobo
- Intel i3-2100T (I will use the integrated graphics)
- Samsung SSD
- 4GB of RAM (I shall just run Ubuntu 32 bit, 64 has always been too much trouble for me ;-))

I am not sure whether to stay with the trusty 10.04 that has served me well and still has some time of official support, or whether to move to 11.04 (the allure of the new..).

I have read about integrated graphics issues with Intel Sandy Bridge with 11.04, but have not really found out whether those are now fixed with the official release, or whether the same issues would exist with 10.04.

I also encountered file sharing difficulties between Win7 and Ubu10.04, and I wonder whether there have been changes with 11.04?

In a nutshell - any system builders that may have done the same thing have any recommendations? 

Thanks in advance!

---

### Post by oldfred on 2011-05-10
You may want to read this:

[http://www.phoronix.com/scan.php?page=article&item=intel_corei3_2100&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei3_2100&num=1)

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by pablolie on 2011-05-14
Well, this configuration doesn't work with 10.04LTS.

(1) The integrated graphics don't work well - I can not enable any desktop effects despite having done the recommended xorg update (add-apt-repository ppa:xorg-edgers/ppa).

(2) The Ethernet interface doesn't work either.

I also tried 11.04, and while it will discover the Ethernet IF and use it, it's hard to say if the graphics work any better because it has done away with effects under "Appearance"...

So appreciate pointers, it's a shame...

---

### Post by fjf on 2011-05-14
Get a cheap nvidia video card, and use the privative nvidia drivers.

---

### Post by pablolie on 2011-05-14
Guess I could live with the so-so graphics until better support for the Sandy Bridge stuff on this cool little MiniITX Intel DH61 board arrives.

However, I am surprised the Ethernet controller isn't working in 10.04 (although it does work in 11.04).

The command output in 10.04 is
lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe51ffff memory:fe528000-fe528fff ioport:f080(size=32)

---

### Post by pablolie on 2011-05-15
For what it's worth. I shall document a few things...

On this type of hardware (Intel mobo DH61 and i3 2100t processor) do yourself a favor and get 11.04. I did switch to Ubuntu Classic (via the Admin - Login menus) because it seems to change behavior a little. I used the NTFS Configuration Tool to re-attach my old drive - but it noodle on much longer in 11.04 to discover and change things, be patient.

If you are installing Squeezeboxserver, I left a note about my experience in the classic Squeezebox forums.

The (integrated in the i3 2100t) graphics don't work at full performance yet, but they work well enough for the stuff that matters.

This is now a great little machine that delivers performance while saving power... less than 20W when idle, perfect as an always on machine, and about 30-something watts when loaded. Awesome.

Thanks again Ubuntu - I wish I could have made this work with the 10.04 stable release, but nah, it was too much hassle and 11.04 works much better here.

---

### Post by Jared Norris on 2011-05-16
Thank you so much for reporting how it went.

As someone who is very interested in purchasing this processor for a low powered desktop replacement I was wondering if you could spare some time to test a couple of things for me (if you haven't already tried these).

1) Does it handle 1080p video ok on the integrated video?
2) Does it handle *shudder* flash on websites ok (even HD content?)

I understand your ethernet issues were motherboard related so I was curious as to if you've noticed any other issues with this processor and integrated video under Ubuntu.

Thanks again for your time, it will put my mind at ease.

---

### Post by pablolie on 2011-05-16
>  Does it handle 1080p video ok on the integrated video?

definitely does handle HD video in every format i have encountered (and i have uploaded a 720 to facebook). video playback is not a problem, i just think it happens with additional processor churn, because this processor handles it no problem with less than 15% processor ultilization in tests...

> Does it handle *shudder* flash on websites ok (even HD content?)

yes it does play HD flash content (download ubuntu restricted extras), i have not noticed any issues there.

> I understand your ethernet issues were motherboard related so I was 
> curious as to if you've noticed any other issues with this processor and > integrated video under Ubuntu.

under 11.04 the ethernet worked like a charm from the base install CD. 

i am very pleased with the way everything works right now with the basic 11.04 install, it is *more* energy efficient at idle than my former Atom D510 board was, and as i type this it still only chomps down 26W... but supposedly this platform could do even better. it's just a matter of a short wait, but it truly is worth going for right now... the power-performance ratio is way unlike anything i have experienced before (and i have an i5-661 system)

---

### Post by Jared Norris on 2011-05-17
Thank you so much for sharing your experience. I'm trying to replace several P4 Prescott's (extremely power hungry) for web browsing, email and IRC type use and you've just put my mind at ease to the performance of the integrated video. 

Now to go and find someone that stocks the T variation as my usual local stores can't get it.

---

