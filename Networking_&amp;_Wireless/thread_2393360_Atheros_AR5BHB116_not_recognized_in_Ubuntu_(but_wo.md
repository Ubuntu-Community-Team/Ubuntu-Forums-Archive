---
title: "Atheros AR5BHB116 not recognized in Ubuntu (but working in Windows)"
date: 2018-06-02
forum: Networking &amp; Wireless
---

### Post by alex14522 on 2018-06-02
**Atheros** AR5BHB116 is not recognized in Ubuntu 18.04. The same setup is working without problems in Windows 10. I get the following messages:
```
lspci
```
```
03:00.0 Ethernet controller: Qualcomm Atheros Device abcd (rev 01)
```
I have read in this forum that this indicated that the card is not properly initialized by the BIOS. However, it works in Windows 10 without problems. Which changes should I make in BIOS to get it initalized?

```
sudo lshw -C network
``` gives
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:81200000-8121ffff memory:81220000-8122ffff

```

Full wireless-info.txt is here: [http://paste.ubuntu.com/p/Prrtcxqz9T/](http://paste.ubuntu.com/p/Prrtcxqz9T/)

I have also tried to manually load the driver with modprobe but this did not have any success:
```
sudo modprobe ath9k
```

Any idea that could help me to solve the problem? thank you

---

### Post by chili555 on 2018-06-02
I suggest that you fully update the BIOS. Please check here: [https://askubuntu.com/questions/1042215/wireless-ath9k-suddenly-stopped-working-on-ubuntu-16-04/1042326?noredirect=1#comment1699298_1042326](https://askubuntu.com/questions/1042215/wireless-ath9k-suddenly-stopped-working-on-ubuntu-16-04/1042326?noredirect=1#comment1699298_1042326)

---

### Post by alex14522 on 2018-06-02
Thank you for your supply. Unfortunately I have a no-name motherboard (BIOS is AMI V) where I don't have any updates available. Since WIFI is working with this BIOS in Windows without any problems, I was hoping to get it to work in Ubuntu too without the need for a BIOS update.

---

### Post by chili555 on 2018-06-02
> 
 I was hoping to get it to work in Ubuntu too without the need for a BIOS update.I am unaware of any surefire method to do so. I suggest that you try a few things.

First, since this is apparently a dual-boot system, experiment to see if the result is the same or improved if you reboot from Windows to Ubuntu. Try cold booting to Ubuntu. Try reseating the card in its PCI slot. Remove the CMOS battery, count to ten, reinsert it and cold boot to Ubuntu. After each test, run again:```
lspci -nnk | grep Atheros
```is the dreaded abcd present in each instance?

Aside from a BIOS update, I haven't any other suggestions.

---

