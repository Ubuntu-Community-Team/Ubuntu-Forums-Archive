---
title: "connect several machines"
date: 2021-04-26
forum: Networking &amp; Wireless
---

### Post by jgw on 2021-04-26
I would like to connect several machines in my house.  Some are connected directly to the system modem and others us wifi.  I used to have them connected but, over the years, it went away and I forget how I did it <sigh>

Thank you.....................

---

### Post by TheFu on 2021-04-26
Buy a router. Connect each system to the router with a CAT5e cable. Connect the router to the "internet" using the WAN port connection.

Security is a different question, completely. Not all routers are created equal. Some aren't good when you get them. Some aren't good a year after purchase because the vendor stopped providing patches.  The safest answer is to use a router that has software that gets patched weekly by the vendor for many years.  The only routers like that I know are all AMD/Intel specific-built routers that can run openwrt, pfsense, opnsense or some other x86 router software distribution.  Consumer routers usually only get patched a few years, if that long.

There are long discussions about routers in these forums already.

---

### Post by jgw on 2021-04-27
Thank you for the response

I use century link as my provider.  They provide a DSL connection and a 'modem'.  As far as I can tell I use what is called a DSL Router (Actiontec C2000A-D) which I have had for a couple of years.  I am really uncertain just what kind of router would work with my connection.  I could update to Actiontec C3000A but I don't really see any real improvement as my speed is 12/13Mbps (they want too much for faster speeds).  The other problem is that several of my machines are on wifi.  I have absolutely no idea about running programs on these things.   I will check route stuff on the forums.  Incidentally have no idea if my modem/router has ever even been updated.  I don't mess with it (other than to plug stuff in.

---

### Post by TheFu on 2021-04-27
Contact century link for help with their router and their patching.

How do you want to connect the machines in the house?  In general, **ssh** is the easiest. It provides ssh, scp, sftp access from any client. There are good clients for each of those for every OS.  Install on any debian-based distro:
```
sudo apt install ssh fail2ban
```
Then any linux file manager should let you put in *sftp://{IP address}* for the other system into the URL entry  area and connect.
On Windows, use **winscp**.

**fail2ban** is for security. It will block any client IP that fails sh/scp/sftp authentication 5 times for an hour. It only protects ssh on port 22/tcp, which is the default. No other protocols come pre-configured.

If you want to use other protocols, name the protocol, please.

---

### Post by SeijiSensei on 2021-04-28
Usually the modem has an Ethernet port that connects to a router. I have that arrangement here, with a Netlink cable modem and a D-Link AC 1750 router.  I own both these items.

If the Actiontec works as a router, then you would need different hardware to install your own router as I have done.  Another option is to buy a router and "daisy-chain" it to the Actiontec, that is, connect the Ethernet out of the Actiontec to the "WAN" port of the router.  I ran such a setup for quite some time.  I disabled the wifi in the router my provider (FiOS) supplied and connected instead to my D-Link.

---

### Post by Dennis N on 2021-04-28
If one or more of your computers is far away from your router, you can use powerline adapters to avoid wifi. Computers see these as ethernet. 
Powerline uses your house wiring to transmit your data, but with some loss of speed compared to your normal ethernet speed. It's reliable and more secure than wifi, in my opinion.

If there are more devices than the number of ethernet ports on the router, you can add a switch into the network.

---

### Post by TheFu on 2021-04-28
I use powerline to get ports on a different floor.  The powerline 600 Mbps onthe box only achieves 60 Mbps. On the same floor, got 220 Mbps.

Today, I'd use MoCA with pre-existing coax in the house. 2.5Gbps MoCa actually provides that bandwidth based on research. Hook up a 5-port switch at each remote end and it is like being n the same room with the main router.

---

### Post by jgw on 2021-04-28
Thank you for all the replies!

I have no idea what powerline is.  I transferred a connection, from the modem/router from the second story to a place in my backyard by just connecting a ethernet cable from the router to a distribution point from which I run two machines (sometimes more if I am working on another one).  Have no problems with that and have exactly the same speed from those connections as the speed on the computer directly attached to the router.   That connection is about 3 years old now and has no problems.  I have two computers that are not directly connected but are on wifi.  One is a laptop and the other is just easier to put on wifi than a powerline.  

You guys have given me a lot of stuff to digest.  I am going to have to take some time to work on it.

Thanks again!
Oh, powerline is a connection, through house wiring?  I have that installed but it doesn't work very well, it was a d-link 2000.  Still have the connectors, one is plugged into an outlet and the router and the other side to an outlet and an eithernet cable which is not connected.  (took me a bit to remember that).

Here is the router I am currently using: [http://www.actiontec.com/wp-content/uploads/2017/04/C2000a-datasheet_finalweb.pdf](http://www.actiontec.com/wp-content/uploads/2017/04/C2000a-datasheet_finalweb.pdf)

Here is another router I could buy (price is right on ebay) [https://wifi-blocker.com/router-model/centurylink-actiontec-c3000a-modem-router/](https://wifi-blocker.com/router-model/centurylink-actiontec-c3000a-modem-router/)   This one says it can tell me who is connected which may mean I could also access them?

---

### Post by TheFu on 2021-04-28
Maybe don't buy a router off ebay unless you are technical enough to actually know that you are getting what you need?  ISPs post approved models of models/routers on their websites. Check that.

Powerline ethernet is highly dependent on the quality of the house wiring. But it is 1000x more secure than wifi - perhaps 100000x more secure. Technically, a powerline ethernet connection is a "bridge", so it bridges 2-sides of a connection using the electrical wiring already in the house. Besides bandwidth changes, it is invisible on the network. It doesn't show up in pings or traceroute as "hops" and doesn't reduce the TTL for packets.
[https://www.smallnetbuilder.com/tags/powerline](https://www.smallnetbuilder.com/tags/powerline) has more on the technology and options for any lurkers.
[https://www.smallnetbuilder.com/archives/lanwan/lanwan-reviews/32716-d-link-dhp701av-powerline-av2-2000-gigabit-network-extender-kit-reviewed](https://www.smallnetbuilder.com/archives/lanwan/lanwan-reviews/32716-d-link-dhp701av-powerline-av2-2000-gigabit-network-extender-kit-reviewed) for the specific model used by jgw, I think. There are warnings about noise in the power lines causing issues.

---

### Post by jgw on 2021-05-14
I have now bought a CenturyLink Actiontec C30A  - 802.1n & 802.1ac Wi-Fi Router  Now all I have to do is hook it up. My problem is that the router is connected to my wife's machine and she is very busy with it but, eventually she will have to go someplace and then I can install it and move one.

---

