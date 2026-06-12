---
title: "Find IP address of router I'm directly connected to?"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by Hatchetfish on 2006-12-07
Short question is this:  Without prior knowledge of the router, how do I find the IP of the router my machine is plugged into?

Explanation:  I'm on a large network, but plugging in my own wireless router, which is allowed.  What's not allowed is any dhcp server but that of the larger network, and evidently NAT as well.  The consequence of this is that my little consumer wap/router has to be configured to not use dhcp, or nat, and takes its cue from the network dhcp servers, such that it's superficially serving simply as a switch.  The problem arrises when I need to get to its web configuration page, normally at [http://192.168.1.1](http://192.168.1.1), only now at an unknown IP assigned to the router from on high.  How do I divine this new IP, given the knowledge that my machines are connected to it directly, and tools in ubuntu?

---

### Post by wieman01 on 2006-12-07
Please try this command from a terminal:
> route

---

### Post by Hatchetfish on 2006-12-07
Hmm.  I can't seem to make any useful sense of the output.  I read it like this, please do correct me if I'm wrong; for destinations on the same xxx.xxx.xxx as the machine, no gateway is needed, that makes sense, as does the 255^3.0 mask.  For 'default' destinations, gateway is 'gateway.<things that possibly identify my network more than i'd like to>' and mask is 0.0.0.0

Is there another step, or am I missing how this gives the ip of the router?

Thank you though.

---

### Post by wieman01 on 2006-12-07
That should be the right command. You could also try this:
> ifconfig
Are you sure you are connected? Can you ping any other computer in the network?

---

### Post by FrodoB on 2006-12-07
In this example the router for the eth0 device is at 192.168.0.2

```

user@Edgy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.2     0.0.0.0         UG    0      0        0 eth1
default         192.168.0.2     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by Hatchetfish on 2006-12-07
I'm most definitely connected, I'm posting from the machine, have an IP in the range of the network, and can ping other machines on it, yes.

---

### Post by Hatchetfish on 2006-12-07
@ Frodo:  That's more or less what I understood, but I don't think the router is what's listed where you have 192.168.0.2

Is there a way route could be giving me incorrect information, or should I now focus on why I can't seem to get a response from the router, secure in the knowledge it -is- at that address?

---

### Post by wieman01 on 2006-12-07
Perhaps the router has HTTPS enabled. Could you try to access it this way?
> [COLOR="Red"]https[/COLOR]://192.168.xxx.xxx
Or web access is disabled after all?

---

### Post by Hatchetfish on 2006-12-07
Concerning ifconfig, where in the output of it would useful info be?  I understand that it gives me the machine's ip, and the broadcast, but i don't see anything that would explain how to get to this router.

---

### Post by FrodoB on 2006-12-07
> **Hatchetfish said:**
> @ Frodo:  That's more or less what I understood, but I don't think the router is what's listed where you have 192.168.0.2

Is there a way route could be giving me incorrect information, or should I now focus on why I can't seem to get a response from the router, secure in the knowledge it -is- at that address?

That is your machine's default gateway route out of your network. If the data that you are getting from this does not make sense, then that would be a problem.

---

### Post by Hatchetfish on 2006-12-07
well, web access may be disabled, though i don't believe so.  either way, the gateway address i'm given by route is unreachable.  ping says it's an unknown host in fact.

---

### Post by FrodoB on 2006-12-07
I see. You can use nmap to map your network using OS detection:

Install nmap:

user@Edgy:~$ sudo apt-get install nmap

Find all machines and their OS on 192.168.0.*:

user@Edgy:~$ sudo nmap -O 192.168.0.0/24

Change to the network that you installed your device on.

This will at least tell you which IP addresses to try to browse to.

It may be a good idea to as for permission to do this as some people consider the mapping of the network a hostile act if it was not properly authorized.

---

### Post by kylevan on 2006-12-07
well, here's an idea, why don't you unplug from the wider network and try the default config IP?

---

### Post by FrodoB on 2006-12-07
Also, you should be able to give your MAC identifier from the device to your DHCP adminstrator and they should be able to tell what address is being assigned to your device.

I would think that they would want this thing at a fixed address anyway.

---

### Post by Hatchetfish on 2006-12-07
Well, nmap (or permission for it) is pretty well out of the question, this is a university residential network, and while adding the router is entirely kosher (provided it defers to their dhcp server and doesn't hide a network behind nat) they almost certainly consider mapping hostile, and will in no way give permission for it.  Likewise, I doubt that asking to have them identify it by mac would get anywhere.  Incidentally, so far as them wanting it static, they expressly -forbid- static ip's (will in fact disconnect them) so that they can reallocate within their block with less trouble.

  I think what it comes down to is that anytime it needs altered, I'm going to have to disconnect it from the network, reset it to factory spec so I can get to it (disconnecting and a soft reset doesn't alter its IP) and redo -all- the settings.  I shouldn't need to particularly often, so it's inconvenient, but at least infrequently inconvenient.  

  I just set the router up this evening, and then remembered that if I needed to fiddle with the thing in future, the old friend 192.168.1.1 wasn't going to do it anymore, and figured there'd have to be some easy way to get the IP of the black box on the immediate other end of the cable.

  Evidently not, at least in this case.  Thank you all very much for trying though.

---

### Post by spd106 on 2006-12-08
Have you tried **arping** the mac address of the router? It should tell you on the underside of the device. If not then match the results of **arp** with the likely vendor codes for your device. [http://www.coffer.com/mac_find/](http://www.coffer.com/mac_find/).

---

### Post by mips on 2006-12-08
> **Hatchetfish said:**
> Short question is this:  Without prior knowledge of the router, how do I find the IP of the router my machine is plugged into?

Explanation:  I'm on a large network, but plugging in my own wireless router, which is allowed.  What's not allowed is any dhcp server but that of the larger network, and evidently NAT as well.  The consequence of this is that my little consumer wap/router has to be configured to not use dhcp, or nat, and takes its cue from the network dhcp servers, such that it's superficially serving simply as a switch.  The problem arrises when I need to get to its web configuration page, normally at [http://192.168.1.1](http://192.168.1.1), only now at an unknown IP assigned to the router from on high.  How do I divine this new IP, given the knowledge that my machines are connected to it directly, and tools in ubuntu?

I thought about this for a while and came to the conclusion that you are screwed if that is the way it *must* work. For I simply cannot see it working at all irrespective of whether you use linux, windows, osx etx.

The only way I see it working is as follows:

1. Lets assume A is the campus network side and B is your LAN side of your wireless router.
2. Configure A side to get IP via DHCP
3. Enable DHCP server on B side.

How do all the other people do it ???

---

### Post by dbott67 on 2006-12-08
If you want to setup your wireless router to forward DHCP requests to the school's server, you must do the following:

1. Disconnect your router from the school network.  If you have the manual handy, you may just want to reset the router to factory settings.  The manual should provide you with the default IP address for configuration purposes.

2. Connect via LAN cable to one of the 4 ethernet ports on the wireless router & login (as posted by others, you should be able to discern the IP address by using the **route -n** command).

*You may have to restart your computer or run sudo dhclient to get an IP from your router.*

3. Once logged in, turn off DHCP services.
4. Save settings & cycle the power on your router.
5. Re-connect your router to the school LAN, but **[COLOR="Red"]DO NOT USE the WAN port[/COLOR]** --- use one of the 4 LAN ports (you will essentially only be using the router as a 'wireless switch').
6. Keep your computer plugged into one of the 3 remaining LAN ports & try to connect to the network (**sudo dhclient eth0** or **sudo ifdown eth0 && sudo ifup eth0**).
7. Once everything works via the 'wire', try connecting wirelessly.

The **ifconfig -a** and **route -n** commands will show you the school's assigned IP and default gateway.

Basically, the school does not want you to use NAT or the router/firewall function, so you just need to 'neuter' it by turning off DHCP and NOT USING the WAN port.



-Dave

---

### Post by mips on 2006-12-08
I thought he wanted to plug the wireless router into the network in order to use the wireless functionality ???

---

### Post by dbott67 on 2006-12-08
I'm assuming he does... the wireless will still work, it will just forward the DHCP request to the school's server.

The reason I suggest connect via cable is to verify that he is able to get online.  Once it works via cable, the wireless setup will be a walk in the park with a pretty girl! :)

---

### Post by FrodoB on 2006-12-08
Try the arp command:

sudo arp

---

### Post by softuse on 2007-11-11
> **wieman01 said:**
> Please try this command from a terminal:

hi thanks

---

