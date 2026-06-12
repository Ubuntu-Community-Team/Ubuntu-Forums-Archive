---
title: "no wireless connection to wpa in ubuntu 7.10"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by mohtasham1983 on 2007-11-07
HI, 
several months ago I configured my friend's wireless connection for edgy so that he could connect to a wpa wireless network. Yesterday he upgraded to the new version of ubuntu and called me that his internet is not working.

I set up his connection by following some thread that I cannot find now. According to that thread I had to disable network manager and edit networks/interface file manually. I checked networks/interfaces and noticed that everything remained the same. 

I can see all available networks using iwconfig ra0 scan, but I m not able to connect to the network that is encrypted by wpa. I m pretty sure that my network configuration file is fine, because it used to work before, but I think this time something is missing that doesn't let me connect.

when I issue ifup sa0 , it fails and cannot bring up the interface.

Any idea what I'm missing here?

---

### Post by balak on 2007-11-07
I am guessing here, but your friend probably had one of the Ralink RT wireless cards.

can you post the output of 

```
lsmod | grep rt 
```

If it says rt61 or rt2500 or rt73 or rt2x00 you have one of the RT wireless cards.
The interface name has changed to 'wlan0' 

You may want to try connecting in networkmanager first. It has come a long way since edgy.

---

### Post by tvphil on 2007-11-07
I'm not sure what that warning means, but just from what you're describing, it sounds like you're missing some steps in the set up process. Did you enter the network key? (usually a string of 8+ numbers that you use like a password to your network).This should get you connected, if you haven't entered it already. Also, you should have entered the SSID (the network's name). If you have done this already, click twice on the network icon in the upper right hand corner and re-enter that information. Maybe it's as simple as a typo error. The problem isn't WPA not working with Ubuntu. I use the WPA2 standard (even higher encryption) with a D-Link wireless N router. Ubuntu found and configured it on the first try. If you haven't given your router a name and a key, you need to do that first.

---

### Post by mohtasham1983 on 2007-11-07
the wireless card is rt2500 and i changed the name from ra0 to wlan0 and eth1 but non of them worked.

The strange thing about it that in the connection configuration file it points driver to something called wext. i found out that wext has something to do with ndiswrapper and I just noticed that ndiswrapper utilities are not installed on his computers. I dont know how to install them, since there is no other way to connect to internet. 

I have disabled network manager based on that thread i read. Sorry i configured this connection for feisty, not edgy.

---

### Post by tvphil on 2007-11-07
To install ndis utilities, just do the following. At the top left of your screen, go to system, then administration, then synaptic package manager. Navigate alphabetically to ndiswrapper utils 1.9.Highlight it and right click over it. Then choose "mark for installation" and then click "apply" at the top of the box.Then it will install. After it installs, re-enter your network's SSID and the network key. Hope it works, please post one way or the other.

---

### Post by mohtasham1983 on 2007-11-07
The main problem is that other than that wireless connection there s no other way to connect to internet from that computer. I'm going to download them from internet from my machine, and hopefully his computer meets all dependencies.

---

