---
title: "DHCP to internet + static private IP (to printer)"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by miamicanes on 2007-09-19
How do you set up a computer's networking so that it belongs to two different networks:

* A local one, with non-routable private IP addresses (say, 192.168.100.xxx) and a fixed IP address within that network

* A public one, with dynamic IP address furnished via DHCP (along with DNS and gateway)

... ensuring that the computer knows that when it needs to send data to another host in the 192.168.100.xxx network, it should send it directly instead of trying to route it through the default gateway?

---

### Post by noob12 on 2007-09-19
Are you having a specific problem?  Because the routing should just work in this case.

Normally you will get a regular route for each of the networks you are on when the interface is brought up. If it is sending data to any address where the address is on the same subnet as one of your interfaces, it should just use that interface automatically.  It shouldn't even try the default route unless it can't find a route that actually applies to the address it is trying to reach.

---

### Post by miamicanes on 2007-09-19
OK, let's try something a little more basic: how do I configure the laptop's internal ethernet adapter so it has a static IP address of 192.168.100.69, and additionally acquire an IP address via DHCP upon booting up?

---

### Post by noob12 on 2007-09-19
Looking at this again I may have been confused about your request.   But I'm going to hope I'm not.

Do you have only one physical ethernet interface or two?  If you have two it is easy.  If you have one, I'm not sure how you would do this at all.

For the case of two, let's say the public one is eth0 and the private one is eth1, and there are no other interfaces on the box you would edit your **/etc/network/interfaces** file to look like this:

```

auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.100.69
netmask 255.255.255.0

```

Lots more information can be obtained by typing **man interfaces**.

You will get your DNS servers and default gateway via DHCP.  You can control this to great extent using the **/etc/dhcp3/dhclient.conf** file (**man dhclient.conf** for details).

When you run this way and type  [B]route -n[/B you should see routes that include the following for the internal net 
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
...
192.168.100.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1

```
as well as a route that has a 0.0.0.0 in the first column, UG in the flags column, and eth0 in the last column, and the gateway that you got assigned via DHCP in the second column.

Traffic destined for the 192.168.100.0/255.255.255.0 net will use eth1 and go there.  Traffic that is not destined for that net (and not to your own eth0 address or the loopback net)  will go out of eth0 and out to the world.

---

### Post by miamicanes on 2007-09-19
Yeah, I'm talking about binding two addresses to a single ethernet interface.

Hmmm... from the last time I really had to dig in and do something like this (~8 years ago, when 2.4 was still considered to be "recklessly experimental" and Redhat installed 2.2 by default), I vaguely remember a rule that I could bind 255 IP addresses per physical card. I also vaguely remember something (IPchains?) that allowed you to set up all kinds of arbitrary routing rules. But as much as I hate to admit it, I feel like just about everything related to networking under Linux has changed radically since that time (let me put it this way: I spent a week in 1998 getting an ancient laptop running Slackware with 2 PCMCIA ethernet cards to work as my first NAT router using pump and IPchains after finally getting DSL... it wasn't fun. I spent 5 days of the week trying to get it to work with one ethernet card, before throwing in the towel and adding a second one).

---

### Post by noob12 on 2007-09-20
Oh.  You can do that, but it only makes sense on a physical network where you have a single cable carrying the traffic of all of the logical nets involved.  I don't think that's the case you have is it?

---

### Post by miamicanes on 2007-09-20
Here's the setup:

10/100 switch, connected to:

* ethernet jack in wall that ultimately leads to office LAN
* JetDirect card attached to printer
* Notebook running Ubuntu 7.04

---

### Post by noob12 on 2007-09-20
Sorry I'm still not getting this.  (Might be me.)

In a typical case you'd just assign a static IP for the printer on the same logical net as your LAN, then just plug your Ubuntu host in and have its address configured by DHCP.  The printer would be accessible from all points on the LAN with queues managed independently.

Another typical case is that you want to manage the queue through printing service on the Ubuntu host.  But unless you are really worried about users going directly to the printer, you shouldn't need to put it on its own subnet.  Just configure one static IP on your Ubuntu host and point other printing clients to point to the printing service port on your host rather than the printer.

You want the printer on its own isolated net?

---

