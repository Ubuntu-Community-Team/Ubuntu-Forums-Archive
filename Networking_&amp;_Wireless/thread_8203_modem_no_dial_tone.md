---
title: "modem no dial tone"
date: 2004-12-15
forum: Networking &amp; Wireless
---

### Post by christooss on 2004-12-15
How can I desable this. I dont want modem to wait dial tone. I looked in howto but i could found nothing that would help me.  

Thanks

---

### Post by clparker on 2004-12-15
sorry buddy, i used to work as a dial up tech for earthlink for over a year, and 99% percent of the no dial tone problems were caused by bad setups, i.e. wrong cord in wrong jack, bad cable, etc. see, the computer is checking for a dial tone, and not getting one, forcing it to dial will do squat if in reality there is no tone. check to see if this is a 'winmodem' as many, many modems are winmodems, they lack essentialy any non windows support. hate being the bearer of bad news, but you may be T.S.O.L.

---

### Post by az on 2004-12-15
If you configure your modem setup with pppconfig, remove the

ABORT    "NO DIALTONE" 

line in /etc/charscripts/provider
(using a connection named provider, of course.)

I am not sure how to do this with wvdial.

---

### Post by Nikola on 2004-12-15
For wvdial (in wvdial.conf):

Abort on No Dialtone = off

Or you can use gnome-ppp and in setup windows un-check "wait for dial tone".

---

### Post by christooss on 2004-12-25
The internet is working its all about X3.

In file /etc/provider

I had to change line ATDT+numbers in to ATX3DT+numbers

I hope it will help to some one

---

### Post by irlandes on 2005-01-03
Contrary to the naysayers, a significant percentage of winmodems do have available drivers.  not all but a lot.  Lucent, Conexant, and many more.

Definitely, an external modem is a valid choice for many users, specifically those who have computers in a fixed position. However, for those of us with laptops who travel a lot, it would be nuts to drag an external modem.

Google for your modem and linux.

Or check linmodems.org

---

### Post by andlinux21 on 2005-06-06
[FONT=Comic Sans MS][SIZE=3][COLOR=RoyalBlue]I hope that my laptop (Micron) doesnt have a winmodem I am going to try and configure it today using the info from the posts here and report back. \\:D/ [/COLOR][/SIZE][/FONT]

---

