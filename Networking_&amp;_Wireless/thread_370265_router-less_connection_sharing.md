---
title: "router-less connection sharing"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-02-25
Hi all!

I have a rather odd network setup here, in that I HAVE a router, but it is too far away to get a network cable to one of the dektops. I also have a laptop with a wireless card, as well as ethernet. 

It should be possible to connect the desktop to the router through the latop, so Dektop->Laptop->Router, but I have no idea how to go about this. Most posts like this end with "Get a router, they are cheap", but I am by no realistic means going to get another one. 

The laptop runs ubuntu 6.06, and the desktops can run whatever you feel like having them run (currently win2k and 95, but the installs are of no value at all).

Any tips, links?

Thanks
-K

---

### Post by n8bounds on 2007-02-25
search for ipmasq (for your lappy)

---

### Post by Kulgan on 2007-02-25
I guess that would be ipmasq as well as ipmasqadm? Well, they are both installed. So.... now what? :| I understand the basics of networking, but I'm not your all-knowing guru, so try to be forgiving. Yes, I do know how to become root :P 

Eventually, will the desktop have the same relative IPs as the rest of the network? ie, the laptop is set up as a switch rather than as a router-like... something... ? 

Cheers :D

---

### Post by koenn on 2007-02-25
connection sharing is based on routing. The only other way I can think of is that your laptop would be running a proxy http server (squid) which would allow other pc's to access the web through it (but not use other network apps eg e-mail, p2p file sharing, ...)

don't get confused by the routing. It's very well possible to set up a linux system do do the necessary routing. 
Here's one : [http://ubuntuforums.org/showthread.php?t=358169](http://ubuntuforums.org/showthread.php?t=358169) (look at post #2)
you'll have to translate that in that the "external" interface will be your wireless that connects you to the router. You may or may not need the NAT. 

Give it a try and come back when you get stuck

---

### Post by Kulgan on 2007-02-26
Ok, so I tried the stuff in post #2 of that one, and it most definitely doesn't work. I no longer have an internet connection on the ubuntu laptop. Well, I do, but I can't ping outside my local network, and can't load anything whatsoever. 

in the "iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE", was the -o <interface> supposed to be the "external" device, as you say? That's probably where I went wrong... 

Also, what do I set up the windows machine as? I know how to configure the network settings, I just don't know what to cofgure them TO! 

Thanks for the help so far :D

-K

---

### Post by netztier on 2007-02-26
> **Kulgan said:**
> 
It should be possible to connect the desktop to the router through the latop, so Dektop->Laptop->Router, but I have no idea how to go about this. Most posts like this end with "Get a router, they are cheap", but I am by no realistic means going to get another one. 

Does the router have an integrated WLAN Access Point?

If yes, get one of these "multi-purpose" WLAN access points, such as the ZyXEL G-570S.  They can be configured as as **WLAN Workgroup Bridge**. Install a switch/hub that wires up your desktops to a LAN, then run one cable from that switch as far as possible/needed towards the WLAN router and place the workgroup bridge there. Done.

Like this, all of these devices are in one LAN and there's no cascade of routers and "ineternet sharing devices" (which can be very painful to debug...)

best regards

Marc

---

### Post by Kulgan on 2007-02-26
yeh, what I would like most of all is to wire from the router to my room, which is about two metres from being as far away from the router as it is possible to be and still be within the house. It's just not an option. :'(

Neither is your suggestion, unless I somehow get my hand on some money to buy one with. Things like that are rather costly here....

I changed the eth0 in the command from the other howto to eth1, rebooted, and couldn't log in (type in username and password, get brown screen and no more). I booted into Fedora Core, just to see if there was anything wrong, and I can access everything perfectly (from FC). 

Reboot back into ubuntu, and it takes AGES (like 5 mins) to log on. Still no internet connection, can't ping things, and can't connect to network. Yay. 

I am now willing to forget the whole issue if I can get the network working on ubuntu again without having to reinstall... I'm lame that way :/

---

### Post by Kulgan on 2007-02-26
Well, just removing it from the /etc/init.d/ folder an rebooting has me back on the network. I found a rather old (and therefore rather slow) wireless card to put in it, but unfortuneately I only have one of them, and several comps to get online... oh well, I'll see how things go...

---

### Post by koenn on 2007-02-26
OK, first let's see if we can undo a few things. 
The only thing that has actually changed if you followed those instructions is that you have a file /etc/init.d/iptables.sh that runs some commands at startup. We'll take one out.
Open the file with a text editor (as root)
```
sudo gedit /etc/init.d/iptables.sh
```
then put a **#** in front of the "iptables -t nat -A .... " line
save, close the file, etc ...

Then reboot, see if anything's gotten better. 
> 
in the "iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE", was the -o <interface> supposed to be the "external" device, as you say? Yes. 

The delays at boot time are probably just failing dhcp requests for a now misconfigured network card, so that problem will probably go away. 

On any case, post the output of the following command  
```
ifconfig
netstat -nr 
```
and the contents of the file /etc/network/interfaces

That should help with (a) further troubleshooting if needed, and (b) setting up routing correctly. 

what we're going for is basically 2 networks, 1 that consists of the far away router and the wireless interface of the laptop, an other that consists of the ethernet card of the laptop and any computer you attach to that. Then, the laptop will route the traffic between its 2 network interfaces. That should allow the Windows machine to reach the wireless router that will then further route towards the internet. 

So as for the network settings on the windows machines : 
you can manually assign IP addresses (different from the address **range** used by the wireless network !), a network mask and a default gateway (which should be the address of the network card on the laptop).
or you can have this done by dhcp but that resquires your setting up a dhcp server (on the laptop). The manual config is easier for now. I can suggest some addresses if your not sure about how to go about it.

---

### Post by koenn on 2007-02-26
oops, looks like i missed a post. 
You got your network back. Want to give that routing another try ?

---

### Post by Kulgan on 2007-02-26
hehehe, of course! :D

The wireless card is so slow that it's beginning to annoy me, so why the hell not?

Thanks for leading me through it - once I have done something once, I can usually do it again, and adjust it, but it's doing it that one time that messes things up... -.-

I'm trying the above right now :D

-K

---

### Post by koenn on 2007-02-26
OK  -  take notes of what you did, in what order, in case we need to backtrack. 
Don't put in that MASQUERADE yet, you may not need it (or leave it commented out with the # )

---

### Post by jglen490 on 2007-02-26
> **Kulgan said:**
> Hi all!

I have a rather odd network setup here, in that I HAVE a router, but it is too far away to get a network cable to one of the dektops. I also have a laptop with a wireless card, as well as ethernet. 

It should be possible to connect the desktop to the router through the latop, so Dektop->Laptop->Router, but I have no idea how to go about this. Most posts like this end with "Get a router, they are cheap", but I am by no realistic means going to get another one. 

The laptop runs ubuntu 6.06, and the desktops can run whatever you feel like having them run (currently win2k and 95, but the installs are of no value at all).

Any tips, links?

Thanks
-K

Well, by now you could have walked (not run ;) ) to a store and gotten a hardware switch.  Until I got wifi working on my laptop, I had a switch between the lappy and my router that took care of the lappy and another desktop as well as a distance issue.  Was simple, cheap, and effective.

---

### Post by koenn on 2007-02-26
> **jglen490 said:**
> Well, by now you could have walked  to a store ... 
where's the fun in *that* ?

---

### Post by netztier on 2007-02-26
> **koenn said:**
> That should allow the Windows machine to reach the wireless router that will then further route towards the internet. 


Yes, if we turn the laptop into a classical non-NATting router, it might work. BUT on the WLAN router, there will have to be a static route for the new IP subnet with the laptop's WLAN interface as next hop. If not, the WLAN router won't know what to do with the incoming packets once they have passed it's NAT & Firewall engine.

Example ([COLOR="DarkGreen"]green: Internet adresses and routes[/COLOR], [COLOR="Blue"]blue: addresses and routes for the WLAN network[/COLOR], [COLOR="Red"]red: addresses and routes for the innermost LAN[/COLOR])

**WLAN-Router:**
outside Interface (WAN): [COLOR="DarkGreen"][provider-assigned:  DHCP, static or PPPoE negotiated][/COLOR]
Inside Interface (LAN): [COLOR="Blue"]192.168.0.1 (netmask 255.255.255.0)[/COLOR]
static route: [COLOR="DarkGreen"]0.0.0.0, mask 0.0.0.0,[/COLOR] via [COLOR="DarkGreen"]*[provider next hop address, automatic]*[/COLOR]
static route: [COLOR="Red"]192.168.1.0, mask 255.255.255.0,[/COLOR] via [COLOR="Blue"]192.168.0.20[/COLOR] [COLOR="SlateGray"]*<--- This static route must not be forgotten (see above statement)*[/COLOR]

**Linux-Router:**
outside (WLAN)-Interface: [COLOR="Blue"]192.168.0.20 (netmask 255.255.255.0)[/COLOR]
inside (LAN)-Interface: [COLOR="Red"]192.168.1.1 (netmask 255.255.255.0)[/COLOR]
static route:[COLOR="DarkGreen"] 0.0.0.0, mask 0.0.0.0,[/COLOR] via [COLOR="Blue"]192.168.0.1[/COLOR]

best regards

Marc

---

### Post by koenn on 2007-02-26
yeah - i thought i was missing something there. 

alternatively, I think NAT on the Linux router would work, like 
- the linux machine would make nat/pat entries for the natted outgoing packets, so 
- when replies to those arrive back at the linux router, they'd match an entry in the natted addresses/ports, and be forwarded to the machines that initiated the connection. 

What do you think ? 

---
I was thinking : first get those two networksoperational and verify that the windows machines have a route to the WLAN router, 
then deal with the rest.

---

### Post by netztier on 2007-02-26
> **koenn said:**
> 
alternatively, I think NAT on the Linux router would work, like 
- the linux machine would make nat/pat entries for the natted outgoing packets, so 
- when replies to those arrive back at the linux router, they'd match an entry in the natted addresses/ports, and be forwarded to the machines that initiated the connection. 

What do you think ? 


'xactly. If the Linux router performs nat/pat, there's no routing configuration needed on the WLAN router, because all connections look as if they were coming from the Linux router's WLAN interface. The Linux router itself however needs that static route for 0.0.0.0/0.0.0.0 in any case!

best regards

Marc

---

### Post by Kulgan on 2007-02-27
There seems to be something wrong with my wireless network - even slow downloads on a windows machine (not related to the one the I'm trying to connect to the ubuntu laptop) makes it EXTREMELY slow. It's torrents on windows, no more than about 50 kbps down, and I technically have 4000/400. The windows machine is wired to the router, though, so that is probably the cause. 

I did as koenn said earlier... Before reboot:
> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:14:71:94
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:1C:53:E3
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe1c:53e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6311552 (6.0 MiB)  TX bytes:974359 (951.5 KiB)
          Interrupt:5 Base address:0xc000 Memory:fcffe000-fcffefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1


After reboot (though I forgot to turn the windows box on ](*,) ):
> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:14:71:94
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:1C:53:E3
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe1c:53e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87304 (85.2 KiB)  TX bytes:1904 (1.8 KiB)
          Interrupt:5 Base address:0x2000 Memory:fcffe000-fcffefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1


Figured out that it was supposed to be on...
> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:14:71:94
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:1C:53:E3
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe1c:53e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47806 (46.6 KiB)  TX bytes:1720 (1.6 KiB)
          Interrupt:5 Base address:0xa000 Memory:fcffe000-fcffefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1


The contents of the file:
```
iptables --flush
iptables -P FORWARD ACCEPT

# iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

echo "1" > /proc/sys/net/ipv4/ip_forward

```

Though I had to comment out everything in it to be able to connect to the router again...
Hopefully there's something in there that I don't see. :/

-K

---

### Post by koenn on 2007-02-27
> eth0 Link encap:Ethernet HWaddr 00:12:3F:14:71:94
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
This is a problem.
eth0 should have an IP address. 

I assume your router is 192.168.0.1 (the gateway address for the ubuntu laptop), and then eth1 would be your wireless nic. 

That makes eth0 the NIC you'll connect the windows box to. 
You need to choose an IP address for this one - 
following netztier's example we can use 192.168.1.0 as the second network, so that means that in /etc/network/interfaces you need to have the following : 

```
auto eth0
iface eth0 inet static
  address 192.168.1.1
  network 192.168.1.0
  netmask 255.255.255.0
  broadcast 196.168.1.255
  
```

your windows machine would need matching network settings (but a different IP address) eg
ip address : 192.168.1.100
mask 255.255.255.0
default gateway:** 192.168.1.1**  - that's the address of eth0 on the linux router

show us the output of ifconfig and netstat -nr egain to see if everything looks OK after those changes.
Also, from your laptop, both of the following should get replies ;
```
ping  192.168.1.100
ping 192.168.0.1
```

---

### Post by Kulgan on 2007-02-27
will assigning an IP to eth0 solve the problem of not having a wireless connection to the router when booting with the 

> iptables --flush
iptables -P FORWARD ACCEPT

# iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

echo "1" > /proc/sys/net/ipv4/ip_forward

file?

---

### Post by koenn on 2007-02-27
the only problem i can see with that file is thet
- my assomption about eth1 being the wireless is worng
or
- you had eth0 as output interface in that file, and eth0 had no IP address so all the address translation would fail

in that case, the NAT would blank the destination address of packages passing through the router and that could more or less explain the problem you had. 

so the answer to your question is : maybe. 

try without it first, see if everything checks out, then proceed. troubleshooting is way easier if you know the "last working config".

---

### Post by Kulgan on 2007-02-27
will do as you say. However, it might take a little time, due to the router screwing up it's wireless, and for some reason only working when I'm close to it. I'm having to rearrange things a little, but I will try it first thing tomorrow :P

---

### Post by koenn on 2007-02-27
fine with me. I'll check in whenever i get a 'new post' notification.

---

