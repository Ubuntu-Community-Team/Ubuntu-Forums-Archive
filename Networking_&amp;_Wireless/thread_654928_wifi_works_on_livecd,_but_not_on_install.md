---
title: "wifi works on livecd, but not on install"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by jibbajabba on 2007-12-31
my apologies if this has been covered before, but ive searched through a ton of docs online today and i still cant make my wifi card work when i install buntu 7.10. i am using a linksys WPC11 pcmcia card (no version number, its really old). and as i said, it works and connects fine in the livecd but does not work when i install it to my HD.

Here is the info i get when i ran sudo lshw -C network  while in the livecd:

ubuntu@ubuntu:~$ sudo lshw -C network
   *-network               
        description: Network PC CARD
        product: Version 01.02
        vendor: Instant Wireless
        physical id: 0
        slot: Socket 1
        resources: irq:3
   *-network
        description: Wireless interface
        physical id: 1
        logical name: eth0
        serial: 00:04:5a:cd:66:86
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 0.8.3 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b

now when i do this in my full hard drive installation it looks like this:

*-network               
        description: Network PC CARD
        product: Version 01.02
        vendor: Instant Wireless
        physical id: 0
        slot: Socket 1
        resources: irq:3
   *-network
        description: Wireless interface
        physical id: 1
        logical name: wlan0 rename
        serial: 00:04:5a:cd:66:86
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=hostap driverversion=0.4.4.4-kernel firmware=0.8.3 multicast=yes wireless=IEEE 802.11b

it seems to me that the hard drive ubuntu install is loading up the hostap drivers instead of the orinoco drivers that worked in the livecd. so from what ive read online i tried to blacklist the other drivers by running gksudo gedit /etc/modprobe.d/blacklist and i added the following and the end of the page

blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

when i restart the laptop, i reran sudo lshw -C network and it has not changed. im totally lost now. ive spent quite a bit of time on this already and i just cant seem to get it working. what i think i need to do is stop the hostap driver from loading and get the orinoco driver working, but i need help in doing that. any ideas on what i am doing wrong? any and all help will be greatly appreciated. TIA!

---

### Post by jibbajabba on 2008-01-06
bump. any ideas? thanks again.

---

