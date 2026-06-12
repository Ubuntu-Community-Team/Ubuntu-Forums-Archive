---
title: "Help.. internet connection... ubuntu/linux virgin"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by majora1 on 2009-07-30
I recently installed ubuntu 9.04 next to windows vista.. dual boot. So far everything looks fine, but cannot get internet connections thru my d-link router, under Ubuntu.. If I disconnect router and wire straight to nic card I get connected, but not with router. under windows, all is fine, i did have to re-address router as it conflicted with the dsl modem address,, router is now 193.168.0.0
 
Read some forums and have tried:
configuring a wired, dynamic connection and a dsl dynamic connection... then
 
ifconfig ( with router) - shows eth0 connection at address 193.168.0.0 ( router address), but i cannot ping the router..
 
ifconfig ( no router ) - dsl0 conection with normal ip dynamic IP address and connectivity... and everything seems fine. but would rather use router than re-wire everytime..
 
system:
amd phenom quad 4, 6 gig mem, plenty of everything..
the router is a d-link ebr-2310, and states windows, mac and linux friendly.
sorry, forgot to add, this is NOT a wireless set-up,, it is hard-wired.. thnx..
 
thanks alot for any help,,, majora1..

---

### Post by wojox on 2009-07-30
This may help you narrow it down:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by majora1 on 2009-07-30
Thnx, but my set-up is hard-wired, not wireless,and it looks as tho those docs are for wi-fi, unless i missed something..
but thnxs for the info, will probably be going wi-fi soon

---

### Post by mapes12 on 2009-07-31
> ifconfig ( with router) - shows eth0 connection at address 193.168.0.0 ( router address), but i cannot ping the router..Just a thought but shouldn't that be 192.168.0.0

Private class C network address range starts at 192. Here's the wiki: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

### Post by majora1 on 2009-07-31
thnx 4 the reply..
yes, normally 192... BUT there was a conflict between my dsl modem (192.168.0.0) and my router (192.168.0.0), so one of them had to change, so i re-addressed my router.. it works fine under windows, just had to change default from 192 to 193 then fine.
I also forgot to add that with router attached, under Ubuntu, my WIRED connection icon flashes and says connected, yet can do nothing..
i appreciate your response and thnx..

---

### Post by vruum on 2009-07-31
Just a few ideas. 
instead of 193.168.0.0, try setting the internal address of the dlink to 192.168.1.0 and the dhcp pool to start 192.168.1.1
also, do you know if your dsl-modem does routing to? My guess is that it does and you could try setting the dlink in bridge mode and let the dsl modem do the routing

---

### Post by majora1 on 2009-08-04
Thanks for the suggestions. I took them as for as my knowledge allows, very litle, and re-addressed the router,, nothing.. as far as having the router act as a bridge, etc. i don't know how to do that.. but thanks,, i'll keep diddling and see if i can stumble onto something.. i just don't see how just the addition of a router presents such a strange problem.. thnx for all and everything..

---

### Post by majora1 on 2009-08-06
tried something new that worked,,, kind of.. i let everything wired up the way it was..  modem = 192.168.0.1,, and router at  193.168.0.0.. that never worked. so what I did was re-address the router back to 192.168.0.1 and it works ok, but as stated earlier this conflicts with the modems addressing,, both being the same... and it worked.. i would really like to re-address one of them as I am getting conflicks, knocks offs, resets,, etc.. is there a default in ubuntu i can set to 193.168.0.0 and get it to talk to the router. Thnx for any help,,, majora1..

---

### Post by pedro3005 on 2009-08-06
I'm not sure, but maybe this is what you look for: run 'ifconfig eth0 ipaddres' so it will change eth0 to such ipaddress. IDK if it will work, worth a try.

---

### Post by cgb on 2009-08-06
The Routers address should never be at 193.168.0.0 (the last number should never be a 0).  You can set the address to 192.168.1.1 and this would put the router in a different subnet then the modem to prevent conflicts.

---

### Post by mapes12 on 2009-08-06
I think your problem is going from class C 192 private address to none standard 193.Can you reconfigure the other end of the address e.g. 192.168.0.2 i.e. the right hand side cos the left hand side may be pre configured somewhere in your modem/router/whatever.

---

### Post by sam007 on 2009-08-06
I recently got my hands over Ubuntu 7.x/8.04/8.10/9.04. i have Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01). i am working on leased line connection. every was allright when i switched to Ubuntu 7.x/8.04.When i migrated to latest versions, i have to restart my system once to get going on internet.
2. when i leave the system using screensaver, the hangs.Please help.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
sameer

---

### Post by mikechant on 2009-08-07
sam007, you should post a new thread rather than tagging onto an existing one.

---

