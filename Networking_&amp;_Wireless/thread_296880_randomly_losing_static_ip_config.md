---
title: "randomly losing static ip config"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by pataphysician on 2006-11-10
i have a file server running dapper. it has a static ip and i've manually set  dns and gateway addresses. randomly, about twice a week, it loses all or part of that. generally, either the ip or gateway will change. i'm assuming - but i could be wrong - that something is causing it to try to renew its (non-existent) lease with the dhcp server, which in turn gives it new addresses.

assuming this is the case, how can i stop the dhcp client service from running? alternately, if you think something else may be the problem... well, how do i fix that?

not sure if it matters but /etc/network/interfaces looks like this

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.21.24
        netmask 255.255.255.0
        route add default gw 192.168.21.1
        dns-nameservers 192.168.20.101


```

---

### Post by maerlma on 2007-07-19
I'm having the same problem with Fiesty. It's my mythbox.

---

### Post by Hei Ku on 2007-07-24
I have the same problem.
It was running ok until a couple of weeks ago I tried the dhclient command to help someone with a problem. Now I have my pc lose its connectivity and lease a DHCP address, even if the interfaces file says it has a static address.
The most weird thing is that if I try to set it correctly in knetworkmanager, when I apply the changes, the address changes to the leased dhcp address, but still as a static address.
I have to do it 4 or 5 times until knetworkmanager recognizes the changes and applies correctly.

btw, all the time, the interfaces file has the correct configuration. No changes there, so it has something to do with knetworkmanager.

---

### Post by Hei Ku on 2007-07-25
This is what I get on my daemon.log when I lose connection.

> Jul 25 22:11:12 maverick avahi-autoipd(eth0)[31103]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 118).
Jul 25 22:11:12 maverick avahi-autoipd(eth0)[31103]: Successfully called chroot().
Jul 25 22:11:12 maverick avahi-autoipd(eth0)[31103]: Successfully dropped root privileges.
Jul 25 22:11:12 maverick avahi-autoipd(eth0)[31103]: fopen() failed: Permission denied
Jul 25 22:11:12 maverick avahi-autoipd(eth0)[31103]: Starting with address 169.254.5.95
Jul 25 22:11:18 maverick avahi-autoipd(eth0)[31103]: Callout BIND, address 169.254.5.95 on interface eth0
Jul 25 22:11:22 maverick avahi-autoipd(eth0)[31103]: Successfully claimed IP address 169.254.5.95
Jul 25 22:11:22 maverick avahi-autoipd(eth0)[31103]: fopen() failed: Permission denied
Jul 25 22:11:22 maverick avahi-autoipd(eth0)[31103]: Got SIGTERM, quitting.
Jul 25 22:11:22 maverick avahi-autoipd(eth0)[31103]: Callout STOP, address 169.254.5.95 on interface eth0
Jul 25 22:11:22 maverick avahi-autoipd(eth0)[31104]: client: RTNETLINK answers: No such process
Jul 25 22:11:23 maverick dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jul 25 22:11:24 maverick dhclient: DHCPOFFER from 192.168.1.1
Jul 25 22:11:24 maverick dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jul 25 22:11:24 maverick dhclient: DHCPACK from 192.168.1.1
Jul 25 22:11:24 maverick dhclient: bound to 192.168.1.101 -- renewal in 41269 seconds.

---

### Post by gangolli on 2007-07-25
Try removing or renaming /etc/dhclient-eth0.conf.  Then reboot or restart networking.

It appears that /sbin/ifup will start dhclient if this file exists for the interface, regardless of whether you have static in the /etc/network/interfaces file.

---

### Post by gangolli on 2007-07-25
Ignore my last posting.  I was looking at my Fedora box!  Boo!

---

### Post by Hei Ku on 2007-07-26
I found that conf file in /etc/dhcp3/
I renamed it, just in case. I will see what happens and let you know.

---

### Post by gangolli on 2007-07-27
Yeah, this strongly suggests that dhclient is getting started by something.
> 
Jul 25 22:11:23 maverick dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jul 25 22:11:24 maverick dhclient: DHCPOFFER from 192.168.1.1
Jul 25 22:11:24 maverick dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jul 25 22:11:24 maverick dhclient: DHCPACK from 192.168.1.1
Jul 25 22:11:24 maverick dhclient: bound to 192.168.1.101 -- renewal in 41269 seconds.


I'd also rename the .leases state file.   Then see if dhclient gets started at all on the next reboot or the next restart of networking.

---

### Post by gangolli on 2007-07-27
By any chance does either of you have a second interface that is being configured using DHCP?  

I'm trying to understand why dhclient is getting started at all.

---

### Post by Hei Ku on 2007-07-28
I only have one inteface. At least thats what shows up in networkmanager. I had wireless enabled, which I disabled now, because I have no wireless network card.

---

### Post by swampdweller on 2007-07-28
I notice that the DHCP server at 1.1
is not your default gateway (21.1).

Now this is a bit of a longshot, but is it possible
that by times the gateway (21.1) becomes inoperable?

I have found on my Feisty that if the gateway
doesn't pan out, it drops my static IP and
asks for a dynamic one.

---

### Post by Hei Ku on 2007-07-28
Actually, 21.1 is the gateway of the original poster. I kind of hijacked this thread by adding more details. My gateway and dhcp server are the same (a linksys router), so that doesnt seem to be the problem.

---

### Post by noob12 on 2007-07-28
Does  **ps -ef | grep dhcp** show dhclient running?

---

### Post by Hei Ku on 2007-07-28
weird, it does look like its running. 

how can I stop it from starting automatically?

---

### Post by noob12 on 2007-07-29
We basically need to figure out what's starting it and when; that will be the main clue to getting it disabled fully. Normally we should expect **/sbin/ifup** to start it only if the **dhcp** method is in use in at least one interface in **/etc/network/interfaces.**

One hack to figure this out would be to replace **/sbin/dhclient** with a script that just does a **ps -ef** from which one hopes to see the PID parentage at the time the process is started.

---

### Post by swampdweller on 2007-07-29
Sorry about confusing you with pataphysician Hei Ku.

---

### Post by Hei Ku on 2007-07-30
> **noob12 said:**
> We basically need to figure out what's starting it and when; that will be the main clue to getting it disabled fully. Normally we should expect **/sbin/ifup** to start it only if the **dhcp** method is in use in at least one interface in **/etc/network/interfaces.**

One hack to figure this out would be to replace **/sbin/dhclient** with a script that just does a **ps -ef** from which one hopes to see the PID parentage at the time the process is started.

I will try that. I think a script that goes like this should work.

ps -ef > parentprocess.log

---

### Post by noob12 on 2007-07-31
Yeah I think that will work to capture it.  Try /tmp though.  Not sure it'll be able to write into its working dir.

---

### Post by pauleyd on 2007-09-04
Get rid of Gnome NetworkManager!  I think it is installed default on Ubuntu.  I had set both my NICs to static IPs and it kept going to DHCP for an IP - and on my external NIC no less.  Drove me and my ISP nuts.  I kept telling him I have nothing external looking for DHCP, but then I went back and looked at my Debian server and found that Gnome NetworkManager automatically looks for DHCP and then falls back to static if one is not found - I am not sure about the logic on that one!  Issuing 'dhclient stop" did nothing because no NICs were configured or bound to DHCP.  Finally removing NetworkManager solved my problem of intermittent and totally dropped static connections.  That thing needs a big fix or maybe I do but it sure made problems for me!

Paul Davis
Director of Technology
Lynden Christian Schools
[www.lyncs.org](www.lyncs.org)

---

