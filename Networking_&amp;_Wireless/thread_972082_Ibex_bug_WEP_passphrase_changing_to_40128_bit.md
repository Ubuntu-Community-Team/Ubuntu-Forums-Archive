---
title: "Ibex bug? WEP passphrase changing to 40/128 bit"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by natehall on 2008-11-05
Did a fresh install if Ibex a few days ago (64 bit version for my Dell 1420 )  
It was working fine for a few days but now whenever I try and enter my wep 128-bit passphrase  it keeps changing the key to a 40/128 bit key. I have even tried to use ifconfig in the terminal to get the proper key remembered but it just keeps converting the passcode.

---

### Post by natehall on 2008-11-13
Well its been a week and nobody knows anything yet I guess. I'm on a wireless network right now where I put the 128 bit code directly and it works fine. However any time I put in a passphrase it converts it to a code which then does not work. The workaround I've come up with is to store that big old code as a text file which I then load when the wep password is asked. Would be nice to be able to use a simple password like previous versions of Ubuntu allowed.

---

### Post by stashluk on 2008-12-18
I'm having a similar problem.  Intel PRO/Wireless 2200.  I've installed linux-firmware and reloaded ipw2200 after reading this thread.  I can only connect to my (Netgear) router if encryption is off.

[http://ubuntuforums.org/showthread.php?t=967323](http://ubuntuforums.org/showthread.php?t=967323)

---

### Post by natehall on 2008-12-19
Got it running. I dumped all the configurations of the wireless files then entered in this:

sudo iwconfig wlan0 essid mynetwork key on key s:the_key

you can find your wireless identifier (in my case wlan0) by typing in iwconfig all by itself. The s: is used to write your key in alpha characters rather than hex. My system is WEP

---

