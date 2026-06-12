---
title: "Exploring other computers with Samba on a router LAN"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by joao82 on 2008-01-12
Hi!
Up until now I used to have a small network between 2 computers. I basically had them connected with an ethernet cable because each computer had it's own internal LAN card. I could use my laptop with Kubuntu and browse the windows desktop files in order to transfer data in and out from both computers. And I could even share the internet connection I had on the windows pc to the laptop, cause the usb modem only worked on it.
That was good as it was, but I was tired of having the desktop always turned on just to have internet access on my laptop.
So I bought a DSL modem/router to make a decent network with a permanent connection to the internet. It all worked fine and instantly. No problems with compatibility with linux or anything.
The problem is now I can't access my desktop using Kubuntu on my laptop. Whenever I start up Samba from the Remote Places menu all I get is this message:
"Unable to find any workgroups in your local network. This might be caused by an enabled firewall."
But when I turn the router firewall off through the [http://192.168.1.1/](http://192.168.1.1/) page configuration, I still get the same error. And I can't see another laptop running ubuntu either. So that's 3 computers running windows/linux on a router network and they can't see each other.
What am I doing wrong? I kept all the settings by default on the router because I'm not really sure what they mean. For example SPI and DMZ are disabled. ACL (access control) is deactivated. Multicast is also disabled. 
It's a Topcom Webracer 8001 router.

On a side note, I would prefer to have some sort of firewall working. The one on the router is pretty good, but it leaves 3 ports open permanently: 21 (ftp), 23 (telnet) and 80 (http). But I can't find any option to close/stealth them or configure any other ports. On windows I use Comodo, which I think it's excellent and Firestarter on Linux, just in case.

---

### Post by chewearn on 2008-01-13
1. In some routers, you need to allow traffic between local ports.  E.g. I have a Linksys router, there is a setting in the web interface that by default blocks local traffic.

2. In another router I used to own, it has a permanently open port.  To "trick" the router into stealth mode for that port, I enable DMZ to a local IP address that does not point to any computer/device in the local net.  That way, any traffic coming into the port get routed to nothing.  The result is that there is not ACK back from that port, essentially its stealthed.

3. If you are not constantly running huge traffic through the router, enable SPI (stateful packet inspection) is a good thing, as it increase the "strength" of the router firewall.  If you are running huge traffic though, you might eventually crash the router because of memory overflow.

---

### Post by joao82 on 2008-01-13
Thanks for the tips.
I got desperate and started installing everything related to nfs and samba and created shared folders on every computer. The strange thing is, after creating a shared folder with samba on the kubuntu laptop I could finally see and browse all the folders on the windows desktop. Pretty weird, but working now.

---

