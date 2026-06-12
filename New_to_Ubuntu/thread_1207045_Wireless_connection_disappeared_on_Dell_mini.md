---
title: "Wireless connection disappeared on Dell mini"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Adamantus on 2009-07-07
Hi,

My mother-in-law got a Dell Mini laptop with Ubuntu 8.04 about 7 months ago and the wireless worked out of the box until a week ago. Now, no option for "Wireless Networks" comes up in the network connections icon and it can only connect through a wired network. I don't know what is causing the problem. At about the same time, an update had an error because of lack of disk space, but we have since deleted some files and updated. But there was another error (that I'm pretty sure is unrelated). It can't seem to update openoffice.org-core. I get this error:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_lpia.deb: failed in buffer_write(fd) (10, ret=-1)

Anyway, that's probably not it. What could it be?

Also, under System>Administration>Hardware Drivers, it says there are no proprietary hardware drivers in use. Could that be a problem?


**Here's the lspci output:**

aimee@aimee:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

**And here's the ifconfig output:**

aimee@aimee:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d2:4a:e9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fed2:4ae9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1720130 (1.6 MB)  TX bytes:367305 (358.6 KB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63900 (62.4 KB)  TX bytes:63900 (62.4 KB)

---

### Post by nhasian on 2009-07-07
your wifi adaptor is the Broadcom Corporation BCM4312 802.11b/g (rev 01)

does your laptop have a physical switch or maybe a keyboard combination that turns the wifi adaptor on/off?

also can you post the output of:

```
lshw -C network
```

I know that older versions of ubuntu had problems with Broadcom wifi adaptors, but it was fixed with newer drivers in 8.10 and even better with 9.04.

---

### Post by Pogeymanz on 2009-07-07
Maybe you have to reinstall the firmware cutter. I forgot what the package is called, but if you search in Synaptic for broadcom, it will come up. I think it's bcmfwcutter or something like that.

And for your openoffice problem, have you tried uninstalling it, then reinstalling it?

---

### Post by superprash2003 on 2009-07-08
sorry..wrong thread..

---

### Post by snowpine on 2009-07-08
Dell really dropped the ball with their "Ubuntu 8.04 remix." If you browse through the forums, lots of users are having this problem the last few days. I strongly recommend installing Ubuntu 9.04 in place of the factory preinstalled 8.04.

---

