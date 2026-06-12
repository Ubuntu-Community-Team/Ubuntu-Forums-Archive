---
title: "Cannot connect to a wap"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-03-15
I am trying to connect to a WAP, I have tried everything, resetting the WAP, rebooting, everything, all unbuntu does is come up with the wireless bars and say cannot connect.

Please help.
 
EDIT: its on the eth0 side, because I can't even log into the WAP.

Mick

---

### Post by finku on 2010-03-15
Are you getting your ip address through a DHCP? or it static?

---

### Post by Mark Phelps on 2010-03-15
Is this WAP an access point to YOUR network? Or is this an access point to a public network?  I'm guessing the former.

Also, unless you're very foolish and want everyone within a block's readius stealing your bandwidth, I'm further guessing that you have some kind of security implemented on Wireless access -- WEP or some flavor of WPA.

If the WAP is secured, the only way you're going to be able to connect is know exactly what security sequence to provide it. If you don't have that written down somewhere, you will have to commect to the WAP via a wired connection, bring up your Wireless security panel, and find out what security sequence you need to enter.

IF you're saying you can't get in via wired connection, either you're not on the same subnet as the WAP, or your WAP also has wired access security implemented.

---

