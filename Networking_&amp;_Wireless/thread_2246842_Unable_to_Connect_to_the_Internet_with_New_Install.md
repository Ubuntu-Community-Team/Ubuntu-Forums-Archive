---
title: "Unable to Connect to the Internet with New Installation"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by Jorge_Calderon on 2014-10-03
I just installed the 32bit version on my Windows host machine running Windows 7 x64.  I'm connected to the internet through Wifi and it works fine on my host machine.  In the VM under Network, I have the the "Attached to" set to "NAT".  I'm on a Dell Latitutde E6510.  I went to Preferences-Additional Drivers and didn't see anything under tab Additional Drivers tab.  When I hover over the network icon it says "Adapter 1 (NAT) Network connected"

Here are some screenshots commands I ran (I wasn't able to copy the text of the screen out of the VM.  Guest additions couldn't be installed due to not being able to connect to the internet):
[http://imgur.com/ZyVv448](http://imgur.com/ZyVv448)
[http://imgur.com/EfK8kLZ](http://imgur.com/EfK8kLZ)
[http://imgur.com/vBNZ2Bp](http://imgur.com/vBNZ2Bp)

---

### Post by bashiergui on 2014-10-05
Don't use NAT Network. Use NAT or bridged.

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by Jorge_Calderon on 2014-10-06
Thanks.  I switched to "Bridged Adapter", and chose my connected wireless networking card.  For some reason those settings didn't work fo rme last time, but after restarting the computer today it worked.

---

### Post by Jorge_Calderon on 2014-10-07
While I can get to the internet with Bridged Adapter, I'm trying to reach resources on a VPN connected through the host machine and that doesn't work with Bridged.  In an old VM I had (Fedora), I used NAT and could reach those VPN resources, but I can't even get to the internet with NAT on this Lubuntu installation.

---

### Post by bashiergui on 2014-10-07
Right, bridged will go directly to your router and not go through the hosts's VPN unless you set up the VPN inside the VM.

Don't confuse "NAT Network" with "NAT". Use the latter. Refer to the link in my previous post for details.

---

### Post by Jorge_Calderon on 2014-10-07
I don't believe I mentioned that I was using NAT network.  I'm using NAT.  I'm still not able to connect with NAT.

---

### Post by bashiergui on 2014-10-07
Ah. I understand. Have a look at this link, it looks like I might have been wrong anyway. [http://askubuntu.com/questions/419327/how-can-i-make-virtualbox-guests-share-the-hosts-vpn-connection](http://askubuntu.com/questions/419327/how-can-i-make-virtualbox-guests-share-the-hosts-vpn-connection)

---

### Post by Jorge_Calderon on 2014-10-08
In that link the person used Bridged. I'm using NAT.

---

### Post by Jorge_Calderon on 2014-10-08
I was able to get it to connect after changing the DNS settings to be the same as what my host machine is currently using.  Is there a way to get this to work dynamically?

---

### Post by Jorge_Calderon on 2014-10-09
It turns out that NetworkManager was not updating /etc/resolv.conf with the nameservers.  
Commenting out dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf worked after rebooting.
From here (the first solution didn't work for me)[http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf](http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf)

---

### Post by bashiergui on 2014-10-10
Good to know!

Glad you figured it out.

---

