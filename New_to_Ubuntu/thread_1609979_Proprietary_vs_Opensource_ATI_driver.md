---
title: "Proprietary vs Opensource ATI driver"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Kyluke on 2010-10-31
Hey does anyone know which is better all round
ATI Proprietary Drivers or ATI Opensource Drivers?

---

### Post by bioterror on 2010-10-31
> **Kyluke said:**
> Hey does anyone know which is better all round
ATI Proprietary Drivers or ATI Opensource Drivers?

I am using xserver-xorg-video-radeonhd with my ATI Technologies Inc RV710 [Radeon HD 4350] and I've got nothing to complain.

So I'm using OpenSource if I got it right ;)

---

### Post by coffeecat on 2010-10-31
> **Kyluke said:**
> Hey does anyone know which is better all round
ATI Proprietary Drivers or ATI Opensource Drivers?

This is too much of a generalisation. It depends on your particular card. See this page for the open-source driver:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> This driver is not as fast as the closed-source, proprietary "fglrx"  driver from AMD/ATI Inc. for some cards, but has better dual-head  support, and supports some older chipsets that fglrx does not.I'm using the same HD4350 chipset in my desktop as bioterror and a HD4200 in one of my laptops with the open-source driver in both. I get 3d acceleration sufficient for compiz, but I'm not a gamer. If I had wanted good acceleration for gaming I would probably have been using the fglrx proprietary driver.

Also - the proprietary driver doesn't support some older cards at all in recent versions of Ubuntu. See:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

### Post by Kyluke on 2010-10-31
I am running:

fnb@fnb:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]

What's the best driver for that?

---

### Post by alexandari on 2010-10-31
They both suck my friend.

---

### Post by Mark Phelps on 2010-10-31
Unfortunately, there's really no one simple, always correct answer.

In general, if what you want is fast 3D gaming graphics, the proprietary driver has historically been the best.

But, when ATI got bought by AMD, they dropped support for a lot of cards, and in their absence the open-source drivers got better and better.

I'm running one of the legacy ATI cards using the open-source drivers and, for the first time, I can get full desktop effects.  But, I don't do 3D gaming, so I can't say how that is with the current open-source drivers.

Also, recent propietary drivers have been experiencing a LOT of problems.  You see that from the posts here, and you can see the details if you go to the Phoronix forums -- where they do a LOT of testing of the drivers.

Some folks continue to use the RadeonHD open-source drivers, and have had good success with them -- but they have been discontinued.

So, in sum, there is no simple one vs. the other answer.

---

