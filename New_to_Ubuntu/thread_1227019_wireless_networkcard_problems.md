---
title: "wireless networkcard problems"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by lestatius on 2009-07-30
I have a wireless network card and the strange thing is sometimes is seems to connect automatically and sometimes it doesn't. Sometimes my wireless network shows up in the list of wireless and when I try connect it says my wpa2 key is incorrect(but I know it is correct), and then sometimes when I restart it does connect automatically. Anyone have any idea why this is?

---

### Post by pbateman on 2009-07-30
What kind of network card it is? I am having similar issues, just mostly frequent disconnections and it never auto-connects when i boot up. I have the infamous Atheros wireless card on a Thinkpad laptop and I know there's issues with them.

---

### Post by lestatius on 2009-07-30
> **pbateman said:**
> What kind of network card it is? I am having similar issues, just mostly frequent disconnections and it never auto-connects when i boot up. I have the infamous Atheros wireless card on a Thinkpad laptop and I know there's issues with them.

[http://www.linksysbycisco.com/US/en/products/WMP54G](http://www.linksysbycisco.com/US/en/products/WMP54G)

---

### Post by mapes12 on 2009-07-30
> **lestatius said:**
> I have a wireless network card and the strange thing is sometimes is seems to connect automatically and sometimes it doesn't. Sometimes my wireless network shows up in the list of wireless and when I try connect it says my wpa2 key is incorrect(but I know it is correct), and then sometimes when I restart it does connect automatically. Anyone have any idea why this is?

Please post the output to ```
lspci
```

---

### Post by mapes12 on 2009-07-30
> **pbateman said:**
> What kind of network card it is? I am having similar issues, just mostly frequent disconnections and it never auto-connects when i boot up. I have the infamous Atheros wireless card on a Thinkpad laptop and I know there's issues with them.
pbateman,

It sounds like you need to install the madwifi driver to your system to support your Atheros card. Here's some links:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by pbateman on 2009-07-30
> **mapes12 said:**
> pbateman,

It sounds like you need to install the madwifi driver to your system to support your Atheros card. Here's some links:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

[http://madwifi-project.org/](http://madwifi-project.org/)

Thanks! I'll try that tonight...I've been reading a lot trying to find a solution to this, and while I had seen this suggestion before I also saw postings stating this was no longer necessary in 9.04 cos the driver was built in already (?) and that this driver was so that the card is recognized?
This is why i hadn't tried this yet since my card is recognized...just doesn't connect very well.
I'll definitely give it a shot tonight once im back home though

---

### Post by lestatius on 2009-07-30
> **mapes12 said:**
> Please post the output to ```
lspci
```

I did a full reinstall and my wireless card seems to be working fine now. Maybe it takes a few minutes or half a minute to find my network. That would be that I'm just impatient sometimes lol. but here's the output I got. 


maarten@jigsawpuzzle:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9460
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi



The strange thing I find about this is that. I have a  WMP54G and on my other partition I have windows 7 installed that works on an abnormal driver. Now how come that same driver is showing up in ubunut? I find that strange?

05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by lestatius on 2009-07-31
I still seem to be having the same problem. here's the output:


maarten@jigsawpuzzle:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9460
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
maarten@jigsawpuzzle:~$

---

### Post by mapes12 on 2009-08-01
The RT61 chipset is reported as working out of the box in 8.10 and higher:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

but there are other posts that may help you out:

[http://www.google.co.uk/search?hl=en&q=RaLink+RT2561%2FRT61+ubuntu&btnG=Google+Search&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&q=RaLink+RT2561%2FRT61+ubuntu&btnG=Google+Search&meta=&aq=f&oq=)

---

### Post by shiroyoshida on 2009-08-08
Hello, 

I've been having problems with this wireless card (Network controller: RaLink RT2561/RT61 802.11g PCI) as well and this blog post helped sort everything out: [http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/](http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/) 

I hope it will help you as well!

---

