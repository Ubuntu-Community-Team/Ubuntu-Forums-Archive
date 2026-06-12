---
title: "Trendnet TEw-423PI PCI card not playing nice"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by ibanez4string on 2008-03-01
So I purchased a Trendnet TEW-423PI PCI card h/W C1.0R.  This has the Realtek rtl8185l radio/chipset in it.  I installed Mythbuntu 7.10 which I believe is running Ubuntu Gutsy Gibbon.  I am running an AMD 64 system.  It detects the card and tries to run a r8180 driver.  Unfortunately the card is not very responsive as it won't see any networks or allow me to access it.  

I am trying to run ndiswrapper and the current xp driver that came with the card.  So I have gotten the screen where ndiswrapper has installed the driver, but the alternate driver is still present.  I blacklisted the r8180 in blacklist and blacklist-compat after rmmod ing it.  Uninstalled and reinstalled ndiswrapper and still get the alternate driver.  

What am I doing wrong?  I just want a wireless connection.  

Thanks for the help.

---

### Post by ibanez4string on 2008-03-02
Pleas help

---

### Post by coolbrook on 2008-03-02
Try the (Win 98/ME) driver linked in my signature.

---

### Post by ibanez4string on 2008-03-04
It looks like the same driver i was trying to load, but i tried it anyway, after uninstalling ndiswrapper and deleting it's files.  Tried it with new drivers and I still get the hardware detected and an alternate driver being used when i use ndiswrapper -l.  It says r8180 being used as the alternate driver.  I have blacklisted this and it still keeps coming up.  How do i get rid of it?

Thanks,

---

### Post by coolbrook on 2008-03-04
I could be wrong but I don't think the alternate driver is in use if *ndiswrapper -l* shows what you have "installed."

```
steven@RAPHAEL:~$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)
```

```

sudo depmod -a
sudo modprobe ndiswrapper

```

..works for me.

---

