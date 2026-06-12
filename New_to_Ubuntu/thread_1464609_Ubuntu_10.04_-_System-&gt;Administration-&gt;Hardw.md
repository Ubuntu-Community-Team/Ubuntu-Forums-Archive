---
title: "Ubuntu 10.04 - System-&gt;Administration-&gt;Hardware Drivers"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by eBryggis on 2010-04-28
Hey!

I am on Ubuntu 10.04 RC. Just installed.

The problem is that I can not access System -> Administration -> Hardware Drivers. No error is given, it is just silent.

On the other hand when running /usr/bin/jockey-gtk from terminal I receive the following error. [http://ubuntu.pastebin.com/MswNR1ah]("http://ubuntu.pastebin.com/MswNR1ah")

I would be very happy if anyone could help me on this. Except for this, the OS looks great.

---

### Post by mk1w86 on 2010-04-28
Could you please post the output of:

```
lspci
```

so we can see what graphics hardware you have?

Have you ever used Ubuntu 9.10 or earlier and has that worked?

There is a possibility it is a bug in Lucid, although by this time I would have thought most major bugs had been ironed out. :???:

---

### Post by eBryggis on 2010-04-28
Computer is brand new. Never tried any OS on it earlier. I have noticed a screen flicker, that occurs on random and rarely: That&#347; why I wanted to check "hardware drivers".

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)


```

---

### Post by eBryggis on 2010-04-28
Another thing I might mention is that when I turn down the screen brightness using defined keys for that the brightness on the ubuntu meter goes down. But no change on overall screen brightness level.

---

### Post by philinux on 2010-04-28
What machine is it. If you've got a launchpad account please bug it using this.

```
ubuntu-bug jockey-gtk
```

If not then good idea to open one.

---

### Post by eBryggis on 2010-04-28
Thanks for the tips.

The machine:
Asus UL30VT-QX008V

Launchpad:
Created account, submitted data

Bug reported here for those of you interested:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/571389](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/571389)

---

### Post by philinux on 2010-04-28
> **eBryggis said:**
> Thanks for the tips.

The machine:
Asus UL30VT-QX008V

Launchpad:
Created account, submitted data

Bug reported here for those of you interested:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/571389](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/571389)

You could try this.....

```
sudo apt-get install nvidia-current
```

---

### Post by eBryggis on 2010-04-28
Thanks, that solved my issue with Hardware Drivers.
After installing that it works. I can launch it without errors.

---

