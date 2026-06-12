---
title: "Adding Fixed IP Address not on Existing Subnet"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by jsland on 2014-01-13
Am needing to bench test a server or host which has a fixed IP address.  It's a big hassle to change the IP address of the device being tested.

LAN used for bench testing has a .1 subnet while the device to be tested has a .0 octet.

In terminal, what command strings can be used to allow the .0 host to be reached by an Ubuntu desktop on the .1 LAN.

---

### Post by TheFu on 2014-01-13
If you must change the IP, then I would create 2 /etc/network/interface files, then just swap in which ever you want "live" and restart the network.

Or you could put the same host on both networks. [http://ubuntuforums.org/showthread.php?t=1228044](http://ubuntuforums.org/showthread.php?t=1228044) has a command to add the other IP. This assumes both the host and the device are connected to a layer 2 switch that isn't too smart.

---

### Post by jsland on 2014-01-13
No IP addresses are to be changed.  That is the reason for the post.

Setting up the ability to see 192.168.0.* devices or hosts on the existing 192.168.1.*/24 subnet is what is being asked.  There is no need for WAN access only temporary LAN.

---

### Post by houstonbofh on 2014-01-13
You mean like this?

```
ifconfig eth0 192.168.1.102 netmask 255.255.255.0 broadcast 192.168.1.255
```

Note that it will clobber your existing settings.  You may want to look at multinetting.

---

### Post by TheFu on 2014-01-13
> **jsland said:**
> No IP addresses are to be changed.  That is the reason for the post.

Setting up the ability to see 192.168.0.* devices or hosts on the existing 192.168.1.*/24 subnet is what is being asked.  There is no need for WAN access only temporary LAN.

Did you click that link provided? It has the answer.

---

### Post by jsland on 2014-01-13
Link in original post was looked at.

Am still uncertain about using ifconfig to add access to the .0 addressed device.  Wiping out existing settings on the LAN is a concern.  If a simple reboot would clear up any corrupted network settings then I could see doing some trial and error.  
 
    ifconfig eth0 192.168.1.102 netmask 255.255.255.0 broadcast 192.168.1.255

If a subnet mask of /24 only covers IP changes to the final octet of the address then a netmask of 255.255.255.0 does not seem completely right to me.  The new subnet requires the 3rd octet to change.

Looking in advanced settings for the Linksys modem/router seemed a logical place for reconfiguring the LAN as it contains the routing table.  I was unable to find a way for the router to add addresses in the .0 subnet although it said it could take up to 20 new addresses.

Point to point contact from one MAC address to another, using a brower, is what is trying to be set up.  It seems this should be rather common and fairly easy but my knowledge is not yet good enough for any network settings outside the /24 netmask range the router wants to work in. All I would like to do is add to the routing table the .0 addresses.  With no need for WAN access the router is essentially only a switch.

---

### Post by bab1 on 2014-01-13
> **jsland said:**
> Link in original post was looked at.

Am still uncertain about using ifconfig to add access to the .0 addressed device.  Wiping out existing settings on the LAN is a concern.  If a simple reboot would clear up any corrupted network settings then I could see doing some trial and error.  
 
    ifconfig eth0 192.168.1.102 netmask 255.255.255.0 broadcast 192.168.1.255

If a subnet mask of /24 only covers IP changes to the final octet of the address then a netmask of 255.255.255.0 does not seem completely right to me.  The new subnet requires the 3rd octet to change.

The subnet mask separates the network ID from the host IP addresses.  The network of 192.168.0.0 /24 means the first 24 bits (positions) in the address are reserved for the 192.168.0 part.  There are 255 individual host IP addresses in this network.  The 192.168.1.0 /24 is the same as far as setup but they are 2 distinct IP networks (e,g. [COLOR="#FF0000"]192.168.0[/COLOR] vs [COLOR="#0000FF"]**192.168.1**[/COLOR]).  They are not the same.  If you wanted to have one big network the subnet mask would be 255.255.[COLOR="#008000"]**254**[/COLOR].0. This would have the notation of 192.168.0.0 /23 and would have 510 IP addresses allocated for hosts.
> 

Looking in advanced settings for the Linksys modem/router seemed a logical place for reconfiguring the LAN as it contains the routing table.  I was unable to find a way for the router to add addresses in the .0 subnet although it said it could take up to 20 new addresses.
/[QUOTE]
This doesn't sound right at all.  What is the model # of the router.0
[QUOTE]

Point to point contact from one MAC address to another, using a brower, is what is trying to be set up.  It seems this should be rather common and fairly easy but my knowledge is not yet good enough for any network settings outside the /24 netmask range the router wants to work in. All I would like to do is add to the routing table the .0 addresses.  With no need for WAN access the router is essentially only a switch.

These are not point to point connections at all.  You can't add random addresses to the network.  It makes more sense if you look at it using binary notation.  Reading the addresses as decimal is a concession to our human brains.

You have 3 choices really.  You can temporarily assign an IP address in the existing IP network to your test host or you can route the TCP/IP packets from one network to another (via the routing table in your router) or you can expand the size of the IP network to encompass all the hosts by resetting the subnet mask to 255.255.254.0 (23 bits of masking instead of 24 bits).  If you choose the last option you need to set the subnet mask in all the hosts and the router for them to be able to communicate.

---

### Post by jsland on 2014-01-14
*Looking in advanced settings for the Linksys modem/router seemed a logical place for reconfiguring the LAN as it contains the routing table.  I was unable to find a way for the router to add addresses in the .0 subnet although it said it could take up to 20 new addresses.*

> This doesn't sound right at all.  What is the model # of the router.0

*Router .1 is Linksys WRT54GL.  Word 'addresses' above should read 'routes'.* 

 >   It makes more sense if you look at it using binary notation. 

This is starting to become clearer thanks to your description.  The /32,/31... sequence was understood before but now makes more sense in how the network is operating.  My take is math students in the future will have it easy.  The only numbers you have to know will be 1 and 0. :)

>   
You have 3 choices really.  You can temporarily assign an IP address in the existing IP network to your test host or you can route the TCP/IP packets from one network to another (via the routing table in your router) or you can expand the size of the IP network to encompass all the hosts by resetting the subnet mask to 255.255.254.0 (23 bits of masking instead of 24 bits).  If you choose the last option you need to set the subnet mask in all the hosts and the router for them to be able to communicate.

Of the 3, for the task at hand, the best option is #2.

So now I need to set up a new network.  The .0 one and route the packets to and from the existing .1 network.

Heading back to the WRT54GL and trying to add the new network in the Advanced Routing section I strike out just as I did this morning.  It gives me an error with the following settings.
  STATIC ROUTING:
     Select Set #:     1      (up to 20 may be added)
     Name:             .0 Network
     Destination IP:    192.168.0.114     (bench test host)
     Subnet Mask:     255.255.225.0     (the ususal)
     Default Gateway:     192.168.1.1    (not sure with this)
     Interface:               LAN & Wireless

OK, so just took another swing using Destination IP 192.168.0.0 and the router accepts the address.
Routing Table shows the new Destination IP but now I think the gateway may be wrong and should be 0.0.0.0 instead.  My understanding of gateway is to think of it as where the LAN meets the WAN.  Routing table for Destination IP on the original network 192.168.1.0 shows a Default Gateway of 0.0.0.0.  It would be logical to expect the new network 192.168.0.0 to have this same table entry.

---

### Post by jsland on 2014-01-14
Default Gateway was first changed to 0.0.0.0 in routing table.  Host is now found on the network.

Thank you bab1, TheFu and houstonbofh.


Host being tested is a small server housed in an Arduino sized case.  It allows a smartphone to open and close a gate and originally was designed for running up to 4 garage doors.  Last week a new relay was soldered on the board along with a transistor and flyback diode.  The new circuit will be used for turning off/on an IP camera that has a heater in it.  During extended cloudy periods during the shortest days of the year the camera may need to be shut down to conserve battery as the gate is PV powered with no connection to the grid.  The battery charge controller for the gate is IP capable so the batteries are monitored using a WiFi radio.

---

### Post by bab1 on 2014-01-14
Glad you got it working.  The 0.0.0.0 means any address (all addresses).  So what this is what route says: any packet sent to 192.168.0.114 can be sent to all of the local ports (4 of them for the LAN).  The built in Ethernet switch handles the rest.

[COLOR="#0000FF"]Edit:  This is an elegant way of solving the problem.  I don't like hacks, this is the proper way of doing this.[/COLOR]

---

