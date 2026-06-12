---
title: "PC exploded &amp; trying to recover - Install CD won't install"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2009-01-09
Hi everyone, 

My PSU failed and took the motherboard, CPU, memory, and two hard drives with it. Let lot's of smoke out :( I have been replacing parts like crazy and finally got everything powered up and was able to boot and install my WinXP partition on a new hard drive. I still have two DVD drives from the old system, a PATA burner and SATA reader. XP installed fine. 

Next I boot the same 8.10 i386 server disk I used to orginally install the system and can set up the partitions and format but during the base install I get this:> Please insert the disc labeled: 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (2008102' in the drive '/cdrom/' and press enter. Media change. and I cannot clear the dialog. Running the CD integrity check passes completely.

I search a bit and tried burning a new disk, this time on DVD since I am out of CDs. This one was 8.10 amd64 server image. This one will boot to the initial dialog screen but clicking install it almost immediately tells me it cannot mount the cdrom. This particular DVD was burned on the same system using a USB booted LIVECD. 

If I boot this dvd from my laptop it works fine. The integrity check also passes on the laptop.

I made a new USB boot drive using the 8.10 amd46 server iso image, and I boot fine, get all the way to the install but it always hangs at one point or another, I suspect due to network timeouts or something.

Bottom line. I cannot install Ubuntu. Any ideas what the problem might be?

---

### Post by wolfen69 on 2009-01-09
did you verify the dvd after burning?

---

### Post by nowhere@cox.net on 2009-01-09
Ubuntu "write to disk" does not have a verify option. I did the integrity check after booting and it checks out.

To elaborate, I actually burned two DVDs of the same image, one on my rebuilt system and one on my laptop. Two different burners, both had the same result but a different result from the CD I had burned. I was wondering if it had to be a CD for it to install correctly...

---

### Post by nowhere@cox.net on 2009-01-14
Ok marking this solved. I bought some new CDs and burned one at 10x in Window Vista. It killed me to have to do this btw, but the Ubuntu tool didn't give me the option to burn slow enough. 

Anyway, it finally booted and installed ok. I still don't understand why the DVDs didn't work. I had burned them at 4x instead of the rated 16x and two out of two failed to mount after booting. 

I am back up and running now tho...

---

### Post by Vantrax on 2009-01-14
Higher burn rates often cause errors on cheep media. 

I tend to burn anything important at low speeds.

---

### Post by nowhere@cox.net on 2009-01-15
Agreed. Weird thing was the first failed attempt was with CD media that I had used less than a month ago to install on this very system before the burn out and install on two other systems. 

Then I did a slow burn on DVD and neither of them would work either. 

All of these were burned from Ubuntu by right clicking on the iso file.

I had to go to Windows Vista to get more control over the burning by using Roxio to get a slow speed and had to use CD media to get a disk that would boot. Just very very weird. 

Also, I just discovered that my CD reader is dead too from the PSU burn out. Spins up but won't read anything. Makes a lot of noise too...

Thanks for the posts!

---

