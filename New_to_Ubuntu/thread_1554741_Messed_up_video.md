---
title: "Messed up video"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by troyguffey on 2010-08-17
I was trying to change the split between Lucid-10.04-amd64 and WinXP, and somehow managed to mess up my formerly working video drivers.  Grub2 shows OK, but trying to boot normally kills the monitor.  Trying the recovery mode failsafeX works, but can't get the resolution to change from 1024x768.  None of the options presented work except "Run Ubuntu in low-resolution mode once only".

How can I get Ubuntu to redetect videocard (ATI Radeon 1800XL All-in-Wonder) and monitor (Dell M992) and reset the boot options.

If this was WinXP, I would boot to Safe Mode.

I have the LiveCD-amd64 available (which works!)

---

### Post by clhsharky on 2010-08-17
troyguffey

Do not try to install fglrx driver, did you?
Open source radeon is the correct driver for your legacy card.

Sharky

---

### Post by troyguffey on 2010-08-17
> **clhsharky said:**
> troyguffey

Do not try to install fglrx driver, did you?
Open source radeon is the correct driver for your legacy card.

Sharky

I did TRY to install the proprietary driver after I lost video, but it would not install.  Something about an unsupported distro.

---

### Post by troyguffey on 2010-08-17
> **clhsharky said:**
> troyguffey

Do not try to install fglrx driver, did you?
Open source radeon is the correct driver for your legacy card.

Sharky

I did TRY to install the proprietary driver after I lost video, but it would not install.  Something about an unsupported distro..

---

### Post by troyguffey on 2010-08-19
Managed a partial fix by copying /etc/x11/xorg.conf.failsafe => xorg.conf

I got back the 1600x1200 mode doing that.

Monitors is still showing up as "Unknown" and I am unable to change resolution.

Any idea how to get full function back?

---

