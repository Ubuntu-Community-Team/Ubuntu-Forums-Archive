---
title: "Qwest 2701HG-D wireless woes"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by XAsmodeanX on 2007-09-03
Hi all, I've been racking my brain for a while now trying to solve this problem.  I have a Qwest 2701HG-D dsl modem that has wireless b/g.  I can connect using any windows machine, but if I boot that same machine into linux and try I absolutely cannot establish a connection.  I have 2 laptops that both dual boot.  Both connect in windows, neither connect in linux no matter what. 

The modem is set up to use dhcp for leasing out local address, wep is enabled, and is on channel 1.  MAC filtering is NOT enabled.  I have tried disabling wep on the modem and connecting to it as an open network.  Still a no-go.

For example when I do:
sudo iwconfig wlan0 essid The_Matrix key *********** && sudo dhclient wlan0

It just tries to acquire an address but never does and then times out.

---

### Post by sintacto on 2007-10-31
1 connect with cable
2 run the disk that came with the 2701hg-d
3 open "manual installation"  run program in there
4 dont click quest with windows click office/plus
5 have phone number and code 
6 wep key is on the modem till you change it
works with atheros card good
not so good with bcm43xx not there sometimes 
any help?

---

