---
title: "[SOLVED] Enabling Wireless"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Virgofenix on 2008-05-09
This is my laptop: [http://h10010.www1.hp.com/wwpc/ph/en/ho/WF06b/1090709-1116637-1123071-1123071-1123071-80598788-81709298.html](http://h10010.www1.hp.com/wwpc/ph/en/ho/WF06b/1090709-1116637-1123071-1123071-1123071-80598788-81709298.html)

Manufacturer's website for the wireless drivers: [http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)

How does one connect to a wireless network using Ubuntu? 

No wireless networks appear in Network Settings. I've read a little about ndiswrapper, and have installed the ndiswrapper package in the repository. When it says, "Currently Installed Windows Drivers", is my taking correct when I say it acts like WINE, as a layer for "translating" Windows drivers? My wireless' manufacturer's website has both Windows and Linux drivers. I downloaded and looked at the Linux drivers, no .deb, though there's an .rpm(idk if Ubuntu supports .rpm packages), and there's source. I'm fine with the installation, but getting it out seems messy, so should I use the Windows drivers with ndiswrapper?

---

### Post by john6six on 2008-05-09
Have a look at Alien. That will allow you to convert the rpm to a deb.

sudo apt-get install alien

---

### Post by Virgofenix on 2008-05-09
Thanks for alien, though I won't be using it. Downloaded the XP drivers and installed using ndiswrapper. That *was* quick.

ndiswrapper says the hardware is present. I still don't know how to find and detect wifi wireless networks though.

---

### Post by Virgofenix on 2008-05-11
iwconfig says:

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

lspci gives:

10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

As I've mentioned before, I successfully installed the Windows drivers via ndiswrapper(installed from the repos). ndiswrapper also says that the hardware is present.

---

### Post by kevdog on 2008-05-11
Youve seen this ubuntu wiki page?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Virgofenix on 2008-05-11
^Worked perfectly. Thanks a lot.

---

