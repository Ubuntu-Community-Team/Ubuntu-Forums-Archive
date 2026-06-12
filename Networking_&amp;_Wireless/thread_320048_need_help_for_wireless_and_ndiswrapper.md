---
title: "need help for wireless and ndiswrapper"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by poppo on 2006-12-16
Hello, I'm new to Linux, I installed Ubuntu 6.10 AMD64 and I can't get the wireless connection to work.

The kernel is 2.6.17-10.

In Network Administration the wireless card does not show at all.
Note: on another disk on the same PC there's WindowsXP and the wi-fi works perfectly.

Anyway I found the following:

1) Using lshw I see:
--------------------------------------------------------------
*-network:0 UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: c
bus info: pci@00:0c.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
resources: iomemory:fae00000-fae0ffff iomemory:fad00000-fad0ffff irq:10
--------------------------------------------------------------

2) with 'lspci |grep 00:0c.0' I get :
00:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

2b) I don't remember how I found it, but I found that the the pccid is 11ab:1faa (rev 03)

3) My wi-fi card is a low-cost Skintek card. The card is not listed in the ndiswrapper list page, but there's some others in the list which apparently are using the same chipset. 
Note: I'm not sure which driver is best - the one given with my card's CD, or the ones used by other cards with same chipset listed on ndiswrapper page ? Anyway I tried one of them with same (negative) results.

4) with 'iwconfig' I see :

lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.


5) With 'sudo ndiswrapper -i ~/Desktop/mrv8000c.inf' I see :

Installing mrv8000c
Forcing parameter AdhocGMode|1 to AdhocGMode|0
Forcing parameter AdhocGMode|1 to AdhocGMode|0

And then with 'ndiswrapper -l' :

Installed drivers:
mrv8000c driver installed, hardware present 

Note: the help page says it should be "driver present, hardware present".

6) 'sudo depmod -a' takes about 2-3 seconds and does not print anything

7) 'sudo modprobe ndiswrapper' returns instantly and does not print anything

After all of this, in Network Administration the wireless card still does not show.
Nothing is appended to the system log.

My main concerns are :

a) not sure which driver is best (see 3 above)
b) I feel I am missing something else other than the driver to activate the wireless card!:confused: 
c) once the wireless card works with Ubuntu, will there be any chance to let it work with WEP? (If not, I will change my wireless network setting to WAP)

Thanx a lot to all who can help me.

---

### Post by spd106 on 2006-12-16
When you ran ndiswrapper -i in step 5, did the working directory have both the .inf and .sys driver files in it?

Also, you might want to check that ndiswrapper was loaded by running **lsmod | grep ndis** at a terminal.

---

### Post by poppo on 2006-12-16
yes I have both .inf and .sys files

lsmod|grep ndis returns two lines:
ndiswrapper             284824  0
usbcore                   167840  4 ndiswrapper,ehci_hcd,uhci_hcd

---

