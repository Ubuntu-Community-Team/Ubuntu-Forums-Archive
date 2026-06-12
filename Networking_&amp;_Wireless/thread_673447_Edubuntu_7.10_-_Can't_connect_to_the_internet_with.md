---
title: "Edubuntu 7.10 - Can't connect to the internet with wireless"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by TucsonTarheel on 2008-01-20
I've set up Edubuntu 7.10 on my step-kid's PC (dual boot Vista/Edubuntu).    I can see my wireless network and have tried to set it up like I have my Ubuntu 7.10 installation on my PC (which works).

I'm using a Dell Inspiron 5315, with a D-Link WDA-2320 wireless adapter (I have the same card in the working PC), and connecting to a 2Wire 2700HG-D.  I'm using WEP-OPEN.

Can anyone help?

My /etc/network/interfaces looks like this:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-key s:<my wireless key>
wireless-essid:<my network name>


---

### Post by Greg Mueller on 2008-01-20
This sounds really stupid, but it worked for me.
Right Click on the two monitors icon in the task bar.
Uncheck "Enable Wireless" then recheck it. Mine started working after I did that

---

### Post by TucsonTarheel on 2008-01-22
Thanks for the reply, but I have it figured out.   I was easy to connect from NetworkManager once I realized I needed to specify that I had a WEP-Hex key.    My key is all digits and I kept trying to input it as a WEP-ASCII key.

---

### Post by asysin2leads on 2008-02-12
I have tried to uncheck/recheck the "Enable Wireless" a couple of times.  I can see the networks fine, but they will never connect.  I have WEP 128bit Hex enabled and entered the correct key and it still won't connect.  I want to tinker around with Edubuntu before I install it as a stand alone OS on my kids' laptop.  Any other thoughts on this?  Thanks

Kevin

---

