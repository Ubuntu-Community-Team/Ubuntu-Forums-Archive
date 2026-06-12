---
title: "Broadcom wireless help"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Brewbart on 2007-04-18
I am trying to configure ubuntu 6.06 on my HP ze4400 laptop when i tryto find out what my network adapter is it replies with 
0000:00:09.0 Network controller:  Broadcom Corporation BCM4306 802.11b/g wireless lan contrller (rev 02).  

I searched to see if i could find any tutorials for this model and was only able to find revision 3 adapters.  I would greatly appreciate if someone could run me through the setup of my wireless card.  Thanks in advance.

---

### Post by Floppyjoe on 2007-04-18
Your best bet if you choose to use ndiswrapper is to go to the manufacturers website of your laptop (HP) and download the wireless drivers for your model of laptop.

I did not see any broadcom chipsets on the ndiswrapper list site with your revision number so I am not sure if it will work with ndiswrapper but my guess is it will.

I have a bcm4318 howto in my signature which you could follow substituting the drivers for your laptop wireless card from the manufacturers website.

If you choose not to use ndiswrapper then you could follow the wiki entry for bcm43xx:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

