---
title: "wifi connected but no internet"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by bison12345 on 2007-11-28
Hi


I just configured wifi and  when i select a connection it connects but i cant go on the interent or even ping.Whats wrong?

---

### Post by mouseboyx on 2007-11-28
Are you sure the wifi is working and what is the name or chip set series of your wifi card?

Did you select a network from the dropdown menu?

---

### Post by bison12345 on 2007-11-28
> **mouseboyx said:**
> Are you sure the wifi is working and what is the name or chip set series of your wifi card?

Did you select a network from the dropdown menu?


I am pretty sure that the wifi is working. I think that this is the name of the card is netgear 54 MBPS WIRELESS USB 2.0 ADAPTER WG111 .  One thing that i noticed is that i selected eth1 (appered as wirelss) and this wifi adapter worked. Whenever i select the wifi adapter  it doesnt even show a bar. 

Yes i did have to select a network from the dropdown menu



things about my connection : Non encrypted wifi (dectable)


Thanks

---

### Post by mouseboyx on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=476735&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=476735&highlight=ndiswrapper)
or
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


should help you with this problem

The wireless card requires windows drivers that are wrapped.

---

### Post by bison12345 on 2007-11-28
Thank you. 

How do i install it (i know how to extract it)

---

### Post by rustybronco on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

go to applications>accessories>Terminal right click and add launcher to panel (after a while you will love having it there )
then cut and paste the commands in the terminal window... cut ctrl-c, paste shift-ctrl-v
There are many ways to skin the cat ndis is one of them.

---

