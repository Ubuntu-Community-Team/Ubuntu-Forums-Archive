---
title: "How to get webcam working"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Nevon on 2009-08-21
Hello everyone,

The built-in webcam in my laptop used to work in 8.04 (and possibly 8.10 - although I'm not sure). However, it has not worked now for over 6 months, due to reasons unknown.

**I would like some help diagnosing what the problem is, and possibly find some ways to get it working again.** I know that there's not a problem with the hardware, as it does work in Windows. 

I do not know the make or model of the webcam, but I'm sure that can be found out from 'lspci'.

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
09:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
09:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
09:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```

I have tried it out in Cheese, and it does not work. I could test it in some other applications as well - if you give me their names.

---

### Post by rajeev1204 on 2009-08-21
> **Nevon said:**
> Hello everyone,

The built-in webcam in my laptop used to work in 8.04 (and possibly 8.10 - although I'm not sure). However, it has not worked now for over 6 months, due to reasons unknown.

**I would like some help diagnosing what the problem is, and possibly find some ways to get it working again.** I know that there's not a problem with the hardware, as it does work in Windows. 

I do not know the make or model of the webcam, but I'm sure that can be found out from 'lspci'.

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
09:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
09:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
09:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```

I have tried it out in Cheese, and it does not work. I could test it in some other applications as well - if you give me their names.

The webcam can be found from the command lsusb.Because a webcam is a usb device.

So type that in a terminal and paste it here.

---

### Post by Nevon on 2009-08-21
> **rajeev1204 said:**
> The webcam can be found from the command lsusb.Because a webcam is a usb device.

So type that in a terminal and paste it here.

Will do.

lsusb:
```
Bus 002 Device 003: ID 5986:0200 Acer, Inc 
Bus 002 Device 002: ID 05ac:1262 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by rajeev1204 on 2009-08-21
So which one is your webcam?The acer, this model is supposed to work out of the box on ubunty 8.04 onwards.

What version of ubuntu areyou using?

---

### Post by Nevon on 2009-08-21
> **rajeev1204 said:**
> So which one is your webcam?
That, I do not know. However, I do know it's not the acer or whatever it is that says apple. I think the make or model is called Bison, or something like that.

> **rajeev1204 said:**
> What version of ubuntu areyou using?
Didn't I say that in the first post? If so, I'm sorry. I'm using 9.04.

---

### Post by Jazzy_Jeff on 2009-08-21
How did you install 9.04? Did you upgrade or do a clean install?

---

### Post by Nevon on 2009-08-21
> **Jazzy_Jeff said:**
> How did you install 9.04? Did you upgrade or do a clean install?

Clean install.

---

### Post by Nevon on 2009-08-24
No more ideas?

---

### Post by Codix121 on 2009-08-24
Connect your webcam and open your terminal, type in

```
lsusb
```

and post your results.

---

### Post by budbaker44 on 2009-08-24
did you install a web cam package through Add/Remove. When I switched to Ubuntu 9.04 from Vista I had to install Cheese web cam to get mine to work. There is another one in Add/Remove but I did not like it as much.

---

### Post by argos3016 on 2009-08-24
Try if cheese detects webcam
sudo apt-get install cheese

---

### Post by Nevon on 2009-08-24
> **Codix121 said:**
> Connect your webcam and open your terminal, type in

```
lsusb
```

and post your results.

It's a built-in webcam, and I already have posted the output from lsusb. However, I can do it again if you'd like:
```
Bus 002 Device 002: ID 5986:0200 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

> **budbaker44 said:**
> did you install a web cam package through Add/Remove. When I switched to Ubuntu 9.04 from Vista I had to install Cheese web cam to get mine to work. There is another one in Add/Remove but I did not like it as much.> **argos3016 said:**
> Try if cheese detects webcam
sudo apt-get install cheese

Yes, like I said in the first post, I'm already using cheese. However, it doesn't not work in amsn either.

---

