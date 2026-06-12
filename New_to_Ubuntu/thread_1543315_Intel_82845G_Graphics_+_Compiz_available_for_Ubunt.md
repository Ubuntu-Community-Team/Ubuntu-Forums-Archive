---
title: "Intel 82845G Graphics + Compiz available for Ubuntu 10.04?"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Brushstroke on 2010-07-31
I've been searching for some way to enable Compiz on Ubuntu 10.04 on this old desktop that has the Intel 845G integrated driver. Apparently it's blacklisted for Compiz, but I'm wondering if anyone has had any success in enabling Compiz anyway?

On top of this, there's another problem I have. See, I WOULD upgrade the graphics card and I've tried a couple different cards on this computer (HP Pavilion a1010n w/ 2GB RAM, it only supports PCI unfortunately) but every time I use one, the BIOS detects it and it runs fine...until I end up with a CLI instead of Ubuntu's GUI login and Ubuntu fails to boot. It gives me notices like it can't detect certain files (I couldn't name them off the top of my head) and that partitions aren't able to be mounted. And eventually it just hangs there and when I take the card out, I get the same screen and have actually had to reinstall the OS because of this. What's causing this?

Thanks!

---

### Post by Terl on 2010-07-31
What kind of cards have you tried?  If you, for example, tried an older nVidia or ATI card some of them require legacy drivers as support for them has been dropped with X0rg.

---

### Post by Brushstroke on 2010-07-31
ATI Radeon 7000 PCI 32MB, and an nVidia GeForce 5200 PCI 256MB which I no longer have. I've looked around and the ATI card appears to not even have very much support from open-source drivers, let alone proprietary support.

---

### Post by Brushstroke on 2010-08-01
Bump.

---

### Post by gandaran on 2010-08-01
> I've been searching for some way to enable Compiz on Ubuntu 10.04 on this old desktop that has the Intel 845G integrated driver. Apparently it's blacklisted for Compiz, but I'm wondering if anyone has had any success in enabling Compiz anyway?
some cards don't support 3D effects so you will not be able to run compiz with 2D cards but you can still enable some effects using the metacity compositing manager instead and be able to have some transparency or run a dock like avant window navigator, the AWN dock must be the trunk version that runs with the compositing manager.

> On top of this, there's another problem I have. See, I WOULD upgrade the graphics card and I've tried a couple different cards on this computer (HP Pavilion a1010n w/ 2GB RAM, it only supports PCI unfortunately) but every time I use one, the BIOS detects it and it runs fine...until I end up with a CLI instead of Ubuntu's GUI login and Ubuntu fails to boot. It gives me notices like it can't detect certain files (I couldn't name them off the top of my head) and that partitions aren't able to be mounted. And eventually it just hangs there and when I take the card out, I get the same screen and have actually had to reinstall the OS because of this. What's causing this?
did you disable the onboard card in the BIOS? 
and installed the driver for the new card?

---

### Post by Terl on 2010-08-01
> **Brushstroke said:**
> ATI Radeon 7000 PCI 32MB, and an nVidia GeForce 5200 PCI 256MB which I no longer have. I've looked around and the ATI card appears to not even have very much support from open-source drivers, let alone proprietary support.

I think both those cards are unsupported.  The ATI card is quite "old" and you will not have much luck with that one.  I think you may have to upgrade the computer or settle for not running full compiz effects

---

