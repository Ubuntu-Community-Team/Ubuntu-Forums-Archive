---
title: "WAN IP and Internal IP Confusion"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Darkling on 2006-09-04
Hi all,

The players:
Ubuntu 6.06
D-Link DSL-504T ADSL Router/Modem
Gigabyte GN-BR01G Wireless Router


I have been having a problem with my D-Link router on various Linuxes for the last few years where I would lose the DNS entries in resolv.conf everytime the dhcp lease expired. Two days ago, I came up with a plan to fix this.

A few months ago, I got a wireless router for my wife to use. All I did, was plug it into the DLink router (PPPoE mode) and let it autoconfigure. Everything worked well and I forgot about it. Then in a flash of inspiration, I decided to reconfigure my entire network, and hopefully get a new topology that would work well with Linux. This is what I did:

I decided I would set up my ADSL router in Bridged mode and use it as an ADSL modem. I would then connect the Gigabyte to it, and set the Gigabyte up to automatically dialup through the D-Link. And finally, I would connect to the Gigabyte, and everything would be peachy. This is my new topology:

My Computer(192.168.1.10)   ==>   GN-BR01G(192.168.1.254)   ==>   D-Link 504T(192.168.1.1)    ==>   Internet


```
eth0      Link encap:Ethernet  HWaddr 00:14:85:E6:D2:1B
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fee6:d21b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:256749062 (244.8 MiB)  TX bytes:98580135 (94.0 MiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19335 (18.8 KiB)  TX bytes:19335 (18.8 KiB)
```


```
Output from route:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```




In my network settings, I have the gateway as 192.168.1.254 (The gigabyte router), and DNS entries manually entered.
DHCP is turned on in the Gigabyte wireless router, and off in the D-Link. My IP is statically set via network options.

The upside of doing this, is that the internet works, and I dont have to mess with file permissions or scripts to keep it working. But all is not well.

There are two problems, which I believe are probably related.
1. I cant ping the D-Link router (Destination Host Unreachable), so I cant access its web based control panel. And everytime I want to change a setting, I must unplug from the Gigabyte and plug directly into the D-Link.
2. Ubuntu believes that my WAN IP and Internal IP are one and the same. This means that quite a few of my inet apps arent working properly (DCC in IRC for example)

Now I am not looking for a tutorial, all I want to know is how it should be set up in general terms. Please help, this is driving me nuts! ](*,)

---

### Post by Original Brownster on 2006-09-04
Hi,
I believe the problem is your routing table, the first entry which is quite normal in most circumstances says,
' route traffic for my subnet through myself' ie all destination in range
192.168.1.1 through to 192.168.1.254
your ping request to the adsl router never reaches it because the ip 192.168.1.1 is not actually visible to your pc.

The solution (hopefully I'm right) is to use a different subnet with the appropriate net mask for adsl router like 192.169.1.x
and re-configure your gigabit wireless jobby's default GW to the new address. the gigabit should now know about the 2 sub-nets 192.168. x.x and 192.169.x.x and have a default GW to reach the adsl router.

Now when you try and connect to the adsl router the gigabyte box will get the packets (default route) then decide to forward it via the gigabytes routing entry for this new subnet to the adsl router. Bingo, the jobs a good'un jackpot etc.

It may also work just be creating a routing entry on your pc for this 'host' ie the adsl router like 'route add host 192.168.1.1 via 192.168.1.254
I'd favour the former solution as it will most likely work but it's upto you, I don't think any is more correct than the other but perhaps the former is neater.

As for your apps, this may work too, it depends on how 'clever' your box's are, I would have said you would certainly need to set up port forwarding in some cases so that traffic destined to a certain port to establish a new connection is correctly directed to your pc. See how it goes.

---

### Post by Darkling on 2006-09-04
Original Brownster: Wow, thanks for that explanation.

I decided to go with the former method of setting up the ADSL router as follows:

D-Link router (Bridged mode of course)
IP: 192.169.1.1
Netmask: 255.255.255.0

My Gigabyte with the following
IP: 192.168.1.254
Netmask: 255.255.255.0

And an entry in the static routing table like this:
Target: 192.169.1.0     (Since the DLink is 192.169.1.1)
Netmask: 255.255.255.0
Gateway: 192.168.1.254
Metric: 2

Unfortunately Im sure I have buggered up with the netmasks. Apparently I dont know as much as I thought. What should the netmask for the D-Link router be? Or is the netmast I set for the routing table in the gigabyte wrong?
Anyway, no ping response from the 192.169.1.1 tho of course the internet is still working.

As far as the programs not working goes, the port forwarding is all working fine, I can for example accept a DCC connection, I just cant initiate them. Reason is that Ubuntu doesnt seem able to find its WAN IP, and sends its local ip instead.

Damn, all these numbers make my head hurt! Thanks for the help anyway!
:p

---

### Post by Original Brownster on 2006-09-05
Hi,
The mask is correct, both ranges are class c address's and should work so I'm not sure what the issue is here, 
Although pinging is not working have you tried connecting to the router network interface again?
Things worth checking:

Since you have a network connection working, the routers are routing the traffic back to you correctly it would seem so why the ping request does not return...

It might help to use the 'tracepath' command to see where the routing goes wrong.

Does a ping to say a well know web address work and just not to the router?

You could check to see it's not a firewall issue, your gigabyte or dsl ignoring ping requests.


My knowledge of using bridges is sketchy to say the least, bridges do not use IP and transfers at a mac address level (I think) maybe this is the issue but I really don't know and you could try switching to routing mode. Maybe someone else reading this will chip in.

Normally your DSL box will use NAT to show your address as the ISP address, is this turned off or maybe linked to the using the router in bridging mode? < clutching at straws >

HTH

---

