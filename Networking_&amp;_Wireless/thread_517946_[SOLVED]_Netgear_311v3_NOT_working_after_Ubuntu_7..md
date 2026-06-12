---
title: "[SOLVED] Netgear 311v3 NOT working after Ubuntu 7.04 Update"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by ashishgoel on 2007-08-05
hi all,
I'm havin a very strange problem. After freshly installing Fiesta Fawn (without any update) i was able to use my netgear 311v3 with the help of Ndisgtk - there after installing the driver - the light on the wireless card light up and was able to connect it thru System->Administration->Network, even though the Ndisgtk showed that there is no device present.

After the update and restart, the Network option stop showing the Wireless Network, the Ndisgtk utility continued showing the same, i.e. No Device for the istalled Driver.  I tried to un-install the driver - but unable to do so.
I Removed the Ndisgtk, and again install it - but the driver was automatically installed... Then I tried using ndiswrapper from terminal - installing etc -  not able to help...

'sudo lshw' gives -
 *-network:0 UNCLAIMED
                description: Ethernet controller
                product: 88w8335 [Libertas] 802.11b/g Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: 1
                bus info: pci@01:01.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32
                resources: iomemory:fe5d0000-fe5dffff iomemory:fe5c0000-fe5cffff irq:5

'lspci -v | grep Ethernet' give-
01:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

'iwconfig' gives -
lo        no wireless extensions.

eth0      no wireless extensions.


PLease help me...  I even tried installing Ubuntu again, got the same problem after update and restart... 

Thanx
Ashish

---

### Post by ashishgoel on 2007-08-07
any help??

---

### Post by ashishgoel on 2007-08-07
Problem Solved...

How did i  - Re-Intalled Ubuntu and updated first ; then loaded latest 1.47 version ndiswarapper from terminal - and followed [http://ubuntuforums.org/showthread.php?t=518021&highlight=ndiswrapper_svn](http://ubuntuforums.org/showthread.php?t=518021&highlight=ndiswrapper_svn)

---

