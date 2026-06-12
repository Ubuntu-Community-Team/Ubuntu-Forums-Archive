---
title: "Using Wireless on an Ubuntu Server as a Bridge to get another server on the network."
date: 2010-07-18
forum: New to Ubuntu
---

### Post by kwikksilva on 2010-07-18
Hi Guys,
This is my first post :-)
I just setup a Dell 650 server running Ubuntu 10.4 LTS which is connected fine to my wireless network using a Philips SNU6500 Adapter running under ndiswrapper.

The 650 has 2 ethernet ports.

I also have a Sun Fire V210 Server running Solaris which has 4 ethernet ports.

Can you suggest any way in which i can get my Sun Fire on to the network using the SNU6500 adapter connection?

Can i bridge one of the ethernet ports on the 650 to the wireless and then plug the Sun Fire into that port?

The room that these servers are in is miles from any RJ45 socket so i'm trying to get the 2 of them online using any other way.

Any suggestions appreciated thanks!

Kwikk

---

### Post by marshmallow1304 on 2010-07-18
Do you have Desktop Edition or Server Edition on the Dell 650?

If you have the full desktop, it's very easy, just follow the short [GUI Method Using Network Manager]("https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20Using%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29").

If you have Server Edition (command-line only), follow the [Internet Gateway Method]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29").  Use
```
ifconfig
```
to check your network interfaces.  The guide uses eth0 as the internet connection and eth1 as the shared connection.  You'll probably use wlan0 as the internet and either eth0 or eth1 as the shared connection.

---

### Post by kwikksilva on 2010-07-19
Thanks for the reply dude! I will give it a go when i get home.

---

### Post by kwikksilva on 2010-07-19
Thanks Marshmallow - That was simple. I just had to do as it said in the instructions, enabled sharing on ETH0 and i plugged the Sun Fire into the ethernet port of the 650.

Thanks so much!

---

