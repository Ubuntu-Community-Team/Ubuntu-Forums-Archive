---
title: "Help w/ University network!"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by Flavian on 2006-10-03
Hi guys!
I got a problem, I just currently switched to Ubuntu as my main operating system. But since things here at university seem a little bit weird with the network, I am kinda frustrated to have to write this post on my windows system :(

I got network-manager installed.
I simply went to university wanted to set up the settings so I can access the Internet...
But I recognized that that is a bigger issue then it appeared to be :/

When I tried first I could not connect to the internet, but NOW I can not even connect to the Local Network, because nm-applet is not showing "WIRED Network" anymore!!

What I did first is that I put in the IP / Gateway / DNS into the gnome network manager gui and everytime I wanted to connect, nm-applet took a LONG time to connect to the wired network and then when it WAS connected I could not access the Internet.
Taking a look at "ifconfig" it said weird IP adresses, I never entered before :/

Is the problem maybe, because I used the common gnome network manager for putting in my IPs and not "network-manager" ??
If so, where do I put in the correct Ips and how do I get network-manager to recognize my wired network again (which was there before, even at university!!) - Now it is gone without any reason :( (or maybe with a reason I don't know)

Thanks for any help!
Flo

---

### Post by Iowan on 2006-10-03
Check **/etc/network/interfaces** to see if the wired connection is there.  I suspect the DNS may have gotten "reconfigured" - **/etc/resolv.conf** may need to be adjusted.  I'm nowhere near my Ubuntu box, so I can't be of much help - other than to recommending a search on resolv.conf and/or /etc/network/interfaces.

---

### Post by Flavian on 2006-10-03
I found the problem...
If one uses network-manager instead of the "gnome network manager" that comes with Ubuntu you can not use the "gnome network manager" at all anymore. That's what caused problems.
I simply disabled "eth1" and now it shows up in "network-manager"
Now my question is: Since I always only used a router at home with a DHCP server, I had no problems so far, but now since my Ip adress is static, I have to set it.
How can I set the IP adress in "network-manager (nm-applet)" ?
I think then it will work.

Last but not least I got a screenshot of how it looks like.
Note the wrong IP adress (dunno where it comes from)
It should be:
IP: 192.168.30.184
Subnet: 255.255.255.0
DNS1: 193.170.244.18
DNS2: 193.170.244.19

How can I change the current settings to what they should be?
Without using the standard gnome-network manager.
Thanks for any help
Flo

---

### Post by kipeloff on 2006-10-03
1) if you will set check box 'Enable connection' no reaction ?
I think, than you should be able to set IP address.

2) Alternatively you can set ip address by adding,
auto eth0
iface eth0 inet static
address 192.168.30.184
netmask 255.255.255.0
gateway

to file /etc/network/interface

Add DNS servers addresses to the /etc/resolv.conf

---

### Post by Flavian on 2006-10-03
Thanks for the solution, but it didn't work out.
The files you posted are simply the files where the standard "gnome network manager GUI" writes in!
Since nm-applet=(network-manager) overrides the standard network manager it is not usable, and using both leads to errors, like I mentioned above.
There must be a way to tell nm-applet(network-manager) the IP adresses so that it will automatically connect the "Wired network" to the given Adress!
Does anyone know a solution?

Flo

---

### Post by Flavian on 2006-10-04
Okay, I finally got it working.
The solution was, to remove network-manager and use the normal gnome version, with that I can use static IPs now...

Thanks for the help though.
Flo

---

