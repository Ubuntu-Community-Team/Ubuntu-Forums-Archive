---
title: "Continually Burning Corrupt ISO - USB Option?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by shaunsmith_99 on 2009-09-21
Hey Folks,

   I've been leeching off these forums since 2006 When I first started Using Ubuntu. I've been dabbling in Linux for a few years now but it's time to get serious. I'm a graduate Student, and many of the programs I would like to run (Industrial Simulation, Statistical Software, et cetera) work WAY better on a linux based system. I used Corel Linux for 3 years (I'm sorry!!) and Redhat. I tried Gentoo a few times, but screw that. = )

  I Bought a new Gateway NV5214U last week and installed a 32bit 9.04 distro flawlessly. Everything worked like a charm. Wireless, Sound, 3D acceleration (after fetching the right driver..) It has 4gig of RAM, and being selfish, I decided to upgrade to a 64bit system up utilize all the RAM and the Dual-core AMD. 

 I have downloaded the .64 image file from 3 different mirrors and tried to burn it 6 times. I've tried to burn it  from the 32-bit Ubuntu System (before the first install attempt), my OSX machine, and my wife's Vista. Everytime it halts installation after partitioning the HD and 70% into copying the files. My disks fail the check everytime. This is ridiculous! :confused: I burn them at the slowest speed (8x), and I've used three different computers.  Any Ideas? I've also done a complete RAM check on my machine and it comes up flawless. :confused:

 I'm going to attempt to write a bootable USB drive and shoot from there this evening. (my BIOS does support booting from USB). Is there any other reason I could be having this many problems witting a simple .iso image!!? No other threads have had the exact problems I'm experiencing here, so I hope that this thread will help some other poor newb like other threads have helped me.

---

### Post by diablo75 on 2009-09-21
Once I had to do a BIOS update before my computer would install right.  The bug caused some sort of conflict during boot involving "Booting from a CD-ROM which is on the same IDE channel as the primary hard drive."  A BIOS update fixed it for me.  Now I would have just put the DVD drive I had on the secondary channel and left the HD on the primary, but this motherboard (for some strange reason) had a broken secondary channel that stopped working.  You might try to move your data cables around and give it a shot.

Alternatively, I think the USB option would work more reliably so you're on the right track.

---

### Post by LewRockwell on 2009-09-21
were your checksums checking out correctly?

.

---

### Post by shaunsmith_99 on 2009-09-21
Yeah, the checksums came out just fine each time!! I was worried that I was trying to write to a corrupt block on the HD. I Fixed it all this afternoon though.. I installed Unetbootin and burned the ISO to a dinky little $5 1gig Stick I bought at WallyWorld. Went into the bios, told it to boot there before the HD, and installed it without any problems what-so-evver. 

 I think I know what the prob was... I bought some house-brand CD's from a grocery store and burned them at 8x and 2x, but I think they were just junk. I ripped an ISO to a nice fancy CD from Bestbuy (you know, the ones with the shiny gold tops...) and it worked like a charm too. Now I'm writtin' this on my 64-bit dual core AMD machine and just tweakin' her up. Next step: Install 32-bit libraries. = (

Thanks gang!!

---

