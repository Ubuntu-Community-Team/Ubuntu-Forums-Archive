---
title: "How to identify a particular device on a lan"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2014-02-15
nmap will give you a list of all devices connected to your lan, but the information provided falls short of a way to tell which device is which.

Is there a way to ping (or another command) each listed IP# and get back information that will reveal this?

---

### Post by steeldriver on 2014-02-15
What information are you looking for exactly? nmap will *try* to probe for OS information if run with the -A switch e.g. something like

```
sudo nmap -A -T4 192.168.1.0/24
```

Alternatively you can probe and list services if that helps

---

### Post by Odyssey1942 on 2014-02-15
Yes, that is the code which I used and it shows 17 devices. I want to figure out what each of them are. 
I have the IP#'s of all the computers and the AIO, but things like the TV or the Roku or a Satellite box etc are not as easy to find, and if I can do so from one of the computers, ideally quickly, that is what I want to use.

---

### Post by steeldriver on 2014-02-15
Well what attribute do you expect to distinguish them by? If there are particular services running on one machine versus the others you could do a port scan and decide based on open ports/services

OTOH if you are just trying to find hosts by (.local) name then you could try the avahi tools (avahi-discover / avahi-browse ?)

---

### Post by Odyssey1942 on 2014-02-15
Not sure I understand your question. I want to know what each device is. If for no other reason, I want to know if there is anything (anyone) on my lan that I don't want on there.

---

### Post by tgalati4 on 2014-02-15
Normally you would install an identifer service on each machine then run an application that talks to that service and you will get back very detailed information.  Landscape is such a service.

tgalati4@Mint14-Extensa ~ $ apt-cache search landscape
landscape-client - The Landscape administration system client
landscape-client-ui - The Landscape administration system client - UI configuration
landscape-client-ui-install - The Landscape administration system client - UI installer

Since you can't run Landscape on your Roku, you have to be clever.  Many streaming devices have uPnP or DNLA and there are tools to query those:

tgalati4@Mint14-Extensa ~ $ apt-cache search dlna
gir1.2-gupnp-dlna-1.0 - transitional dummy package
gir1.2-gupnpdlna-1.0 - GObject introspection data for the DLNA utility library for GUPnP
gupnp-dlna-tools - GObject-based library for GUPnP DLNA (tools)
libdlna-dev - development files for libdlna
libdlna0 - DLNA codec library
libgupnp-dlna-1.0-2 - DLNA utility library for GUPnP
libgupnp-dlna-1.0-dbg - DLNA utility library for GUPnP (debug symbols)
libgupnp-dlna-1.0-dev - DLNA utility library for GUPnP (development files)
libgupnp-dlna-doc - DLNA utility library for GUPnP (documentation)
librygel-core-1.0-0 - GNOME UPnP/DLNA services - core library
librygel-renderer-1.0-0 - GNOME UPnP/DLNA services - renderer library
librygel-server-1.0-0 - GNOME UPnP/DLNA services - server library
minidlna - lightweight DLNA/UPnP-AV server targeted at embedded systems
rygel - GNOME UPnP/DLNA services
rygel-1.0-dev - GNOME UPnP/DLNA services - plugin development files
rygel-dbg - GNOME UPnP/DLNA services
rygel-gst-launch - GNOME UPnP/DLNA services - gst-launch plugin
rygel-mediathek - GNOME UPnP/DLNA services - Mediathek plugin
rygel-playbin - GNOME UPnP/DLNA services - GStreamer Media Renderer plugin
rygel-preferences - GNOME UPnP/DLNA services - preferences tool
rygel-tracker - GNOME UPnP/DLNA services - Tracker plugin
**upnp-inspector - Python UPnP framework analyser**

For other devices like routers and IP video cameras, you need to know what ports are used to communicate (left open) and ping those with the port switch.

A simple way to enforce your network is to use MAC filtering  on your router and put together a MAC list for each device.  Then, any device not on the list won't get access.  It's easy to spoof a MAC address, but it will keep the casual dingleberries off of your network.

---

### Post by Odyssey1942 on 2014-02-15
tgalati4, this is to say thanks, but I fear that it mostly went over my head (beginner and all, you understand).

I will wait awhile to see if anything else, but may restart this in the network forum.

---

### Post by tgalati4 on 2014-02-15
Sorry, I only speak geek.  Read this post in a year.

---

### Post by bab1 on 2014-02-16
> **Odyssey1942 said:**
> ...I fear that it mostly went over my head (beginner and all, you understand).

If you don't understand then I would suggest that you take a manual inventory of the assets you placed (and manage) in the network.  If you know the IP address, MAC address and hostname of all of those, any others would be an intruder.  You can run nmap in a GUI environment.  It's called zenmap.  You might try running a quick search to locate the various hosts and the above data. 
> 

I will wait awhile to see if anything else, but may restart this in the network forum.

Don't repost this anywhere else in the forum.  There is no need to duplicate the post.  Just click on the "Report Abuse" icon at the lower left and ask the forum moderators to move this thread to where you want it.

---

### Post by Odyssey1942 on 2014-02-16
Bab. Thanks for yours, and the tip on zenmap which I installed and ran. It gives more info than the nmap command in the terminal did.

However, what I am trying to achieve and am rapidly concluding (since no one seems to offer a solution) that one cannot achieve, is to use the lan to gather the information that you are suggesting that I gather manually. I recognize that I can walk around, make a list of all connected devices and ATTEMPT to determine the IP# etc, but this is a very time consuming exercise since it is usually not quickly evident what the IP# is (must get out manuals, etc). Doable, yes but time consuming, yes.

So I was hoping that my computer could be used to do the walking for me, and do it quickly. Looks like that was a vain hope.

BTW, was not thinking of double posting, rather moving as you suggest. That is what I meant by "restart" but perhaps an unfortunate choice of words.

---

### Post by Elfy on 2014-02-16
> Just click on the "Report Abuse" icon at the lower left and ask the forum moderators to move this thread to where you want it. That works then :p

---

### Post by bab1 on 2014-02-16
> **Odyssey1942 said:**
> Bab. Thanks for yours, and the tip on zenmap which I installed and ran. It gives more info than the nmap command in the terminal did.

However, what I am trying to achieve and am rapidly concluding (since no one seems to offer a solution) that one cannot achieve, is to use the lan to gather the information that you are suggesting that I gather manually. I recognize that I can walk around, make a list of all connected devices and ATTEMPT to determine the IP# etc, but this is a very time consuming exercise since it is usually not quickly evident what the IP# is (must get out manuals, etc). Doable, yes but time consuming, yes.

So I was hoping that my computer could be used to do the walking for me, and do it quickly. Looks like that was a vain hope.

BTW, was not thinking of double posting, rather moving as you suggest. That is what I meant by "restart" but perhaps an unfortunate choice of words.
It is always better to document your network as you install the various devices.  Nmap (Zenmap) uses a series of tools to poll the various hosts (devices) for that same information.  The tools you really need are *PING * and *ARP*.  What do you get with this command```

arp -a

```...that should list all active devices on the network.  Here is what I get on a pretty quiet network today```

arp -a 
bb-ap1 (192.168.1.245) at 00:14:bf:7d:d5:0a [ether] on eth0
bb-hp1 (192.168.1.200) at 00:01:e6:6b:9f:90 [ether] on eth0
ventura (192.168.1.5) at 00:a0:cc:37:9d:8e [ether] on eth0
bb-gw1 (192.168.1.1) at 00:0f:db:b5:44:d8 [ether] on eth0

``` 
What do you get with this command```

ping - b -c2 192.168.1.255

```...this is a ping of the broadcast address of your network.  All devices that respond to ICMP pings should respond.  Here is what I get for this command```
ping -b -c2 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.500 ms
64 bytes from 192.168.1.245: icmp_req=1 ttl=64 time=0.876 ms (DUP!)
64 bytes from 192.168.1.200: icmp_req=1 ttl=64 time=6.00 ms (DUP!)
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.485 ms

--- 192.168.1.255 ping statistics ---
2 packets transmitted, 2 received, +2 duplicates, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.485/1.967/6.007/2.337 ms

```...Note that there is no IP address for the host named ventura listed.  I had to manually ping that host ( ping ventura) to make it active and then it would show up in the ARP cache (shown by arp -a).  

At this point you should have most of the network assets documented as far as their IPv4 and MAC addresses.  I'm sure you can cut down on the sifting through the manuals and old documentation.  Ask more questions if you need to.
 
I'm curious as to why you feel that you might have network intruders (leaches). Have you had problems in the past?

---

### Post by Odyssey1942 on 2014-02-18
Bab1,

Still working on this but not making much headway.

```
robert@i3-2120:~$ sudo arp -a
sudo] password for robert: 
router.xyz.com (192.168.0.1) at macaddress [ether] on eth0
robert@i3-2120:~$ 
```
Looking at yours, should I be expecting more information?

---

### Post by Dennis N on 2014-02-18
To identify IP address of A, why not just disconnect A at the router (or turn off A) and see what IP address is dropped from the scan?

In the future, if not already, use static IP addresses for wired devices. This can be sometimes be done from the router interface depending on make of router.

---

### Post by ian-weisser on 2014-02-18
> **Odyssey1942 said:**
> Is there a way to ping (or another command) each listed IP# and get back information that will reveal this?

Not in human-readable form.

Query tools like arp or nmap will generally return only the IP address, MAC address, active ports, and (sometimes) hostname.
But you shouldn't even need those - your router maintains the definitive list of active systems on it's LAN. Simply log into your router.

As the other posts have mentioned, one of those little tasks of the human network admin is to keep the list of which MAC addresses are installed on which machines. The system simply does not have the ability to do it for you. It doesn't know what those systems on the LAN are, either. It merely exchanges packets with them when told to. And would you really want your system telling strangers what it is whenever they ask? "I'm an Ubuntu Desktop. I probably have my owner's banking passwords. Hack me first"

On my LAN, for example, I track everything by MAC address. I used to have a little script that logged into my router, downloaded that list, and checked it against my whitelist of MAC addresses...before i changed routers.

---

### Post by Odyssey1942 on 2014-02-18
Thanks for two very helpful posts. Question;
> In the future, if not already, use static IP addresses for wired devices.

I assume that one cannot control this at the router. Would this be done at the device level?

---

### Post by Dennis N on 2014-02-18
> I assume that one cannot control this at the router. 

I would check and see. Most routers have a HTML interface you can view with the web browser. You have to check with the documentation to see what it is. A netgear router can be seen at:

[http://www.routerlogin.net/](http://www.routerlogin.net/) (only works from the LAN)

This could be a numerical address on other routers.

---

### Post by SeijiSensei on 2014-02-18
You should be able to use the router's configuration tool (try [http://ip.of.your.router](http://ip.of.your.router)) to designate a portion of the local address space to be allocated by the router's DHCP server with another portion of the block left unassigned.  You should be able to tell the DHCP server to use, say, addresses starting at .100, leaving the addresses from .1 to .99 unallocated.  Use that range to select addresses for static devices like servers, printers, etc.

---

