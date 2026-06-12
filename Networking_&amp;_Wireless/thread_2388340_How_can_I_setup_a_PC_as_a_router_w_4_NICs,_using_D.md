---
title: "How can I setup a PC as a router w 4 NICs, using DHCP?"
date: 2018-03-31
forum: Networking &amp; Wireless
---

### Post by sandman887 on 2018-03-31
Hey,

I'm using Debian Stretch for the router, so if that violates this specific board, please feel free to move it to the appropriate forum :)

I have a Dell Dimension 4400 from 2002 (seems like just a few years ago...:P ) that has been sitting sad and unused for a long time. But recently I decided to use it as a router. 

_**What I want to do**_
I want my router to automatically configure the hosts on all three NICs, like how most of our home routers work. I want the 3 NICs to all have their own subnets. I want all three subnets to be on the same network.

Right now, I'm just trying to get the subnets to work. I had been going off of [Linux Networking Cookbook]("https://smile.amazon.com/gp/product/0596102488/ref=oh_aui_search_detailpage?ie=UTF8&psc=1"), but it's a little confusing. She doesn't provide any complete config files to use for examples. She provides lines of code here and there between paragraphs, but it's difficult to know if it's meant for the # command line, or a config file, as well as which commands she gives can be used together.

I've spent three days on this, and I feel like it shouldn't have been this difficult to set up. Last night, I finally got to the point when I connected a couple laptops to two different NICs on my router. I was trying to set them up with static IPs manually on each laptop. My Acer netbook was able to ping eth3 at 172.16.3.1, but my Dell laptop wasn't able to ping eth2 at 172.16.2.1. It was late, so I called it a night.

Today, I decided to say screw it, I'll set it up to do it automatically. So then I installed isc-dhcp-server. But I'm still not able to get things working.

_**I have 4 ethernet NICs**_
eth0 is connected to an external network run by my Linksys router on network 192.168.1.0.
eth1 (172.16.1.1) will be the gateway for subnet 172.16.1.0
eth2 (172.16.2.1) will be the gateway for subnet 172.16.2.0
eth3 (172.16.3.1) will be the gateway for subnet 172.16.3.0

[HTML]ifconfig -a[/HTML] confirms that each NIC has the correct IP address.

I also uncommented [HTML]net.ipv4.ip_forward=1[/HTML] in /etc/sysctl.conf to turn on IP forwarding.

By going off of the book, and trying to guess at what could be functional configurations, I arrived at this. I haven't changed it since last night (before I installed the DHCP server):
```
# eth0          NIC connected to external network
auto eth0 eth1 eth2 eth3
allow-hotplug eth0
iface eth0 inet dhcp
   netmask 255.255.255.0
   network 192.168.1.0
   broadcast 192.168.1.255
   route add default gw 192.168.1.1

# eth1
allow-hotplug eth1
iface eth1 inet static
   address 172.16.1.1
   netmask 255.255.255.0
   network 172.16.1.0
   broadcast 172.16.1.255
   gateway 172.16.1.1

# eth2
allow-hotplug eth2
iface eth2 inet static
   address 172.16.2.1
   netmask 255.255.255.0
   network 172.16.2.0
   broadcast 172.16.2.255
   gateway 172.16.2.1

# eth3
allow-hotplug eth3
iface eth3 inet static
   address 172.16.3.1
   netmask 255.255.255.0
   network 172.16.3.0
   broadcast 172.16.3.255
   gateway 172.16.3.1


# The loopback network interface
auto lo
iface lo inet loopback


```

Should each NIC be the gateway for that subnet? Or would the only gateway be the NIC that's connected to my Linksys router?

I have seen many different posts on the internet, but of course, everyone's situation is different, with many different distros existing, so I don't know which parts of which examples would work or not. This is my first attempt ever at doing anything like this, and I feel like I've learned a lot already, but apparently I need help setting up even a simple router ](*,)

If the networking wizards here can help, I would be very thankful!

Edit: Well that's typical lol, I spend several days on something, can't get it, pull my hair out, then ask for help, then shortly after I ask for help, I solve my problem! :D It seems that's always how it goes. I still want to send thank yous out because I know out of good faith that you guys would have helped. Have a good day/night :)

---

### Post by mörgæs on 2018-04-01
Good that you found a solution. Please use Thread Tools for marking the thread solved.

---

