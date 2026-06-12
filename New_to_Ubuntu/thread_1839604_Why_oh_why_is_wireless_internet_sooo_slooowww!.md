---
title: "Why oh why is wireless internet sooo slooowww!"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2011-09-05
Am not new to this game and have just re-installed Ubuntu 11.04 x64 after previously removing it due to slow internet speeds compared to Windows. So I installed Windows 7 and got great fast internet browsing speeds using Firefox/Chrome when I suddenly realized what the hell am I doing going back to Windows after running Linux for so long! SO am back in this every going problem of really slow internet browsing speeds in Ubuntu 11.04 x64. Don't get me wrong downloading directly and torrent speeds are great its just when I use internet browsers that it goes slow. Sometimes it sits on Connected to [www.somesite.co.nz](www.somesite.co.nz) for a good 25 seconds before loading.

I use Firefox 6.01.

My Wireless device is using the rt73usb driver.
I have disabled IPV6 I think and I think I have power management turned off.

I am desperate to get this internet speeded up as I bloody love Ubuntu!

```

terry@SKYNET:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13)
00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13)
00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:91a3] (rev 11)
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
03:00.0 VGA compatible controller [0300]: nVidia Corporation GF100 [GeForce GTX 470] [10de:06cd] (rev a3)
03:00.1 Audio device [0403]: nVidia Corporation GF100 High Definition Audio Controller [10de:0be5] (rev a1)
05:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
05:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
06:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
06:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
09:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
09:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]

```

Any suggestions?

Terry

---

### Post by alphacrucis2 on 2011-09-05
> **terrykiwi83 said:**
> Am not new to this game and have just re-installed Ubuntu 11.04 x64 after previously removing it due to slow internet speeds compared to Windows. So I installed Windows 7 and got great fast internet browsing speeds using Firefox/Chrome when I suddenly realized what the hell am I doing going back to Windows after running Linux for so long! SO am back in this every going problem of really slow internet browsing speeds in Ubuntu 11.04 x64. Don't get me wrong downloading directly and torrent speeds are great its just when I use internet browsers that it goes slow. Sometimes it sits on Connected to [www.somesite.co.nz](www.somesite.co.nz) for a good 25 seconds before loading.

I use Firefox 6.01.

My Wireless device is using the rt73usb driver.
I have disabled IPV6 I think and I think I have power management turned off.

I am desperate to get this internet speeded up as I bloody love Ubuntu!

```

terry@SKYNET:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13)
00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13)
00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:91a3] (rev 11)
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
03:00.0 VGA compatible controller [0300]: nVidia Corporation GF100 [GeForce GTX 470] [10de:06cd] (rev a3)
03:00.1 Audio device [0403]: nVidia Corporation GF100 High Definition Audio Controller [10de:0be5] (rev a1)
05:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
05:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
06:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
06:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
09:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
09:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]

```

Any suggestions?

Terry


In firefox about:config did you try setting network.dns.disableIPV6 to true? That may help.

---

### Post by 3rdalbum on 2011-09-06
Sounds a bit like a DNS problem; go to the Network Manager indicator in your top panel and come down to Connection Information. What's your Primary and Secondary DNS in there?

Go to Edit Connections, edit your wireless connection in there, and change the "Method" in the IPv4 Settings tab to "DHCP Addresses Only", and then put in the following into the DNS Servers field:

```
208.67.222.222, 208.67.220.220
```

Save and disconnect, then reconnect. You'll be using the OpenDNS server instead for DNS. Do websites load quicker? If they do, then you can just use OpenDNS permanently, or you can post your current DNS addresses into here and we'll see if there's anything wrong with it.

---

### Post by AddyTx on 2011-10-24
Wonderful! I had the same problem, seems to be helping... Do I have to do anything special to use OpenDNS permanently or do I just keep the changes you just gave?

---

