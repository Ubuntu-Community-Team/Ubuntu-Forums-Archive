---
title: "Setting Static Address"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2013-12-20
I am trying to set a static address for my Ubuntu machine.  I do an ifconfig, and it shows 192.168.1.2 as I had configured it.  I have the following setup in my /etc/network/interfaces:

```
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

I had restarted the wireless adapter and wlan0 connection.

When I try to ping it from another machine, it says that the reply from 192.168.1.11 is Destination host unreachable.

---

### Post by Iowan on 2013-12-20
Have you tried setting a static address from Network Manager?
(or a static lease via the router?)

---

### Post by sniper8752 on 2013-12-20
So I found in my router a place to add a NAT rule.  I selected the host computer name, and am not sure what to choose for the public IP address.  Am I in the right place? And then there is a WAN connection type.

---

### Post by chili555 on 2013-12-20
I suggest you set the address in Network Manager. Please see: [http://askubuntu.com/questions/381112/static-ip-network-guide](http://askubuntu.com/questions/381112/static-ip-network-guide)

---

### Post by PaulBx on 2013-12-22
Can you ping the gateway? Or ping your computer from it? Sometimes the router can be configured to disallow any client-to-client communication. Maybe yours is set up that way.

I wouldn't fool with NAT rules in the router. Seems like that is only relevant going out on the internet, and the default setup there is usually sufficient.

---

### Post by Bucky Ball on 2013-12-22
> **chili555 said:**
> I suggest you set the address in Network Manager. Please see: [http://askubuntu.com/questions/381112/static-ip-network-guide](http://askubuntu.com/questions/381112/static-ip-network-guide)

Yes, you are making this more complex than it needs to be. Setting up the static in Network Manager is easy. Just don't set one that is in the range your router may be trying to serve you via DHCP. In other words, limit the range of the router's DHCP server or switch it off.

Also:

> **sniper8752 said:**
> 
When I try to ping it from another machine, it says that the reply from 192.168.1.11 is Destination host unreachable.

192.168.1.11 probably is unreachable as you have 192.168.1.1 set. I'm presuming this is a typo. ;)

---

### Post by sniper8752 on 2013-12-22
I limited the range of DHCP.
And it is suppose to be .11.

---

### Post by chili555 on 2013-12-22
> Yes, you are making this more complex than it needs to be. Setting up the static in Network Manager is easy. Amen, my brutha!

If Network Manager is running on your system, setting up manual methods will be tricky to impossible. However, if you are running a server or you are hard-headed just like me, and completely remove NM, then this won't work:> iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1However, this probably will work:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

[COLOR="#FF0000"]auto wlan0[/COLOR]
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="#FF0000"]wpa-ssid <your_ssid>
wpa-psk <your_wpa_key>
dns-nameservers 8.8.8.8 192.168.1.1[/COLOR]
```

---

### Post by sniper8752 on 2013-12-22
I got it!  Phew, thanks for your help, Chili!  I was afraid I would never get it.  I was looking at the interfaces file, and I'm like, well, i commented out my router psk/ssid, and I'm wondering if that would be useful to talk with the router...  and it was!  that was the next thing that I was going to try.
Now for the dns nameservers, would you use the router-provided one, which is i think for me, 192.168.1.1, or use google's like you have provided?  are there any advantages/disadvantages to both?

---

### Post by chili555 on 2013-12-22
> **sniper8752 said:**
> I got it!  Phew, thanks for your help, Chili!  I was afraid I would never get it.  I was looking at the interfaces file, and I'm like, well, i commented out my router psk/ssid, and I'm wondering if that would be useful to talk with the router...  and it was!  that was the next thing that I was going to try.
Now for the dns nameservers, would you use the router-provided one, which is i think for me, 192.168.1.1, or use google's like you have provided?  are there any advantages/disadvantages to both?Awesome! Glad it's working.

As for DNS, I use the exact settings I posted. Without checking in your router's administration pages, it's impossible to know what is used there; probably whatever your ISP provides. 

I periodically check namebench and see which DNS nameservers are fastest.> DESCRIPTION
       namebench  searches the fastest DNS servers available for your computer
       to use. namebench runs a fair and thorough  benchmark  using  your  web
       browser  history,  tcpdump output, or standardized datasets in order to
       provide an individualized recommendation.Google's 8.8.8.8 is generally fastest for me at my location, so I specify it as the primary in my interfaces file. I have read some criticism of Google's alleged lack of privacy, world domination, etc., but I'm not too concerned.

---

### Post by sniper8752 on 2013-12-22
thanks, i'll look into it!

---

