---
title: "Wifi Troubles"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by kilroy423 on 2007-05-29
my wifi refuses to work, what am I missing?

```
dan@dan-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev  03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controlle r (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Stora ge Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0398 (rev a1)
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c
0000:08:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 01 )

```

```
dan@dan-laptop:~$ ndiswrapper -l
Installed ndis drivers:
w39n51          driver present, hardware present
```

```
dan@dan-laptop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

```

thx for any help,

dan

---

### Post by kilroy423 on 2007-05-30
bump

---

### Post by kilroy423 on 2007-05-31
bump

---

### Post by stoian on 2007-05-31
my wifi card worked out of the box with ubuntu 6.06 all the way up to 7.04 (present) but some update a few days ago broke wifi access. i can see wireless networks but cannot connect to any. (well, duh, not even my own wireless router)...

hopefully somebody will solve this at ubuntu hq.

similar post here:
[http://ubuntuforums.org/showthread.php?p=2752526#post2752526](http://ubuntuforums.org/showthread.php?p=2752526#post2752526)

thanks

---

### Post by stoian on 2007-06-01
a bug has been logged and confirmed:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117580)

---

### Post by cornsnap on 2007-06-02
I don't even see a wireless device being identified in your lspci log.  Correct?

---

### Post by cornsnap on 2007-06-02
Did you try using wlassistant?

---

