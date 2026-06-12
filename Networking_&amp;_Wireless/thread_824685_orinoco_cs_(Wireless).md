---
title: "orinoco_cs (Wireless)"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by fazavon on 2008-06-10
I am at a loss and think I need some help.

Using Ubuntu 8.04 

I have a Buffalo pcmcia Card The card is (WLI-PCM-L11G)

Ubuntu installs the orinoco_cs driver

lspcmcia:
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:01.0)
Socket 0 Device 0:      [orinoco_cs]            (bus ID: 0.0)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:01.1)
Socket 1 Device 0:      [-- no driver --]       (bus ID: 1.0)

pccardctl ident:
Socket 0:
  product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
Socket 1:
  product info: "O2Micro", "SmartCardBus Reader", "V1.0", ""
  manfid: 0xffff, 0x0001

Now I can connect to wide open Wireless (starbucks, Barns and Nobles, etc) but I cannot connect to WEP or WPA. I have been fighting with this thing for days.. 

I do have a proxim (Orinoco 11b/g gold atheros chipset) that worked until the last kernel update.. 2.6.24-16 to 2.6.24-18

I tried to roll back to the 24-16 and the proxim card still will not work in my Dell Lattitude D600. 

I do have a second Laptop but it was not cheap and do not like to travel with it just in case.. both cards work in it.

I just need it to work on the Dell

Any help would be great (ready to throw laptop and pull out all of my hair)

thanks

//j

---

### Post by fazavon on 2008-06-10
bump

---

### Post by chili555 on 2008-06-10
Is the hostap suite installed and loading?```
lsmod | grep host
```Can you connect to WEP networks manually, suggesting it's not s driver problem, but a Network Manager problem?```
sudo iwconfig eth1 essid <ur_lil_router>
sudo iwconfig eth1 key <ur_10 or 26 character_key>
sudo dhclient eth1
```# 40-or 64-bit ASCII WEP code has 5 characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters

If your key is ASCII, precede it with **s:**, like this:```
sudo iwconfig eth1 key s:<ur_5 or 13 character_ascii_key>
```Do you have *wpasupplicant* installed?

---

### Post by alSee on 2008-08-23
You need to replace orinoco_cs module with wlags49-h1-cs one as described [here]("http://ubuntuforums.org/showpost.php?p=5148420&postcount=107")

---

