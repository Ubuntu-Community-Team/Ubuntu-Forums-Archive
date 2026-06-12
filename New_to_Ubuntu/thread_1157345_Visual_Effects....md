---
title: "Visual Effects..."
date: 2009-05-12
forum: New to Ubuntu
---

### Post by stmasi on 2009-05-12
Ubuntu 9.04 (jaunty)
Dell Latitude D630

How do I get the "extra" visual effects to work? Every time I attempt to change from "none" to "extra" I simply get a window stating that the visual effects were not enabled.

---

### Post by Dynaflow on 2009-05-12
Post the terminal output of ```
lspci
```

---

### Post by LesterPalooza on 2009-05-12
Make sure you have installed the latest video card drivers for your laptop. :)

---

### Post by stmasi on 2009-05-14
> **Dynaflow said:**
> Post the terminal output of ```
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

I see the problem. There are several hardware components missing (I'm assuming because drivers haven't been loaded). However, I do not know how to go about "discovering" the hardware and loading the drivers.

Anyone have the time to assist?

Thanx.

---

### Post by stmasi on 2009-05-14
N e 1 ?

;)

---

### Post by Niniel on 2009-05-14
How about using complete words? ):P

There's nothing missing. But, 9.04 is having problems with some Intel graphics chips right now, and I think yours is one of them. So until that's fixed, your only option, if you can't do without desktop effects, is to use an older version of Ubuntu, e.g. 8.10.

---

### Post by bacardiandwatermelon on 2009-05-14
Have you tried this?

[http://ubuntuforums.org/showthread.php?t=799070&highlight=GM965]("http://ubuntuforums.org/showthread.php?t=799070&highlight=GM965")

---

### Post by FirstByté on 2009-05-14
> **stmasi said:**
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 **VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller** (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)



> **stmasi said:**
> 
I see the problem. There are several hardware components missing (I'm assuming because drivers haven't been loaded). However, I do not know how to go about "discovering" the hardware and loading the drivers.

Anyone have the time to assist?

Thanx.

We seem to be in the same league pal. As rightly explained [here]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+dell") You apparently have an Intel graphics card as I have too. 

Ubuntu 9.04 Jaunty runs kernel version 2.6.28, with the Graphics Execution Manager (GEM) which has been migrated to the kernel. This should simplify and improve the efficiency of X Server memory management, but requires some changes to graphics drivers.

As it is at the moment, a couple work-around exist [here]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+dell")

We can only hope the version 2.6.29 handles this adequately.

---

### Post by stmasi on 2009-05-14
> **bacardiandwatermelon said:**
> Have you tried this?

[http://ubuntuforums.org/showthread.php?t=799070&highlight=GM965]("http://ubuntuforums.org/showthread.php?t=799070&highlight=GM965")

THIS WORKED!!!

It reported an error, but I chose to ignore it and now everything works perfectly!

Thanx much!!!

=D>     \\:D/

---

### Post by entr3p on 2009-06-04
You can enable the blacklist manually as well which is very easy to do :D. You can also re-enable the black list any time so that's useful if anything goes wrong. You can check how to do that with this article.


[Fix Intel graphics on Ubuntu 9.04 - Enabling visual effects]("http://www.learningubuntu.com/articles/fix-intel-graphics-ubuntu-904-enabling-visual-effects")

---

