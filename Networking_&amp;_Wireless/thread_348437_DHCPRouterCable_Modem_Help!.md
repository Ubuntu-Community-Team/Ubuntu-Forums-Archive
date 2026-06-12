---
title: "DHCP/Router/Cable Modem Help!"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by staplerz on 2007-01-28
[SIZE="4"]Roadrunner--->My Cable Modem--->My D-Link router(eth0 Connection)--->My Ubuntu PC[/SIZE]

I have been trying to get the internet working om my pc for a few days now and its driving me crazy. This forum is my last resort. I have a cable modem which is connected to my DHCP D-link router. The router is connected to my comp using a Ethernet cord.  I have pinged my router and here are the results:
[IMG]http://tinypic.com/29lzq8p.jpg[/IMG]


I also tried to ping 66.102.7.104 (google):

**staplerz@ubuntu:~$** ping 66.102.7.104
connect: Network is unreachable
**staplerz@ubuntu:~$ **

Can anyone help me??

---

### Post by haiku99 on 2007-01-28
does it work without the router, plugged directly into the cable modem??  does it work w/ windows??   need more info...

---

### Post by staplerz on 2007-01-28
> **haiku99 said:**
> does it work without the router, plugged directly into the cable modem??  does it work w/ windows??   need more info...

I dont know if it works on windows because i just built my comp yesterday and installed ubuntu. It works fine on my other windows pc but i haven't installed windows on the Ubuntu comp. I just tried to connect the Ethernet cord from the modem directly to the comp and it did not work. the PC link light on my cable modem did not light up.

---

### Post by kosmic on 2007-01-28
We need more info.

Your eth0 IP -> is DHCP right ?
What configuration you have in your router, maybe your router is blocking the acess to the modem

---

### Post by staplerz on 2007-01-28
Didnt mean to post this. Ignore

---

### Post by staplerz on 2007-01-28
> **kosmic said:**
> We need more info.

Your eth0 IP -> is DHCP right ?
What configuration you have in your router, maybe your router is blocking the acess to the modem

I'm pretty sure its says "**DHCP Server:** Enabled" but other than that i have no idea how to check if it is...And how can i give more info if i dont know what info to give...i dont think thats the problem because i can connect to the internet through my router just fine on the pc im on right now..

---

### Post by staplerz on 2007-01-28
Anyone know whats wrong?

---

### Post by Cobikegeek on 2007-01-28
Have you looked at your router setup by entering the router ip address in your browser?  Does it recognize your ubuntu pc (or even access your router)?  If not, you may need to enter you pc's ip address and mac address in your router setup.  (the d-link website has some useful info if don't have your router documentation or manual)

You might also try making all the connections, then booting your ubuntu pc from the live cd and seeing if ubuntu recognizes your modem/router hardware setup and you can get on the web.  If it does, look at the info under "system->networking" to see how ubuntu set everything up.

I had a similar setup to yours and on reboot ubuntu recognized everything.  Sorry to hear it hasn't been that easy for you.

---

### Post by RandomJoe on 2007-01-29
I would say you don't have / aren't getting a default route.  If you can ping the router, then you are getting (or have set) a valid IP.  The 'network unreachable' means the Ubuntu computer doesn't know where to send the packet to get to outside IPs.  (It could also be as the others said, the router is using MAC filtering or something.)

In a terminal window, run 'route'.  You should see something like:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.144.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.144.1 0.0.0.0         UG    0      0        0 eth0

```
You have to have the 'default' line in order to route to the Internet.  Yours should have 192.168.0.1 as the Gateway.

If it isn't there, try the following command:
```
sudo route add default gw 192.168.0.1
```
That will add the default route, see if you can get to the net then.

You can also try checking System -> Administration -> Network Settings.  At the bottom of the Connections tab is Default Gateway Device:  It should be set to your ethernet card's interface name.

If this works, the next problem is figuring out why it doesn't get set right to begin with.  It has always been automatic for me, although it might get set wrong if you have two active network connections.

---

### Post by Trzone on 2007-07-30
I also have a road runner modem with a dlink router.
I just installed Ubuntu and the router never recognizes ubuntu as being connected
this has happened before with my road runner modem

usually you just have to reinstall ubuntu.
i'll have to try that in the morning.


The router seems to not recognize Ubuntu as a computer
as in there is no connection on the router
not even from the live cd.
could it be the way the router is configured?
my router is a dlink wbr-1310


and... now a few hours later
suddenly, i turn off my computer with a power bar
which has everything on it
including modem and router
wait 10 seconds
turn it on
wait 1 min
turn my computer on and suddenly it works heh

---

