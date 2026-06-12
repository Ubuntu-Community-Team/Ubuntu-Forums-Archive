---
title: "New to linux( Have some problems)"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Panekoek on 2011-03-05
Hi Guys.

I am new to linux and so far i am LOVING it.

I just have two prblems if you could please help me out.

1. I have a Hp Pavilion dv6 2190US Laptop and it had windows on but now only linux. The problem is that i can't get the wireless to work. Is it the driver that is missing ? 

2. I downloaded and installed the Kylix programming app from the software centre but I cant seem to find it. Any suggestions?

Thanks in advance 

~Pane

Ps: Sorry for being so newbie :(

---

### Post by pastalavista on 2011-03-05
With an ethernet cable connected to your router/modem (which I assume is how you downloaded and installed kylix) you should open System/Administration/Hardware Drivers tool to install any proprietary drivers for your machine.

Programs installed via software center usually create a launcher in the Applications menu under the category of wherever it was in the Software Center (ie: Games, Internet etc). ou can find where it is installed in the system using terminal ```
locate kylix
```

---

### Post by Hippytaff on 2011-03-05
Hi and Welcome

If the above doesn't work please post the output of```
lspci | grep -i wireless
``` so we can see what wireless card you have.

---

### Post by Panekoek on 2011-03-05
It still cant find Kylix. Iv tried installing and uninstalling but it does not work. The one that i installed is called: fp-units-i386. Its the only thing that came up in the search for Kylix.

As for the driver, do you know where I can get a driver for my Wireless?

---

### Post by Panekoek on 2011-03-05
It does not get a response.

---

### Post by Hippytaff on 2011-03-05
do ```
lspci
``` in a terminal and post the results here so we know which driver you need

---

### Post by Jerry N on 2011-03-05
> **Panekoek said:**
> 
2. I downloaded and installed the Kylix programming app from the software centre but I cant seem to find it. Any suggestions?


I assume you have re-booted your computer since installing Kylix.  I have found that to be necessary before some newly installed applications show up in the menus.

Jerry

---

### Post by Panekoek on 2011-03-05
> 00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)



Thats the response.

@ Jerry: I think I am confused here. Can one download the actual Kylix app from the software centre or do you have to buy it??

---

### Post by Hippytaff on 2011-03-05
This is the driver> BCM43225

As I thought, it's broadcom and they tend to be a bit tricky sometimes. Have a look at[ this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and let us know how it goes.

---

### Post by Panekoek on 2011-03-05
I am really terrible with this stuff... Do not know what im looking for :(

---

### Post by Hippytaff on 2011-03-05
Follow the instructions from Step 1

```

 sudo apt-get update && sudo apt-get install bcmwl-kernel-source

```
activate the driver by going to go [B]System > Administration > Hardware/Additional Drivers
[/B]

---

### Post by Jerry N on 2011-03-05
> **Panekoek said:**
> 
@ Jerry: I think I am confused here. Can one download the actual Kylix app from the software centre or do you have to buy it??

Maybe I'm confused - I don't know a thing about Kylix but in your first post you said that you had downloaded from the software center and installed it but then you couldn't find it in your menus.

Jerry

---

### Post by Panekoek on 2011-03-06
I downloaded something that had the word kylix in it but i do not think it is the actual program...

---

### Post by Panekoek on 2011-03-06
@ Hippytaff

WHen i click additional drivers, it is there but it says it is not in use.

---

### Post by Panekoek on 2011-03-06
Good news, wireless randomly started working :P

---

