---
title: "Net keeps resetting."
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by JudasReanimated on 2007-08-14
At random times net on this machine Ubuntu - Feisty Fawn will just stop working, and I'm forced to restart this computer to fix said issue. 

ISP is Comcast, and they said the problem is on my end (how reliable that info is is undetermined), but I still would like to know how this looks to you guys.

---

### Post by kevdog on 2007-08-14
You mean the computer just stops responding, or the internet connection is dropped.

When it is dropped can you ping a destination like your router or google.com??

Need more information about your card and driver

lspci -nn
lshw -C network

---

### Post by JudasReanimated on 2007-08-14
It's integrated, and the connection is cable, and the net just stops working. However when at wor on the same type of connect just different ISP, it works fine.

Though they say the modem is fine.

Know any commands I could use in case this happens again? Similar to ipconfig

---

### Post by kevdog on 2007-08-14
This isnt going to tell me whats wrong with your system however whenever the connection drops what happens when you type:

sudo /etc/init.d/networking restart

Also the equivalent of ipconfig is ifconfig

---

### Post by JudasReanimated on 2007-08-14
Basically I don't have the PC with me anymore, what I found odd is that it did work at home, but it did at work. I no longer have the PC though, but thanks for the ipconfig equivalent.

---

