---
title: "Problems configuring vpn"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Ivana on 2009-09-02
Yo :)

I'm a complete noob (to both computer and ubuntu) so please if you could help me.

I managed to install ubuntu 9.04 and it's the only OS on my laptop.
Problem is I can't connect to internet.
I have something that looks like a modem (I'm not exactly sure what it is, sorry) and I'm certain that it has to be conected with laptop by wire. I did that. But it couldn't connect to internet. I got some manual from ISP provider so I figured I had to configure VPN. It's step by step guide how to connect but only for windows. link [http://portal.bnet.hr/ST/windows-xp.htm](http://portal.bnet.hr/ST/windows-xp.htm)  (I know it's on croatian but I think that pictures help)
But even if I knew how to do that I don't know how to enable VPN in ubuntu (there is some lock near it and I can't press add) :confused:
I tried some advices found on this forum like typing something like
```

sudo apt-get install network-manager-pptp
```but I got some error saying it cannot be found or something (I figured it had to be downloaded from internet)
unfortunately there is no other way for me to connect to internet. I understand what WI FI is only in theory and have no clue how to connect to wireless network even if I found a hot spot. :(

I hope I've been detailed enough considering I don't have a clue what is going on.
Could you please help me establish a VPN connection like one in the manual. Thanks

---

### Post by XCan on 2009-09-02
I'm not expert in this matter, but if I understand you correctly you can't install the above package because your computer can't connect to the internet to begin with.

I think you should be able to manually download the package from [http://packages.ubuntu.com/jaunty/network-manager-pptp](http://packages.ubuntu.com/jaunty/network-manager-pptp) , copy it over to your laptop, and install it there. This should work, however, the package may, or may not, be dependent on some other files. But it will be apparent when you try to install it.

---

### Post by Ivana on 2009-09-02
Thanks!

Now I can configure VPN but after I write gateway, user name and password (I leave NT domain empty cause I don't know what to put there)
and disable CHAP MSCHAP MSCHAPv2 (I was instructed by cable company to uncheck it though they said they don't know how to deal with linux) still nothing happens.
I connect the cable, see my new connection but can't click it or get it working.

Any ideas?

---

### Post by Ivana on 2009-09-03
I learned I needed to configure routes in IPv4 tab.
but I have no idea how to do it.
In windows there are values

Ethernet adapter : IP address, subnet mask, gateway
PPP adapter: IP address, subnet mask, gateway

I believe it equals Address, Netmask, Gateway in routes
But which value should I put, PPP adapter values or ethernet adapter ones?
or some mix? And what is Metric and what value should I put?

I tried several combinations but nothing changed. I can still see my connection when I click on network connections (under VPN) but I can't activate it (it appears grey)

help?

---

