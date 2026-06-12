---
title: "Compaq - Atheros - Weak Wireless"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by ren_zao on 2009-08-31
Weak signal while using Linux (stronger in Win Vista).
 
Compaq Presario CQ50 Notebook PC  (115NR)
Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Ubuntu
Release 9.04 (Juanty)
Kernel Linux 2.6.28-15-generic
GNOME 2.26.1

Hardware
Memory 2.7 GiB
Processor 0: AMD Turion Dual-Core RM-70
Processor 1: AMD Turion Dual-Core RM-70

Linux newbie (installed this week) - any help is much appreciated.

Thanks.

---

### Post by lkraemer on 2009-09-01
Are you using the madwifi drivers?  If not, did wifi work when
you were done with the install?

I have a Compaq CQ50-139NR.

lkraemer

---

### Post by ren_zao on 2009-09-01
No I have yet to install such drivers on my system post-Ubuntu-install.. Maybe I should try that.. Is this "Madwifi" reliable?

---

### Post by lkraemer on 2009-09-01
My Compaq has the Atheros (AR5007) AR242x Wifi card, and I am using the
madwifi drivers.  They seem to work good.  I am not sure your card is
supported by madwifi.  I'd search the forum and see what you find.

```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig

```
will give you more information.

madwifi - if yours is supported:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
Then go to the hal-0.10.5.6 at 
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

lkraemer

---

