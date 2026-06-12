---
title: "HDMI audio not working in Laptop MSI PR200"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by rhenium3 on 2010-08-17
Hi,

So have a little (big) problem. The HDMI sound output is not working for my laptop. It only does sound from the laptop, and would really like to have the sound from our new tv (Samsung). Video output is fine.

I installed the ALSA driver described here ([http://ubuntuforums.org/showthread.php?t=205449&highlight=hdmi+audio+problems](http://ubuntuforums.org/showthread.php?t=205449&highlight=hdmi+audio+problems)), and I think I did it correctly. Well, nothing broke at least.  But truthfully that tutorial was a bit above my ubuntu knowledge.

Have Ubuntu 10.04 Lucid Lynx. Pls let me know if you need more info.

Thanks for the help in advanced! Oh, in the sound preferences -> Output if I change the Connector to analog output I get no sound.

Thanks again.

---

### Post by LowSky on 2010-08-17
What chipset does you laptop use? ATI, Nvidia, Intel? If you don't know or are not sure, post the results to this command

```
lspci
```
(thats lowercase L)
Are you sure you enable digital sound in alsamixer?

---

### Post by rhenium3 on 2010-08-17
> **LowSky said:**
> 
Are you sure you enable digital sound in alsamixer?
No I'm not, but no idea how to enable it or how to see if I enabled it in alsamixer...


It is intel, here is the info:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Memory Stick Card Reader Controller
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

---

### Post by rhenium3 on 2010-08-18
bumb, any ideas?

---

### Post by rhenium3 on 2010-08-20
At this point any ideas will help - I've googled, I've looked on the forum, I've installed various packages with no results.

Whoever helps me solve this will get a package of moose and reindeer jerky from Sweden (yes, I'm bribing at this point!)

Hjalp!

---

