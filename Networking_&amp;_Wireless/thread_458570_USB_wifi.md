---
title: "USB wifi"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by ivesjd on 2007-05-29
I recived an Ashton Digital USB wifi dongle. I first got it working in windows to make sure it worked at all. Then it was to linux. After some research I discovered that it had been set-up using ndiswrapper. So I installed ndis wrapper, and then the drivers. After a few frusterating hours it finally seemed like I had gotten it. Network Manager says that wireless is enabled. I can click the connect button and type in the network, but it just says "wireless network connection to 'XXXX' (0%)". My laptop is right next to it with a 70-80% connection (with ubunutu). I would just use a network cable but the router is on the other side of a block wall (i think) and I dont have access to it (university houseing). Any help would be greatly appreciated.
Need anymore info? Just ask.

lsusb =
Bus 001 Device 006: ID 124a:4017 AirVast PC-Chips 802.11b Adapter

lshw =
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: wlan0
capabilites: ethernet physical
configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes

ndiswrapper -l =
avwlpnic : driver installed 
device (124A:4017) present (alternate driver: prism2_usb)

iwconfig =
wlan0 no wireless extensions
__________________

---

### Post by ivesjd on 2007-05-30
bump :)

---

### Post by ivesjd on 2007-05-31
bump

---

### Post by alsantos on 2007-06-06
Hi!

I have the same USB WiFi card, but I can't make it work!!! My card works fine with Windows XP, so it's not my card's fault.

I used a SysInfo software to identify my drivers, and it identified that the files used by my card were "oem34.inf" and "UWLANUSB.sys". I copied it into a directory, ran "ndiswrapper -i oem34.inf", "ndiswrapper -l" (appeared "driver present,hardware present"), "depmode -a" and "modprobe ndiswrapper".
My network still doesn't work...

Could you help me?

Thanks in advance!

---

### Post by ivesjd on 2007-06-09
I have given up for now as it is not my primary computer. I believe it uses the prisim2 usb drivers although Im not sure. Hope that helps though.

---

### Post by alsantos on 2007-06-09
Just to thank you! I enabled the prims2_usb module, edited the /etc/network/interfaces file and configured the wlan0 interface there. I just couldn't enable the WEP encryption, but the card is working without it.

Here are the natwork cards that works with the prims2_usb module activated:

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb")

Bye bye!
  Alexandre

---

### Post by ivesjd on 2007-06-09
Could you elaborate on how you got it to work? I just tried what you had said youd done, all to no avail. Thanks:)

---

### Post by alsantos on 2007-06-14
I don't remember exactly what I've done, but I'm upgrading my system do 7.04. As I'm reformatting my HD, I'll have to install my wireless USB card again. Then I'll note my steps and put it here as soon as I get it done, ok?

Regards!

---

### Post by alsantos on 2007-06-15
> **ivesjd said:**
> Could you elaborate on how you got it to work? I just tried what you had said youd done, all to no avail. Thanks:)

I got it! I was watching [this thread]("http://ubuntuforums.org/showthread.php?t=4041") and I found a step-by-step way to activate my USB card.

Go there and try az's solution. It worked for me!!

I'll try to install Beryl now... then my desktop will be on fire! :)

Good luck!

---

