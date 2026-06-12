---
title: "Quick dwl-g122 question"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by ukatoton on 2007-05-03
I'm thinking of buying a DWL-G122 for use with my laptop. As it has a small HD, and I want to keep widnows, i like using the ubuntu live cds.

Does the dw-g122 work natively with the included packages on any live cds? I don't want to use NDISwrapper, and it'd be great if i did not require extra packages.

Does anyone have any experience in this matter?

---

### Post by chili555 on 2007-05-03
It depends on the version. Please check here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) 

Check on down the page for USB adapters.

---

### Post by ukatoton on 2007-05-03
>_< I meant to specify the B1 revision, and the list seems terribly out of date.

I've heard some posts stating it works out of the box on 7.04 whilst others way it doesn't. 

Is anyone able to clear this up?

---

### Post by brambles on 2007-05-05
Running 64bit Feisty here and while it seems to load fine out of the box I'm getting no signal at all. May be that 32bit works fine though

Cheers

Mark

Version C1 tho'

---

### Post by akbob on 2007-05-07
DWL-G122 D1 on Fiesty 32 bit.  Can't get to even register.

---

### Post by chili555 on 2007-05-07
Well, it seems even the B1 has two versions! Can you all post:```
sudo lshw -C network
```Thanks.

They can all be made to work, with varying amounts of work. I believe only the rt2500 B1 will work with only the packages on the installation disk, not the rt2570.

---

### Post by brambles on 2007-05-07
Relevant portion

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:19:5b:80:bb:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Not really a whole lot of info. Oh and this is on i386. Had to abandon 64bit cos _really_ need wireless. Currently in Bogota!

However still no joy with g122 - loads fine but no dice at getting a signal. Thankfully have other card working.

---

