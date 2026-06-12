---
title: "Need some help - Modem &gt; Wireless Router &gt; PC's"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-08-17
Hi there, I hope someone can help me out.

I know how to configure ports, I know how to connect my PC's etc. I just can't seem, to make uTorrent work with open ports.

Here's how my home is set up.

A line comes from somewhere outside and I connect that telephone line to my Modem (a ZTE), from there, I connect a LAN cable from the ZTE Modem to my Wireless WTG routers, and from there I connect any PC I need to have internet wireslessly.

ZTE Modem IP:       192.168.1.1
Wireless Router IP: 192.168.0.1
My computers IP:    192.168.0.3

Set up:
Modem > Wireless Router > every other PC

No need for much explaining, I just want to know what port to forward where. I know how to configure etc.

Thank you very much for all the help. :guitar:

---

### Post by mikewhatever on 2009-08-17
> **papuccino1 said:**
> ...

No need for much explaining, I just want to know what port to forward where. I know how to configure etc.



What port? The port uTorrent uses for incoming connections.

Where? The router.

---

### Post by kambrik on 2009-08-17
It depends on the Torrent port that the application is using...  If your using something like uTorrent then its randomized everytime it starts.  So I would three things:

1) Updated your WRT54G to the latest firmware or DD-WRT or [Tomato]("http://thecomputergroup.net/how-to-install-tomato-v125-on-wrt54g-v2")

2) Verify that UPNP is enabled in the router

3) look in your torrent application to see what the port it uses

---

