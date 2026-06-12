---
title: "I got problem on install WG511 v2 on Ubuntu"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by wangtao on 2006-12-08
Hi, everyone,

I have googled and searched forum. There are a problem I am facing.

The first problem is I don't have the Netgear WG511 installation disk. So I cannot get windows driver from the disk and install it by ndiswrapper.

I have downloaded several version of WG511 driver from netgear website:

[http://kbserver.netgear.com/products/WG511v2.asp](http://kbserver.netgear.com/products/WG511v2.asp)

However, I cannot extract the file. All the files download from the site is *.zip, after extract the zip, I got *.exe file, which is installation file when I use windows. I tried cabextract to extract the file, I do got several files, however, most of them are 0 bytes(include the *.dll/sys/inf). So, I can never use it.

There was a link to sunny's site which is packed the file to WG511.tar.gz, however the link is broken. I cannot download the file.

I provide my card information as following, hope anyone can give me a hand.

lspci -vv
```
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Netgear WG511 v2 54MBit/ Wireless PC-Card
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Region 1: Memory at f6010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

lspci -n
```
07:00.0 0200: 11ab:1faa (rev 03)
```

my ubuntu is 6.10
```
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)

```

Thanks.

---

### Post by wangtao on 2006-12-08
I am sorry to disturb, I found the solution on this link:

[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

although, I don't know why it's WG311v3 rather than WG511v2. It quite strange, but the driver at this link is working. I haven't give a details try, but i can install the driver, and it recognize the device.

---

### Post by FrodoB on 2006-12-08
See this instruction which contains a link to the necessary NDIS drivers that should work with your device:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by rashas on 2008-05-26
I run an ancient Acer laptop and got the Netgear WG511v2 card to work by following the NDIS Wrapper method detailed in other posts on 'Gutsy'. As soon as I upgraded to 'Hardy' the card stopped working I was stumped for a while but by going through the NDIS wrapper process again things settled down and worked.  
You will be prompted that it has been deprecated and should not be used. The other thing to remember is you will need a hard reboot before trying to make any wireless connections. It's not a perfect solution though, as I get no love from a mac 'Airport Extreme'

---

