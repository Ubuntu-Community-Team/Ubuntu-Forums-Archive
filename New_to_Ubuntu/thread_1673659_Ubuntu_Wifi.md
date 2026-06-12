---
title: "Ubuntu Wifi"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Iamred on 2011-01-22
Hello! I am a n00b at Ubuntu. I can't connect to my WiFi. I click the three bars up top and the Wireless connection thing, well, you can't click it.

Help would be appreciated.

---

### Post by MisterLambda on 2011-01-22
Anyways, snooping around with him on IRC, he says he's used both mouse buttons. Just someting to avoid asking.

He also as an Intel card.

---

### Post by Luci4n0 on 2011-01-22
try restarting the wireless application..

Hold Alt key + F2 .. you will get a startup interface .. type nm-applet then ok .. left click on the bars now .. and see if you can select your modem/router.

---

### Post by TBABill on 2011-01-22
Ok, can you open a terminal (click applications, then accessories, then terminal) and type in ```
sudo lshw -C network
``` and ```
lspci
``` and paste the output of those back here so we can provide you some assistance getting it going. We need to know some info about the device (wireless device) so we can give you the right guidance.

Edit: And please respond with which version of Ubuntu you are using (9.10, 10.04, 10.10, etc) and if you were prompted to install any drivers when you installed the software. Also, can you connect via ethernet cord to a router or modem?

---

