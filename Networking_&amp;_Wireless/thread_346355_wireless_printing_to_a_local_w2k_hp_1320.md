---
title: "wireless printing to a local w2k hp 1320"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by maclenin on 2007-01-25
As the getting-to-know-ubuntu process continues, I now find myself in the thick of trying to untangle printer / networking issues. And this latest issue involves trying to print (wirelessly) from my linux laptop via a (DHCP enabled) linksys wireless router to the shared hp laserjet 1320 (printer), which is connected, via parallel cable, to my windows 2000 (w2k) workstation....

**A. Background**

1. I have installed edgy eft (2.6.17-10-generic) across 3 partitions (/, /home and swap) on a dell inspiron 600m laptop - windows has been wiped away!

2. In it's past life, the linux laptop was a windows xp pro (xp) machine with a working wireless connection (via router and w2k workstation) to the printer.

3. I had set up a user account in w2k for the xp user and was able to print, at will, wirelessly, as long as I remembered to drop the firewall (at the time of printing - might there be a workaround for having to drop the firewall each time I print?) on my w2k machine.

**B. Current Status**

4. I am now trying to get my linux laptop to enjoy the same printing access as it's earlier xp incarnation....

5. In an effort to accomplish this, I have:

a. Installed (successfully) and run (unsuccessfully) the hplip printer driver and setup utilty:

[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)

b. And also tried (unsuccessfully) to use the CUPS, via:

[http://localhost:631](http://localhost:631)

6. In both (unsuccessful) instances of using hplip or CUPS, I have received errors similar (or identical) to the following:

```
[COLOR="DarkRed"]error: No devices found. Please make sure your printer is properly connected and powered-on.[/COLOR]
```

7. I can ping both the w2k workstation from the linux laptop and the linux laptop from the w2k workstation.

8. I have set up a user account on the w2k machine which matches the user and password settings of my linux user.

9. Essentially, all settings that facilitated printing from the xp laptop to the hp 1320 are still in place on the w2k workstation. I just can't, from the linux side, seem to "find" the printer....

10. I have a feeling that there are numerous settings to be toyed with, here... 

/etc/dhcp3/dhclient.conf
/etc/cups/printers.conf
/etc/cups/cupsd.conf
/etc/samba/smb.conf

...in order to complete this connection - among other things....

Any thoughts?

---

### Post by maclenin on 2007-01-25
I think I would prefer the CUPS route - if reasonable.... And I have a feeling the windows box is correctly config'ed - it's getting the linux laptop to "see" the windows box that continues to perplex.... Where might I begin?

---

### Post by maclenin on 2007-01-26
Might (the) Samba be the answer for printing FROM linux TO a printer attached to a Windows 2000 workstation? Any kernel of wisdom will do!

---

### Post by maclenin on 2007-01-27
Shameless bumping to try to get someone to take a peek at this issue with me.... Meanwhile, I continue to "goog"....

---

