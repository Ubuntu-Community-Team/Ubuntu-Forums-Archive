---
title: "How to request specific IP address from router?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by RootsLINUX on 2007-04-16
Hi. I've been successfully using my debian desktop and ubuntu laptop with my wireless network at home for some time. However, I'd like to arrange it so that each computer requests a specific IP address from the router, instead of just relying on whatever dhcp gives it. I'm pretty sure all I have to do is add something to my /etc/network/interfaces file, but I have been unable to find out what that is. Here is my copy of that file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid OMITTED
wireless-mode managed
wireless-key OMITTED

# The secondary network interface
#auto eth0
iface eth0 inet dhcp

```


Can anyone enlighten me? Thanks in advance :wink:

---

### Post by rufius on 2007-04-16
This link should help you out :)

[http://textsnippets.com/posts/show/319](http://textsnippets.com/posts/show/319)

---

### Post by capitalistpiglet on 2007-04-16
You can assign static ip addresses to machines from the routers config page.

---

### Post by computerease on 2007-04-16
I would, indeed, cop for the static IP on the station itself and tell the router to reserve the static IP address.  There is an alternative to telling the router to reserve the IP.  You can give the IP address OUTSIDE the DHCP assignment range.  For instance, If the IP range is x.x.x.1-50, assign 51 or 52 etc.

---

### Post by reauthor on 2007-04-16
> **RootsLINUX said:**
> Hi. I've been successfully using my debian desktop and ubuntu laptop with my wireless network at home for some time. However, I'd like to arrange it so that each computer requests a specific IP address from the router, instead of just relying on whatever dhcp gives it. I'm pretty sure all I have to do is add something to my /etc/network/interfaces file, but I have been unable to find out what that is. Here is my copy of that file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid OMITTED
wireless-mode managed
wireless-key OMITTED

# The secondary network interface
#auto eth0
iface eth0 inet dhcp

```


Can anyone enlighten me? Thanks in advance :wink:

# The primary network interface
auto wlan0
iface wlan0 inet static
address 192.168.1.1(depends of ip range of your dhcp in your router)
netmask 255.255.255.0
gateway 192.168.1.254(put here address of your router 
wireless-essid OMITTED
wireless-mode managed
wireless-key OMITTE

---

### Post by theToolman on 2008-04-27
I have had this issue, and I also have a cheap DSL router with builtin DHCP.  The problem is that the router doesn't have any static IP assignment from the web gui, I know that some routers can only set statics via telent but not even there!

It does have NAT but without static IP assignment its frustrating!

My solution is to limit the DCHP range in the router - in my case to

192.168.1.[2-200]

and then add a second IP to my DHCP interface (in my case wlan0, but if you are cabled, then its likely eth0)

I simply added these lines to /etc/network/interfaces :

```

# The secondary (static) network interface over wireless
auto wlan0:1
iface wlan0:1 inet static
        address 192.168.1.201
        netmask 255.255.255.0
        broadcast 192.168.1.255

```

SO all my NAT goes to my xxx.201 IP which is always static, and DHCP assigns anything in the xxx.[2-200] range, i dont care which!

Don't forget that you are hard setting that second IP, so if you go to other networks, you mgiht clobber the real owner of (in my case) 192.168.1.201 so take down that interface if you are not at your local location.

---

