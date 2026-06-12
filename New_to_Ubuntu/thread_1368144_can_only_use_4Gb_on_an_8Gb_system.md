---
title: "can only use 4Gb on an 8Gb system"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by new_tew_this on 2009-12-30
I have a problem where only half of my RAM is accessible. How do I fix this? When installing Ubuntu 9.04 from a disk it never asked me if I wanted 64 bit. My machine has an AMD Phenom quad core processor and 8 Gigs of Ram but only half is available. My computer origionaly had 64bit Vista installed on it. My hard drive with windows vista crashed so I replaced it and installed Ubuntu. Can I simply download and install a 64bit version of Ubuntu 9.04 directly to my system? Its a new install so there is no worries about backing anything up yet.

Also I can not get my ATI graphics driver to work.

:confused:

---

### Post by CharlesA on 2009-12-30
You would need to download and install the 64bit version.

As for the driver issue, install the proprietary driver located in hardware drivers.

---

### Post by MelDJ on 2009-12-30
> **CharlesA said:**
> 
As for the driver issue, install the proprietary driver located in hardware drivers.

its better to get the drivers from the ati site

---

### Post by LowSky on 2009-12-30
> **MelDJ said:**
> its better to get the drivers from the ati site
it might be better but for a Linux newbie it might be tougher to install... but we can help with that, here the link to the ATI website... I hope you have a newer ATI card like the HD2xxx series or higher. Otherwise you wont have much luck
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

install instructions
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by insane_alien on 2009-12-30
well, you obviously used the 32-bit disk to install. go get the 64-bit disk and reinstall.

it won't ask you becasue we can't fit both the 32-bit and 64-bit on the same CD.

if we used a DVD we could do it but no-one wants to download that much when it can be done with the cd.

just make sure to check the 64-bit option.

---

### Post by MelDJ on 2009-12-30
> **LowSky said:**
> it might be better but for a Linux newbie it might be tougher to install.

type sudo sh and type space in terminal. then drag the downloaded driver file into terminal and then just go through the graphical installation.
the ati graphic drivers in hardware drivers will most probably break the computer.

---

### Post by Sef on 2009-12-30
> go get the 64-bit disk and reinstall.

To download the 64-bit version, click [here]("http://www.ubuntu.com/getubuntu/download").

---

### Post by new_tew_this on 2009-12-30
Well I was surprised to get this many answers so fast. Thanks for all the help, I get how to get the 64 bit version now. I still can't figure out how to get the driver for my video card though. It downloaded to my desktop from ATI's web site but it won't install. Any help for this? My ATI Radeon card is a 3200.

---

### Post by halitech on 2009-12-30
what video card do you have? Did you make it executable after downloading it? right click the file - properties, check allow executing.

---

### Post by beetleman64 on 2009-12-30
You can only use 4GB on a 32-bit system. Use the 64-bit Ubuntu to use all 8GB.

---

### Post by DasEi on 2009-12-30
with that hardware I'd use 64 bit , too.
You can also use the server kernel in 32 bit, which has native pae-support
(physical address translation), as it's less hassle than to patch the generic kernel with that

---

### Post by Nburnes on 2009-12-30
To address all 8 GB you could use the PAE kernel.

---

### Post by CharlesA on 2009-12-30
> **new_tew_this said:**
> Well I was surprised to get this many answers so fast. Thanks for all the help, I get how to get the 64 bit version now. I still can't figure out how to get the driver for my video card though. It downloaded to my desktop from ATI's web site but it won't install. Any help for this? My ATI Radeon card is a 3200.

What's the exact error you are getting? Also, what's the exact model of the card? Is it integrated?

---

