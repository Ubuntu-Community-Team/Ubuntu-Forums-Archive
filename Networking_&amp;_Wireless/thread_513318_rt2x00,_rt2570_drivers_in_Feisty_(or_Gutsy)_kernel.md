---
title: "rt2x00, rt2570 drivers in Feisty (or Gutsy) kernel for PPC?"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by prairie_dad on 2007-07-30
I've got a USB wireless dongle (from Addlogix)  that seems to have the ralink 2570 chipset and runs perfectly on an old Pentium III PC with Xubuntu Feisty. It also works okay on G4 towers when they have OSX on them, given the proper Mac driver from serialmonkey.  

So, now I'm trying to attach it to a G4 tower (silver, a gig of RAM) with Feisty (Kubuntu in this case, not that it should matter, right?) and it freezes the system every time. Does that make sense?  I mean, it works on this same hardware with another OS (OS X) and on the same OS (meaning Feisty) on different hardware (x86) but not on PPC with 7.04!!

Are the drivers that _do_ work in Feisty for x86 not included in the Feisty PPC kernel?  Am I dumb for assuming that they would be, since they're in the same kernel for x86? Are they going to be incorporated into later kernels than Feisty's, like Gutsy?

Is there any way to get this thing to work? This seems to be a big issue, wireless with Ubuntu...so many complaints. I'd hate to go to another distro, not sure what diff it would make...Fedora for PPC?

thanks!

---

### Post by Kobalt on 2007-07-30
Have you also tried to use the [serialmonkey drivers]("http://ubuntuforums.org/showthread.php?t=400236") for Ubuntu ?
Unfortunately, I think I read somewhere that PPC kernels will not be shipped anymore officially by Ubuntu, since recent Macs are based on Intel chipsets...

---

### Post by prairie_dad on 2007-07-30
thanks Kobalt,

no I haven't tried the serialmonkey drivers, but I guess that's because I thought they were going to be in the new kernel of Gutsy by default.  Not so?  How does one know what drivers are included by default?

And you're right, PPC support is now community only, but I think the community size is pretty large.  And there are plenty of G4s out there without Apple cards in them, so supporting USB dongles makes some sense.  I will certainly try the recipe on the page you sent me to.

thanks and regards,

dave

---

