---
title: "Help needed for an Ubuntu/Win XP LAN and shared Internet!"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by gravityaddict on 2007-03-04
Hi, firstly I have to apologise for being new to Ubuntu and only knowing so much about computers. I have two machines, one running Win XP with everything connected such as my USB ADSL Modem, printer etc, and another older machine running purely on Ubuntu without any extras attached. Basically what I want to achive is a working LAN connection between the two machines on which I can share the internet connection & other resources from my XP computer. I had both machines running on XP a while ago with a working LAN connection, but since then I've been playing with settings trying to get things working. I've been reading lots of posts about this sort of thing but most seem to concern wireless setups and havn't really gained much from them. On my Ubuntu machine ifconfig brings up:

eth0     Link encap:Ethernet HWaddr 00:20:ED:3E:80:7D
           inet6 addr: fe80::220:edff:fe3e:807d/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:250 errors:0 dropped:0 overruns:0 frame:0
           TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
           Collisions:0 txqueuelen:1000
           RX bytes:48483 (47.3 KiB)    TX bytes:34326 (33.5 KiB)
           Interrupt:193 Base address:0x6ff00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPCACK RUNNING MTU:16436 Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5968 (5.8 Kib)    TX bytes:5968 (5.8 KiB)

My Ubuntu machine shows a Windows Network Icon when browsing the Network, but when clicked I get an empty browser window.

On my XP Network connections I have a LAN (Intel(R) Pro/100 VE Network Connection), a 1394 Net Adapter and a BT Voyager 105 USB ADSL Modem.

If anyone can make any sense out of this and point me in the right direction It would be much appreciated! Cheers

---

### Post by gravityaddict on 2007-03-04
Ok, I've reset my settings on my windows machine and I've got the internet working on my Ubuntu machine, but I still cant get a working LAN set up. Any pointers anyone?

---

### Post by tyres on 2007-03-04
Hi gravityaddict,

You don't say what you're using to connect your XP machine to your Ubuntu machine. Presumably it's an ethernet cable? If it's a direct connection you need a crossover cable. If it's not a crossover cable I think you'll need a hub to connect the two computers.

Colin

---

### Post by gravityaddict on 2007-03-04
Yeah its an Ethernet Cable, I managed to get a LAN working fine before with the exact same wiring setup but with both machines on Windows, so I know its possible. I'm just not sure what to do next, I spent hours setting one up last time and I cant remember what I did now to be honest.

---

### Post by tyres on 2007-03-04
Hi gravityaddict,

Assuming it's a crossover cable you've got, I have set up an Ubuntu to Ubuntu connection using this setup. Not, however, an XP to Ubuntu connection.

I found I had to setup static IP addresses, I think because I also had a wireless connection set up on the machines, and the wireless and ethernet adapters seemed to not like co-existing on the same subnet (not too sure if that's the right term). So where my wireless IP address was of the form 192.168.1.x, I set the ethernet direct cable connection static IP address to be of the form 192.168.0.x (0 rather than 1 as the third 'octet' I think it's called). That seemed to stop them interfering with each other. If you've not got a wireless connection (at least on one of the machines) you may not need to use '0' instead of '1'. I've got wireless set up on both machines.

I set the IP adddress  (for Ubuntu) up in the /etc/network/interfaces script, like this 

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.x
netmask 255.255.255.0

Replace 'x' with whatever number you want. I did the same thing on the other Ubuntu machine, and then checked to see if I could 'ping' from one to the other. As long as 'ifconfig' shows that you do have an IP address assigned to the 'eth0' adapter, I think you should be able to do this. Successful pinging established that I had connectivity between the two machines, and I could proceed from there.

I realise that this doesn't exactly do what you want to do, but maybe it will help you on your way. The Windows side of it I've not looked at, but I know XP has a facility for setting up Internet Connection Sharing (ICS).  Looking at the Properties of the 'Network Connections' applet in Control Panel may give you some help there.

Colin

---

### Post by gravityaddict on 2007-03-04
Cheers, looks like I'm just going to have to sit and fry my eyes for a day while I try to work it all out again!

---

### Post by tyres on 2007-03-04
Hi,

A couple of other things occur to me that might help you. For file-sharing between XP and Ubuntu, you've got to set up a file-share on Windows (right-click the folder you want to share and click properties. There's a 'sharing' tab). By default file-sharing is turned off in XP, so you may need to enable it. If you've got a firewall set up, you may need to add the Ubuntu machine's IP address to the 'Trusted Zone' in Windows, or else the firewall won't let connections from the Ubuntu machine through.

But first you've obviously got to get your connectivity between the two machines going! 

Colin

---

### Post by gravityaddict on 2007-03-05
Cheers for that, I already had file sharing turned on and I'd added the Ubuntu machine to the 'trusted zone' but after much messing around, pinging and eventually turning all my firewalls off I sorted it. Turns out I needed to add the Ubuntu machine into the 'trusted zone' in three different modes on my main firewall. Being unfamiliar with a new OS doesn't make things any easier eather! Thanks for the help, much appreciated. :)

---

### Post by tyres on 2007-03-05
Hi,

Glad you got it sorted out :-) The firewall thing sounds a pain :-( I set up an Ubuntu to XP share a while ago, over a wireless connection. The Zone Alarm firewall on XP only needed one entry for the 
Ubuntu machine's IP address into the 'trusted zone'.

Did you get the Internet Connection Sharing set up?  I looked at that briefly, but in the end didn't need it, as I got wireless going on the other machine, so it didn't need a shared connection to the internet (via XP).

---

### Post by gravityaddict on 2007-03-06
Yeah, I managed to sort that first. Cheers again!

---

