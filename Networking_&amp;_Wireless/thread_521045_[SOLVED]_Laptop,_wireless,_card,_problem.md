---
title: "[SOLVED] Laptop, wireless, card, problem"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by ti3st0 on 2007-08-08
Hey all. 

I installed Ubuntu on my laptop and I'm having problems getting my wireless card to be recognized. I've tried a few things but nothing works. The card is in the slot, but the lights don't flash and Ubuntu doesn't recognize its existence. Is there anything I can do short of getting a new wireless card? 

Here are some links to the card that I have:  

[http://www.geeks.com/details.asp?invtid=WLG-1101&cat=NET](http://www.geeks.com/details.asp?invtid=WLG-1101&cat=NET)

[http://www.evertek.com/viewpart.asp?auto=17054](http://www.evertek.com/viewpart.asp?auto=17054)

Thanks in advance!

- Robert

---

### Post by kevdog on 2007-08-09
You need to type at the command prompt and cut and paste the output of the following:

lspci -nn
lshw -C network

---

### Post by ti3st0 on 2007-08-09
The output for lspci -nn is:
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:04.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:04.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1978 Maestro 2E [125d:1978] (rev 10)
00:09.0 Ethernet controller [0200]: Intel Corporation 82557/8/9 [Ethernet Pro 100] [8086:1229] (rev 09)
00:09.1 Serial controller [0700]: Agere Systems LT WinModem [11c1:0445]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

The output for lshw -C network is:

  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:39:6c:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:41280000-41280fff ioport:3400-343f iomemory:41100000-4111ffff irq:11
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:24000000-2400ffff iomemory:24010000-2401ffff irq:11

---

### Post by ti3st0 on 2007-08-10
I hate to be double posting, but does anybody have a solution?

---

### Post by hghtn on 2007-08-10
How do you get to a command prompt, please bear with me I'm new

---

### Post by ti3st0 on 2007-08-10
And what does That have to do with anything?

Do you mean console?

---

### Post by hghtn on 2007-08-10
> **kevdog said:**
> You need to type at the command prompt and cut and paste the output of the following:

lspci -nn
lshw -C network

How do you get to a command prompt?

---

### Post by ugm6hr on 2007-08-10
> **ti3st0 said:**
> 
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

This is your wifi card.  I believe it will work with ndiswrapper (install *ndiswrapper-common* and *ndisrapper-utils-1.9* from Synaptic, or compile the newest version manually), and use the drivers as suggested for your card here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)
(search for the pciid *11ab:1faa* with Ctrl+F in Firefox) - there are lots suggested, or just use the driver on the CD.
Using ndiswrapper - instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper)
Obviously, you need to use the appropriate driver (and not copy the instructions above blindly).
Any problems - just post where you got up to, and the error messages, and someone will hopefully point you in the right direction.

PS: @hghtn - see the link in my signature about "Code entries"

---

### Post by ti3st0 on 2007-08-10
Thanks a lot for that! It worked like a charm.

---

### Post by ugm6hr on 2007-08-11
> **ti3st0 said:**
> Thanks a lot for that! It worked like a charm.

Good to hear :)

It's worth marking this thread as solved (look under Thread Tools near the top), and letting other people know which Windows driver you used to get it to work.  This will help others....

---

### Post by ti3st0 on 2007-08-11
I used the Windows 2000 driver from this link:

[http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip)

It's number 24 under M on the NDISwrapper page with all the supported cards.

---

