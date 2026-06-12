---
title: "My desktop clock is always out of sync"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by ALF102 on 2009-11-04
This always happen whenever I just start ubuntu, it seems the clock is always late by the-total-amount-of-time I turn off the PC. Ex. if I have turn off the PC 3 hours ago, the clock would be late by 3 hours.

---

### Post by madnessjack on 2009-11-04
This sounds more like a problem with your BIOS. Do you know that the clock worked before?

---

### Post by danill2008 on 2009-11-04
Is your time-zone settings correct and also your BIOS settings?

---

### Post by ALF102 on 2009-11-04
Yes, timezone is set correctly. This started as soon as I started the PC for the second time after the first installation when I realised the clock is very late.

---

### Post by x C0MMAND0 x on 2009-11-04
Correct me if I'm wrong, but isn't it the CMOS battery on the motherboard which is responsible for keeping the time going when the computer is off?

How old is your computer?

---

### Post by philinux on 2009-11-04
Could be the date battery in the motherboard dying.

Try installing the ntp package or system>admin>time and date.
Synchronise with internet servers.

---

### Post by danill2008 on 2009-11-04
> **x C0MMAND0 x said:**
> Correct me if I'm wrong, but isn't it the CMOS battery on the motherboard which is responsible for keeping the time going when the computer is off?

How old is your computer?

Was just thinking the same thing...

---

### Post by ALF102 on 2009-11-04
Well, this Laptop was bought last year and I still have my Windows XP, what bugs me is that the clock on the Windows XP is functioning fine and correctly

---

### Post by Excedio on 2009-11-04
I suggest setting your clock to follow an NTP server instead.

System > Administration > Time and Date

Unlock and then change the Configuration to "Keep synchronized with Internet Servers"

---

### Post by ALF102 on 2009-11-04
Yeah, I've tried that one and it works really fine. Thank you guys for the help

---

### Post by QIII on 2009-11-04
If you have XP/Ubuntu in a dual boot configuration, you may be running into the dreaded UTC settings gremlin.

Do

```
sudo cp /etc/default/rcS /etc/default/rcS_backup
```

```
sudo gedit /etc/default/rcS
```

Scroll down to the line that says "UTC=yes" and change it to "UTC=no".

---

