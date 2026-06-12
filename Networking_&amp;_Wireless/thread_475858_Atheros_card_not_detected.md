---
title: "Atheros card not detected"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by shpez on 2007-06-16
```

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 16
        Memory at 54000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

I have searched these forums for days and tried almost everything suggested.  No matter what I have tried I can not get my laptop to see my wireless card!!!!

Please help and thank you in advance.

---

### Post by Ice_C on 2007-06-17
I have the same exact problem.
*bump*

Can anyone help?

---

### Post by spd106 on 2007-06-17
Make sure you have the linux-restricted-modules package installed.

If that doesn't work then you can try building the madwifi driver from svn, just download a snapshot from the madwifi.org website.

If that still doesn't work then, and only then, try ndiswrapper.

---

### Post by Ice_C on 2007-06-18
Neither the Linux restricted modules or the madwifi worked so I went and tried ndiswrapper.With Ndiswrapper I can see wireless networks, but when I try to connect the computer freezes. Any ideas?

---

### Post by stchman on 2007-06-18
> **shpez said:**
> ```

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 16
        Memory at 54000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

I have searched these forums for days and tried almost everything suggested.  No matter what I have tried I can not get my laptop to see my wireless card!!!!

Please help and thank you in advance.

Most Atheros cards work out of the box with Feisty.  What Ubuntu version are you running?

I have a procedure to install MadWifi drivers here.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked on my old Edgy installation.

---

### Post by dardack on 2007-06-19
Ice_c, i had to use ndiswrapper for my arethos card too.  Did you black list ath_pci and ath_hal and make sure that the restricted driver is unchecked?  And did you use a driver from the ndiswrapper website that matches your pci bus (i used the ones from my CD and broke my install, had to do a fresh install and used one from the ndiswrapper website that matched my pci bus number and i'm working like a charm).

---

### Post by shpez on 2007-06-21
> **stchman said:**
> Most Atheros cards work out of the box with Feisty.  What Ubuntu version are you running?

I have a procedure to install MadWifi drivers here.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked on my old Edgy installation.


I have tried following the steps on your website and still nothing at all.  I have also tried ndiswrapper, along with other things.   I read somewhere, cant remember where though, that it might have something to with that is it a windows vista driver that is not supported yet.

---

