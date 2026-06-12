---
title: "ADSL modem takes often a restart when downloading big files via WLAN"
date: 2014-08-16
forum: Networking &amp; Wireless
---

### Post by jjaakkol on 2014-08-16
Still hitting this "old issue" what I have seen with different Linux versions during my Linux years.

Mostly with Ubuntu based stuff. Fedora was pretty OK with this issue.

Now I have Lubuntu. (Ubuntu 14.04.1 LTS) **Has there been any clear solution to this?** Is there a debug guide for this?

I have experienced this with IBM t40, t60p, Acer Aspire. My modem Zyxel P-660HW-D1 has been same. Config of modem is psw protected. (My employer paids it).

My current wireless adaptor is Intel PRO/Wireless 3945ABG [Golan] in Lenovo t60p.

If wired connection is used no problem seen. Modem also works ok with Windows laptop, Android mobiles/ tabs, Windows phone and with Ipad.

---

### Post by coldraven on 2014-08-16
My first ADSL router/modem was a cheap second-hand 2wire, my current router/modem is a £50 Edimax and I've been using Ubuntu since 8.04. My wifi adaptor is a Broadcom B43XX 
I have not had any problems downloading big files. Could your problem just be a coincidence or do you get the same failure every time?

---

### Post by jjaakkol on 2014-08-16
I do not believe it is coincidence. It happens almost everytime for example when software update is downloaded. If file size is more than or around 2MB it can happen already. 
I start to take wireshark logs about it. And try to find some commands to collect data. 

There are others also having this kind of issue. I have googled this issue already couple of years. And now it finally started to be annoying... ;)

---

### Post by jjaakkol on 2014-09-27
Short update: 
I got new ADSL box. Restarts still happened with new rbox BUT now I am able to set my wireless hidden or not. I got the admin psw. ;) 
And it seems that when wireless is not hidden things are ok. "Testing" still ongoing but no ADSL restarts since four days. Eventually I will turn WLAN to hidden to see if restarts are back. :)

An other thing noticed when I got new ADSL router. Channel number was set to "auto". One Lubuntu laptop and my Windows phone did not connected to WLAN. When I set channel number for example to 12 it solved "the problem". This is easy to reproduce.

New ADSL box is Zyxel P-661HNU-F1.

---

