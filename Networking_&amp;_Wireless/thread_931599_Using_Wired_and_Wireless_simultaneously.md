---
title: "Using Wired and Wireless simultaneously"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by disigma on 2008-09-27
Hi,

I have 2 broadband connections in my house and I use a wired one mainly for internet access or large downloads and the wireless one is available when I want.

However, I need to be connected to both simultaneously, as the wired connection provides good stable direct access through the router and I need to access the wireless to share various folders in my home network for others to access as well as play various games on the wireless networks (whom other users use for network play).

To clarify, I have 2 separate routers, wired and a wireless one both offering internet access, and I need to connect to both not one, which the network manager applet will not allow me to do, it gives me a choice to use wired, or the various wireless it finds in the area.

I hope someone can help. Many Thanks.

---

### Post by jheaton5 on 2008-09-27
you might try getting a wireless router with a multi-port(e.g.4 port) switch. With this device you can connect to the router by cable and communicate with your wireless peers.

---

### Post by Iowan on 2008-09-27
You can bypass Network Manager by editing the **/etc/network/interfaces** file directly.  Add an "auto" line to whichever interface currently doesn't boot (which is to say - both wired and wireless interfaces should have an "auto" line - or you can put them both on one... eg **auto eth0 wlan0**).

---

### Post by whitepony20054545 on 2008-10-01
Have roughly th same problem [http://ubuntuforums.org/showthread.php?t=934387]("http://ubuntuforums.org/showthread.php?t=934387") but not using 2 internet connections. i have wireless for internet and a wired connection to an xbox360 for media sharing. i have looked at the /etc/network/interfaces file which only contains 2 lines. 
> auto lo
iface lo inet loopback

bit of a noob so correct me if i'm wrong but the auto lo command is for my wired connection so adding an auto wlan line will work??? 
would like to know before i mess things up.

---

### Post by VorDesigns on 2008-10-01
Configure the wirless connection with no gateway; the gateway is the outbound path.  Network straddling for clients has always been problematic but not impossible to implement.
You will need local routes on the client to deal with splitting the traffic and to minimize bleed which is common, at least in Win32 based server systems.  I don't have enough experience with Linux networking to make a more concise recommendation.
Configure the hardwired Internet connection with a route back to the wireless NIC connection for any errant traffic that may bleed through.
## Example 1:
NIC 0:  wired, 172.16.254.100/255.255.255.0, gateway 172.16.254.1
NIC 1:  wireless, 192.168.254.100/255.255.255.0, no gateway
Scenario:  NIC 1 tries to get something from a host on the NIC 1 network at 192.168.254.101 but, the host is turned off and therefore unavailable on the NIC 1 network.  The NIC 1 network has no gateway so it bridges the call through the NIC 0 network this is bleed.

## Example 2:
NIC 0:  wired, 172.16.254.100/255.255.255.0, gateway 172.16.254.1
NIC 1:  wireless, 192.168.254.100/255.255.255.0, no 192.168.254.1
NIC 1 establishes a connection with a host on the WAN through the default gateway for NIC 1 at 192.168.254.1.  During interraction, the socket closes for some reason before the transaction completes.  NIC1 attempts to reconnect via the default gateway but fails.  NIC 1 fails the NIC 1 gateway and now tries to reconnect via the NIC 0 gateway which succeeds; now you have a failed gateway condition on NIC 1 and from that point on, until you reboot, traffic for NIC 1 will bleed through to the NIC 0 network.

At least, that is what I have observed on Win32 networks.  Part of the problem, to my interpretation is that only one network stack exists and runs for all network interfaces and so there is a low level bridge at the OS level and no proper, configurable isolation settings to stop just this type of issue.

---

### Post by whitepony20054545 on 2008-10-01
ok so i went ahead and edited the interfaces file. it now says 
> auto lo
iface lo inet loopback 
auto wlan0
ok so i can still use wired or wireless. and it does automatically connect to the wireless when i turn the xbox off. but i still have to disconnect from wireless to stream music to xbox and vice versa for internet. is there any way i can have 2 network managers (one for each connection) or is that just a stupid idea

---

### Post by Iowan on 2008-10-01
> **whitepony20054545 said:**
> bit of a noob so correct me if i'm wrong but the auto lo command is for my wired connection so adding an auto wlan line will work??? . The "lo" is the loopback device, not the wired connection.  There *should* be an "auto eth0" in there, too... but it'd be a shame to mess up a working system...

---

