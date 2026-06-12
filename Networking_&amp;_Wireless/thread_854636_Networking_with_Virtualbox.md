---
title: "Networking with Virtualbox"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by Rimfrost on 2008-07-09
Hello!

Ok so this is my situation:
I have an Acer Aspire laptop on which I run 8.04 (32 bits). 
I have a wireless network where the router acts as DHCP server in the 192.168.1.xxx range. The wireless network works fine. To my network i also have a D-Link DNS-323 networked hard drive connected. It is assigned the IP 192.168.1.2.
On my laptop, I have installed Virtualbox on which I run Windows XP as guest OS. 
Now, to configure the DNS-323 I must use a Windows program which i run in virtualbox since i do not have a "real" windows installation. The problem is this: Virtualbox uses NAT, so the guest OS (XP) is not connected to my local network, and thus the configuration program does not find my network hard drive. 
I have read the manual for Virtualbox which talks about building a bridge, but when I tried that, my network connection got all messed up. I have also read that bridging is not possible with wireless cards because of something with MAC addresses. 

I think what I want is the guest OS to have another IP on my local network, different than the one used by the host OS. 
Is this possible with bridging, or have I misunderstood something? 

It seems to me that both the "real" interface, wlan0, and the bridge, br0, gets assigned the same IP by the DHCP. 

Any guidance appreciated!
Cheers,
Anders

---

### Post by superprash2003 on 2008-07-09
yes setting to bridged would give different ips to both.. you wouldnt get the same ip

---

### Post by Rimfrost on 2008-07-19
Ok, thats my intention. 
But it seems my wireless router, who works as DHCP server, uses the MAC adress of the assignee to give it a IP adress. 
So how should I setup so that the DHCP server sees a different MAC adress when asking on behalf of Virtualbox, even if it is in fact the same wireless card whom is asking?

---

### Post by markwyatt on 2008-08-03
I just got this working:
VirtualBox
Host: Windows XP - Wireless Internet
Guest: Ubuntu 8

I hope this helps

[IMG]http://s15242348.onlinehome-server.com/i/FCKeditor/userfiles/CLIENTPORTAL/WebSoft - internal/Image/virtualbox_networking.jpg[/IMG]

---

