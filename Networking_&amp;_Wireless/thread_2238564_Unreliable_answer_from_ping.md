---
title: "Unreliable answer from ping?"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by Charlie_van_Weert on 2014-08-08
Hello all,  I have a very strange network problem, and am still trying to get to some kind of explanation. Maybe some networking guru luring around on this forum can shed some light?  Setup is following: 
[LIST] 
[*]One router DHCP server build into a router 
[*]Antenna system (Ubiquity) bridging a network (calll it 'garage') to another location (call it 'office'), both on fixed addresses 
[*]On the other side of the antenna's: fileserver (fixed IP address) running Ubuntu 14.04 LTS, and a bunch of Mac/Windows/smartPhone systems (different make/model) 
[/LIST]
 After a disruption of the power on the router (router goes off and on), I try to ping the antenna on the 'garage' side (using the Ubuntu fileserver command line), and I get a meaningful return value from it. Because the internet still has not returned to 'normal', meaning either the router has a problem, or the antenna system is not functioning correctly (yet), I tried a ping from one of  the Windows system on the intranet inside the 'office' to the 'garage' antenna which says the system cannot be reached. I checked again and again, Ubuntu ping will get an answer from the fixed address antenna system, but the Windows system will not return an answer.  I thought ping was actually checking the existence of the destination, and waiting/timing an answer, this seems to be not the case? Can ping not be trusted anymore? Is it possible that a ping address is somehow cached inside the Ubuntu fileserver???  Some more details: 
[LIST] 
[*]DHCP pool starts at 100, out of range of the fixed addresses 
[*]A ping on the Ubuntu server will get answer from the 'fake' antenna, but also a correct answer from the local antenna (which is functioning correctly btw). 
[*]The antenna on the 'garage' side is actually not working correctly, and should NOT be answering. 
[/LIST]
  I guess I am missing something here, but I am wondering where to look... Anyone?  - Charlie

---

### Post by bab1 on 2014-08-08
> **Charlie_van_Weert said:**
> Hello all,  I have a very strange network problem, and am still trying to get to some kind of explanation. Maybe some networking guru luring around on this forum can shed some light?  Setup is following: 
[LIST] 
[*]One router DHCP server build into a router 
[*]Antenna system (Ubiquity) bridging a network (calll it 'garage') to another location (call it 'office'), both on fixed addresses 
[*]On the other side of the antenna's: fileserver (fixed IP address) running Ubuntu 14.04 LTS, and a bunch of Mac/Windows/smartPhone systems (different make/model) 
[/LIST]

After a disruption of the power on the router (router goes off and on), I try to ping the antenna on the 'garage' side (using the Ubuntu fileserver command line), and I get a meaningful return value from it. Because the internet still has not returned to 'normal', meaning either the router has a problem, or the antenna system is not functioning correctly (yet), I tried a ping from one of  the Windows system on the intranet inside the 'office' to the 'garage' antenna which says the system cannot be reached. I checked again and again, Ubuntu ping will get an answer from the fixed address antenna system, but the Windows system will not return an answer.  I thought ping was actually checking the existence of the destination, and waiting/timing an answer, this seems to be not the case? Can ping not be trusted anymore? Is it possible that a ping address is somehow cached inside the Ubuntu fileserver???  Some more details: 
[LIST] 
[*]DHCP pool starts at 100, out of range of the fixed addresses 
[*]A ping on the Ubuntu server will get answer from the 'fake' antenna, but also a correct answer from the local antenna (which is functioning correctly btw). 
[*]The antenna on the 'garage' side is actually not working correctly, and should NOT be answering. 
[/LIST]
  I guess I am missing something here, but I am wondering where to look... Anyone?  - Charlie
Ping doesn't directly check for the existence of any host.  It sends a request to the host and if it does not get an answer it declares "Destination Host Unreachable" if you ping by legitimate IP address or "unknown host" if the hostname can't be resolved.  

I'm not the expert in wireless but the device itself as an administrative IP address, so it is a host in the LAN just as any host is as far as ping is concerned.  I have a wireless AP and it has a hostname of bb-ap1 and an IP address of 192.168.1.235.  I can ping by either the hostname of IP address   I assume that the brand name of your equipment is Ubiquiti not Ubiquity.  Am I correct?  So these are most likely just wireless AP's and each should have an IP address and may have a hostname.

depending upon where you are one of these AP's is directly connected to a switch or hub on that side unless there is only the one machine that is used to host the wireless device.  In that case the IP address would be the address of the hosting machine.

It is entirely possible that the Windows machine has no RF connectivity to the machine it is pinging so there is no return.  TheRF is the equivalent of an Ethernet cable.  If you unplug an Ethernet cable from a host you can't ping that host, but the TCP/IP stack could be fine.

Can you assure yourself (and me that the wireless device (antenna) has a RF connectivity between itself and the Windows machine?

What do you get from this command:  *arp -a * on either the Ubuntu host or the Windows host?

I believe you will find the internet connectivity is a function of the gateway device and is not really relevant to this problem.

---

### Post by Charlie_van_Weert on 2014-08-08
Thanks for this fast answer.

Oops for the brandname, it is indeed Ubiquiti.

The ping goes out to an IP numbered address like the default 192.168.1.20 address for the antenna, all of which are wired to the subnet. All relevant connections are wired, except
for the antenna bits. The network is actually quite complex, because of the antenna's and the requirement that all network computers have to be able to reach each other.

Also: yes, internet connectivity is irrelevant, it was just a means of checking whether the network was behaving again.

Little more explanation, the network we are using looks like:

        |Windows
        |Mac             --<cable>-- Switch --<cable>-- Antenna  . . . . . . . .  Antenna --<cable>-- Router --<fiber/cable>-- Internet
        |Server

Sorry for being unclear in my first email, I think I went a bit too fast trying to explain something that has bugged me for over a day now.

I am guessing here, but if a PC or Mac goes into sleep mode, and during that sleep, the power is taken from the DHCP server (the router in the 'garage'), PC wakes up again and
cannot reach the router (DHCP), it would have to stick to its 'old' IP address? Power to the DHCP server it switched on again, but the antenna is still faulty, so both PC/Server
have no way of reaching out to the internet, so there is no reason to change any of the IP parameter/addresses.
Ping wil see an unreachable machine, but what I don't get is why it is different for two platforms. On Ubuntu ping should not see I don't have access to the network right now,
but I certainly will run arp on both platforms, and check the list it comes up with.

---

### Post by bab1 on 2014-08-08
> **Charlie_van_Weert said:**
> Thanks for this fast answer....

The ping goes out to an IP numbered address like the default 192.168.1.20 address for the antenna, all of which are wired to the subnet. All relevant connections are wired, except for the antenna bits. The network is actually quite complex, because of the antenna's and the requirement that all network computers have to be able to reach each other.

Also: yes, internet connectivity is irrelevant, it was just a means of checking whether the network was behaving again.

Little more explanation, the network we are using looks like:

        |Windows
        |Mac             --<cable>-- Switch --<cable>-- Antenna  . . . . . . . .  Antenna --<cable>-- Router --<fiber/cable>-- Internet
        |Server


For any LAN network all hosts need to be on the same subnet (i.e. 192.168.1.0 /45 (255.255.255.0).  I imagine (hope actually) that this is the case.  In fact the devices  ultimately use arp (address resolution protocol) to find the specific interface by MAC address (HDWR ADDR).  The ping goes out on the wire and the IP address is matched to the MAC address and the data stream begins.  That is if the 2 RF transceivers are connected first.  The TCP/IP stack starts with the connection (wired=physical -- wireless = RF transcievers), then you have the link layer (Ethernet) and then you have the addressing layer (ip addressing).  It is like a cake with layers.  You need all threee layers for everthing to work.  BTW -- there are 4 more layers to the complete puzzle.

By your network diagram it looks like all the equipment is in one room and connected by a switch.  The antenna (i'm assuming a wireless bridge (extender) is also connected to the switch.  This wireless bridge talks to the other wireless bridge that is connected to the router and on to the internet.
> 
Sorry for being unclear in my first email, I think I went a bit too fast trying to explain something that has bugged me for over a day now.

I am guessing here, but if a PC or Mac goes into sleep mode, and during that sleep, the power is taken from the DHCP server (the router in the 'garage'), PC wakes up again and cannot reach the router (DHCP), it would have to stick to its 'old' IP address?

Power to the DHCP server it switched on again, but the antenna is still faulty, so both PC/Server have no way of reaching out to the internet, so there is no reason to change any of the IP parameter/addresses.

DHCP supplied IP addresses are *leased* for a specific amount of time and at *_half that time_* The cleint starts requesting a renewal.  Other than that the host (client) never talks to the DHCP server.  The settings are what were supplied.  The internet connectivty can be problematic if the router is off, or the host is behind the antennas and either the RF is bad or the IP addressed interfaces for the antennas are not up.

What happens when the host goes to sleep.  i dunno.  You will have to check that out on that specific host,  In your case you have multiple means of failure and you will have to start with one end or the other of the connection.  When you havee a failuer you can ping the 127.0.0.1 (localhost) address to see if the IP stack is up, then ping the host itself (192.168.1.??) then ping the antenna working your way to the gateway. 
> 

Ping wil see an unreachable machine, but what I don't get is why it is different for two platforms. On Ubuntu ping should not see I don't have access to the network right now, but I certainly will run arp on both platforms, and check the list it comes up with.
Your explanation is confusing to me.  Like I said, start at one end and see if you can ping other devices such as the localhost, your machines Ethernet interface. some other host and then the near side antenna.  do both hosts work this way?  Is there a way to see if both the Ubuntu and Windows machines are RF connected?  Are the 2 antennas connected?

You have at least 3 variables that can be wrong and maybe more.  We have to confirm good each one of them.

---

### Post by Charlie_van_Weert on 2014-08-10
Thanks again :)

"The mist is rising" .. a bit...

- Yes, all machines are on the same network, as long as the DHCP server (router) is working/within reach.
- No, the antenna on the 'garage' side is **not** connecting due to a power failure.

It is confusing on my side as well, the network has been fully functioning for a long time now, and I am now figuring out what went wrong and how to prevent it, or detect it.
My confusion started the moment an Ubuntu machine, within the same 192.168.1.x network, send a ping to a non-functioning antenna, and gets an answer back.
I do the same ping on a Windows machine, just started up, and because of the unreachable DHCP server, is **not** on the same network, default network address for Windows (a 169.x.x.x  if I remember right),
and does not get an answer from the non-functioning antenna. Ping on windows is correct, ping on Ubuntu is incorrect (or at least not reliable).

Hope this helps clarify things a bit, and I will also collect some arp info when I am back and logged into the network again.

---

### Post by bab1 on 2014-08-11
> **Charlie_van_Weert said:**
> Thanks again :)

"The mist is rising" .. a bit...

- Yes, all machines are on the same network, as long as the DHCP server (router) is working/within reach.
- No, the antenna on the 'garage' side is **not** connecting due to a power failure.

It is confusing on my side as well, the network has been fully functioning for a long time now, and I am now figuring out what went wrong and how to prevent it, or detect it.
My confusion started the moment an Ubuntu machine, within the same 192.168.1.x network, send a ping to a non-functioning antenna, and gets an answer back.
I do the same ping on a Windows machine, just started up, and because of the unreachable DHCP server, is **not** on the same network, default network address for Windows (a 169.x.x.x  if I remember right),
and does not get an answer from the non-functioning antenna. Ping on windows is correct, ping on Ubuntu is incorrect (or at least not reliable).

Hope this helps clarify things a bit, and I will also collect some arp info when I am back and logged into the network again.
Part of the problem is the 169.254.x.x network.  This is not the default network.  It's more like the network of last resort.  It is part of a protocol to provide a local network IP address when the machine does not have access to a DHCP server or is not configured with a fixed IP address via a conf file.  See [here]("http://ask-leo.com/why_cant_i_connect_with_a_169254xx_ip_address.html") for a simplified description.

So it seems that when the DHCP server is down the the host you are pinging configures itself to a 169.254.x.x address and can be pinged locally.   This just shows the limits of what PING really is.  Ping only says "are you there?" and of course it is.

What are the exact ping commands?  Are you using the hostname (e.g. ping some-name) or are you using a known IP address (e.g. ping  192.168.1.x)?

So far nothing is inconsistent with the correct operation of ***ping*** itself.

---

### Post by The Cog on 2014-08-11
If your windows machine assigns itself an address on 169.254.x.x then it will not be able to ping 192.168.1.x - they are different network numbers and they need a router to route between them. But I doubt that your router has an interface on 169.254.

You can check the IP address of the windows machine with the command **ipconfig**. You can check the ubuntu ip address with the command **ifconfig**.

From the sound of it, I think maybe the DHCP server is slow in restarting and not handing out addresses soon enough, so the windows machine defaults to 169.254.x.x, which is neither use nor ornament. From then on, it will not be able to talk to anything on 192.168.1.x and will not be able to talk to the internet because the router is on 192.168.1.x. The ubuntu machine continues to use the proper 192.168.1.x address and therefor can talk to other devices on 192.168.1.x, including the wireless antenna which you are assuming is non-functioning because the windows machine can't ping it.

Ping is not unreliable, on either windows or ubuntu. 

Incidentally, if you reboot the DHCP server it will probably forget all the DHCP allocations it has previously assigned, and may well hand out addresses that are already in use. Just another problem to watch out for.

---

### Post by Charlie_van_Weert on 2014-08-11
Thanks both, I think I am beginning to see light in the darkness... I have no control of the 'non-functioning' antenna, if it is dead (for whatever reason), I cannot restart it.
I agree, a bad situation, but not much to do about it. I would have to wake up someone to switch it off and on.
It is beginning to look like the DHCP server in the router is coughing up some network problems. Maybe we should go for an actual pro version...

Thanks again for helping out, my trust in ping is restored, but as always, you have to know how to use it. This goes simple as well as pro tools...

---

### Post by bab1 on 2014-08-11
> **Charlie_van_Weert said:**
> Thanks both, I think I am beginning to see light in the darkness... I have no control of the 'non-functioning' antenna, if it is dead (for whatever reason), I cannot restart it.
I agree, a bad situation, but not much to do about it. I would have to wake up someone to switch it off and on.
It is beginning to look like the DHCP server in the router is coughing up some network problems. Maybe we should go for an actual pro version...

Thanks again for helping out, my trust in ping is restored, but as always, you have to know how to use it. This goes simple as well as pro tools...
The router doesn't supply the 169.254.x.x number.  The computer that can't get an address from the router configures itself with that number.  To me it just tells me either the router is down or the route to the router is down.  Not that the router itself is bad.

---

### Post by The Cog on 2014-08-12
Bab1 is right. If the suspect antenna is between the windows PCs and the router, it is possible that the antenna takes a long time to recover - long enough for the windows PCs to give up on DHCP and autoconfigure themselves with 169.254.x.x. But that it's working again by the time you come to investigate by doing pings.

It may be difficult to work out whether it's the antenna or the router that's slow to recover.

---

