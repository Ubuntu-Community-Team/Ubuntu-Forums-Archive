---
title: "No Wireless option in Network manager"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by ivaylo.tanev on 2014-01-15
Hi all. I installed some updates earlier today and since then the option of wireless connection dissapeared from the network manager. I have only "Enable Networking" and I am struggling to get the wifi working. I tried several different options from other threads but I just cant get it to work. 


> 0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)



thank you!

---

### Post by Bucky Ball on 2014-01-15
Welcome. There is a solution at the bottom of post #1 here:

[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)

... or read post #4 here for another approach:

[http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)

Did you install the driver for this card manually or from a PPA and was there a kernel update in the updates you got recently?

---

### Post by ivaylo.tanev on 2014-01-15
There were 618 updates and I was inconsiderate enough not to check all of them. I dont know how to access the list now. I will check the postst and report back on the result. I couldnt find the right driver I think because the one I installed did not work.

---

### Post by Bucky Ball on 2014-01-15
Did you follow my links? There's two solutions there.

---

### Post by ivaylo.tanev on 2014-01-15
[http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930) POST 4 this one worked. Thank you so much.

---

### Post by Bucky Ball on 2014-01-15
Good news. Enjoy! ;)

---

