---
title: "How can I disable my laptop's internal wireless adapter?"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by malisjw19 on 2014-03-20
It's an Acer Aspire 3050 laptop which has an adapter not supported by Linux. I have 5 USB adapters (Varying brands that have worked on other Linux systems) all of which seem to half-work when I use Linux on the laptop. By half-work I mean that it will connect for a minute, load pages really slow, disconnect, and just continue to have problems. I have tried several different distributions and the only one that I have got to work steadily is PC Linux OS, but for other reasons, I don't love that one. I'm pretty sure the two adapters are conflicting with each other.
I would like either Ubuntu, Mint, or OpenSuse. Is there an easy way to disable the internal adapter so it won't conflict?  If that's not the problem, then what is? This laptop is a gift for family member and I would like to get Linux working well before giving it to them. (I would simply leave Windows on it, but I bought it off Craigslist with a non-activated fresh install and I don't have the product key)

Thank you for any assistance you can provide.

---

### Post by chili555 on 2014-03-20
The strict answer to your question is to determine what the driver is from the terminal:```
sudo lshw -C network
```It will report something like:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: xx:94:6b:99:55:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=iwlwifi[/COLOR] driverversion=3.11.0-18-generic firmware=9.221.4.1 build 25532 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:f2400000-f2401fffThen blacklist what you found:```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Of course, substitute your details here. Reboot and you'll be all set.

The real answer is to troubleshoot the internal device and see if we can fix it. If you'd like to do so, tell us the information you found from above.

---

### Post by kostkon on 2014-03-21
If your laptop has a wifi button you can use that to disable (hard block) it. Or you could try to soft block it, by doing the following:
```
rfkill list
```
to find the index of the card and then
```
rfkill block index_number
```
e.g.
```
rfkill block 0
```
although I'm not sure if the block will stay between reboots.

Hope that helps.

---

### Post by mansonfan78 on 2014-03-21
Have you checked the bios settings?  There may be a way to disable it in there.

---

