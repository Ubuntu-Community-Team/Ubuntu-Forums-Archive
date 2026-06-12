---
title: "How Do I Setup A Vpn?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by erbag on 2008-05-05
I want to be able to set-up a vpn for my Ubuntu [7.10] box. What do I need to do?

---

### Post by hariprs on 2008-05-05
VPN within your home or between your different office location via Internet?

---

### Post by superprash2003 on 2008-05-06
hamachi is a good vpn tool

---

### Post by erbag on 2008-05-06
I work at home so I use Real VNC to connect to the box while at home but I also want my partner/associates to be able to access the box over the internet. Primarily when our job takes us out of town.


I look at hamachi but see no linux version.

---

### Post by ivze on 2008-05-06
Hamachi for linux Exists! Seen and used it. But, only for x86.
See [https://secure.logmein.com/products/hamachi/download.asp](https://secure.logmein.com/products/hamachi/download.asp).

---

### Post by superprash2003 on 2008-05-06
as ivze mentioned above hamachi for linux exists.
 another way around is to setup remote desktop in ubuntu(System->preferences->remote desktop) and enable it.THen you might have to open a port so that its accessible from the internet.(i think its either 3389 or 5900) then download a client like vncviewer.. and you should be able to connect to your computer by typing its ip address.. if its not a static ip then you could register with no-ip to get a free domain name

---

### Post by hariprs on 2008-05-06
Option 1) Real VPN:

VPN through internet is possible only if your operator supports it and enable it for you at your location. This is more secured way for your requirement and i guess it is less cost.

Option 2) Remote desktop/VNC:

This is possible only if you have a static IP. Less secured and cost is high.

---

### Post by Monicker on 2008-05-06
> **erbag said:**
> I work at home so I use Real VNC to connect to the box while at home but I also want my partner/associates to be able to access the box over the internet. Primarily when our job takes us out of town.


I look at hamachi but see no linux version.

OpenVPN is also something you could look into.  I run an openvpn server on my desktop, and can connect it from my laptop when away from home.

---

### Post by jvin248 on 2008-05-06
Moniker, how do you have your desktop set up - I assume you are using a dynamic IP address?

erbag, Hamachi works well and there is a linux version for it.  There is even a nice gui control panel (separate download) that makes it easier to link to. 

J

---

### Post by Monicker on 2008-05-06
Yes, I have a dynamic ip address.  I use dyndns, and just specify that hostname in the client side configuration.  Works fine.

---

### Post by Paris Heng on 2008-05-06
> **erbag said:**
> I want to be able to set-up a vpn for my Ubuntu [7.10] box. What do I need to do?

[Linux VPN How-To]("http://parisheng.110mb.com/download.html")

:guitar:

---

### Post by erbag on 2008-05-08
Yow this is crazy confusing ](*,)...I've used Real VNC, Tight VNC and Ultimate VNC to connect to the box locally and from Windows PC to Windows PC.

I used Hamachi & TeamViewer to connect from on PC to the next over the internet with ease. Why does it have to be so complicted with Linux? HELP?!?!?

I'm a novice...can you tell

---

