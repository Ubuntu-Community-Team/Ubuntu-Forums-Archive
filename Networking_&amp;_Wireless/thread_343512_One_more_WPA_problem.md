---
title: "One more WPA problem"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by mr4thjuly on 2007-01-21
Hi Guys,
  I am new to this forum and very new to Linux as well. So should you decide to answer my problem below please treat me as an absolute beginner i.e. post related commands and detailed how tos :). Assume I know how to create, move and navigate through my file system.

Ok so here goes:
I installed Ubuntu Edgy 6.10. Everything works great except my WPA. I can't connect to the internet due to this reason. The gnome network manager did not get installed either and neither did wpa_supplicant. So i can't do "sudo apt-get install" on anything since I cannot connect to the net. I think I might have to manually create some files in the right places I just don't know how and cannot find a place that will tell me where and how to do this step by step. I even tried downloading the wpa_supplicant but the link to the site seems broken. 

Here is the output of "lspci"

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
**00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)**
00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:0a.3 Mass storage controller: <pci_lookup_name: buffer too small>
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

Thanks to anyone who has a solution or part of the solution to my problem. Its great to be a part of the Ubuntu community.

---

### Post by spd106 on 2007-01-21
wpa_supplicant is installed by default on Edgy (6.10). Maybe have a look at this page [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by mr4thjuly on 2007-01-21
I finally re-installed Ubuntu 6.10 and wpa_supplicant got installed but there is not wpa_supplicant.conf file to edit.

---

### Post by mr4thjuly on 2007-01-21
I directly hooked up my laptop to my cable modem to be able to install network-manager-gnome. However I am unable to see that in the gnome panel. Nothing seems to be working for me :). The only file in the /etc/wpa_supplicant is the ifupdown.sh file. I don't have either a wpa_supplicant.conf or a wpasupplicant.conf file to edit. What do I do? More importantly how can I get my network-manager-gnome to show up. 

Thanks

---

