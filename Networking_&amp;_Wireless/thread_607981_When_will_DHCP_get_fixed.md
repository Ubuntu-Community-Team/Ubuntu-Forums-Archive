---
title: "When will DHCP get fixed"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2007-11-09
Title says it all, it been dragging on for a long time now....

---

### Post by sipickles on 2007-11-09
I agree.

Ubuntu is stunning. For a community project it is simply amazing... all the quality software and great design... I hope my programming skills are one-day up to contributing.

But the network support? wtf?

Computers aren't stand-alone word processors anymore. 

Gutsy should NOT have been released without Total Networking Support. I have two Ubuntu PCs and my Wireless laptop was easier to configure than the wired one (which still will not connect through anything other than Firefox).

In the face of much cynicism from my Windows friends and colleagues, I continue to try and MAKE Ubuntu/Linux work..... 

I coordinate the IT at my company. I _could_ get them to abandon Windows, if only I provide an alternative which didn't require a week per PC to network.

Rant over <phew>  :)

---

### Post by mardawi on 2007-11-09
I don't really understand, what kind of network troubles are you guys facing on ubuntu? I'm just curious to know.

---

### Post by Peter09 on 2007-11-09
My main problem now is that DHCP does not work, I can connect using an ip address and can ping using an ip address but cannot use a host name for any of my machines.

My router shows all the devices attached to it and I can see correct host names in there, but Ubuntu just does not work with it. Vista on the other hand has no problems, it can see my Ubuntu machines and my networked printer. Ubuntu machines see none.

If you look through the forums you will see plenty of people with similar problems.

In my opinion DHCP is a critical part of a modern operating system. Its been broken for some time now (not just Gutsy).

---

### Post by mardawi on 2007-11-10
Are you trying to use ubuntu as a DHCP server?

---

### Post by iceslice on 2007-11-10
> **Peter09 said:**
> My main problem now is that DHCP does not work, I can connect using an ip address and can ping using an ip address but cannot use a host name for any of my machines.

My router shows all the devices attached to it and I can see correct host names in there, but Ubuntu just does not work with it. Vista on the other hand has no problems, it can see my Ubuntu machines and my networked printer. Ubuntu machines see none.

If you look through the forums you will see plenty of people with similar problems.

In my opinion DHCP is a critical part of a modern operating system. Its been broken for some time now (not just Gutsy).

I too am curious about what your problem is. I think he is trying to use his machine as a client, but I don't understand what the problem is. How are you trying to use "hostnames", and how have you configured them? What sort of things do and don't work beyond pinging, and what kind of work are you trying to accomplish?

---

### Post by Peter09 on 2007-11-10
I have a few machines on my internal network, a vista machine and four Ubuntu machines. I  have a netgear router through which they are attached to the internet. This router acts as a DHCP server.  All machines can see the internet using firefox.  I also have a NAS disk which presents as a windows share to the network.

The router shows the machines by Host name are connected.

The NAS share and my webserver are designated static addresses by the router, other machines are not static.

The vista machine can see all the other machines on the network and will link to a share by host name.

Ubuntu machines can see the domain 'HOME' which is the windows workgroup but cannot see any machine with the workgroup. The vista machine shows all machines are within the HOME workgroup.

However I can connect to a share using its IP address,but not its share host name. Similarly I can ping the ip address and get a response, but get a 'host unknown' message when trying to ping by host name.

I have a shared printer on a Ubunti machine which can be seen by the vista machine but not by other Ubuntu machines.

Looking through these forums I see a scattering of people who are voicing the same set of symptoms as myself. This is not an isolated problem. 

I have stopped ipv6 but it has made no difference.

---

### Post by grubincan on 2007-11-10
Hmm, this is my theory.....

DHCP is working for you, otherwise you wouldn't have an IP address, or be able to connect to the internet.

The DNS server (your router) is not responding to name queries for hosts in your local network.

The possible reason Vista can see other machines, assuming the above to be true, is that you are running samba shares on those boxes and they are responding to WINS queries(???).

If you have the samba client running on your ubuntu boxes, i *think* you can configure them to use WINS for name resolution, but maybe somebody with some more knowledge can chime in here and tell you what you need to do.

Sorry I can't be of more help, but you seem to be heading down the wrong path of blaming DHCP, when your solution probably lies in configuring WINS support or a better DNS server.

---

### Post by kevdog on 2007-11-11
Do a search for winbind in the forums with a post written by dbott67.  He tells you how to use names in a samba environment.  (It could be dbott69 -- I cant remember off the top of my head)

---

### Post by Peter09 on 2007-11-11
Firstly the Vista machine can see all hosts by name, so that suggests that the DHCP server is working correctly for it.

Secondly the ability to ping by host name is not any thing to do with samba (correct me if I am wrong here).

Below is a section of my syslog from boot up.

Nov  9 12:10:21 toshlaptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>    address 192.168.0.4 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>    netmask 255.255.255.0 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>    broadcast 192.168.0.255 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>    gateway 192.168.0.1 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>    nameserver 192.168.0.1 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  9 12:10:21 toshlaptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: Withdrawing address record for 192.168.0.4 on eth1.
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: New relevant interface eth1.IPv4 for mDNS.
Nov  9 12:10:21 toshlaptop avahi-daemon[5334]: Registering new address record for 192.168.0.4 on eth1.IPv4.
Nov  9 12:10:21 toshlaptop dhclient: bound to 192.168.0.4 -- renewal in 108068 seconds.
Nov  9 12:10:22 toshlaptop NetworkManager: <info>  Clearing nscd hosts cache. 

Obviously it is talking to the DHCP device and getting a response.

---

### Post by netztier on 2007-11-11
> **grubincan said:**
> 
The DNS server (your router) is not responding to name queries for hosts in your local network.

Routers don't have DNS servers - at least not the ones I know - but only DNS relays that forward and DNS request to your ISP's DNS servers (about which they have learnt via DHCP or PPPoE). Now of course your ISP's DNS servers wouldn't (want to) know anything about your local network at all. 

The fact that your router shows the hostnames in it's DHCP client table comes from the fact that the client can include it's hostname in a special field of the DHCP-DISCOVEr and DHCP-REQUEST message and the DHCP server can learn it from there. Granted, it could use that information to feed a local DNS database and act as DNS server from there - but I wouldn't know of and router that'd actually do this.

To the OP: you're barking up the wrong tree.You don't have a *DHCP* problem (or else you would'nt be getting any addresses - but this you've already shown in your last post), but very probably a *name resolution* problem.

I can think of three ways:

**hosts file**
As a simple and rather crude (but rather foolproof) alternative, you could configure DHCP reservations on your router so that each machine always gets the same IP address, and then write a simple **/etc/hosts** file that you keep in sync on all your machines.

**local DNS**
As the most advanced solution, you could run a DNS on a machine in your local network, maybe along with a DHCP service with reservations for each machine; the DNS would use your ISP' DNS server as "forwarders". This is of course the most advanced approach. Downside: the DNS/DHCP machine would have to be up 24/7 or whenever someone wants to use your network.


**avahi**
You could try with avahi, so that each of your machines becomes resolvable via **<hostname>.local**. You showed syslog output from one of them, I think avahi is already running on that one and it's announcing itself. You'll probably have to activate avahi-based (also called mDNS) resolution in /etc/nsswitch.conf on the Ubuntu machines. 

```
marc@cube:/$ **more /etc/nsswitch.conf **
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns **[COLOR="DarkGreen"]mdns[/COLOR]**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

[INDENT][I]Edit: actually, on agutsy fresh install (on a Sun Ultra 5), this line looks like this:

```
hosts:      files mnds4_minimal [NOTFOUND=return] dns mdns4
```

And this station can resolve any other hostname on the network easily with the .local extension. Even typing **smb://<hostname>.local/** in Nautilus brings up the file server's shared directories instantly.[/I]
[/INDENT]

Please search the forums for the details about mDNS resolution - there's a knack or two about it - but maybe it's all been fixed with gutsy already. I'd need to boot my clean-install machine to tell.


**Suggestion:**
Search the forums about avahi and mDNS. This should be the approach that leads to best ineroperability.

regards

Marc

---

### Post by Peter09 on 2007-11-11
Hi Netztier,
thanks for the response. 

I guess I raised this thread as much to get some recognition of the problem as to find a fix. I have seen a few posts by people who have a similar problem and they almost all go unaddressed to some extent. I am unsure that I want to make large changes to my systems to address bugs, I really want them addressed at source.

It would be nice to know that there is a recognised problem from within Ubuntu, may be there is, although I do not know.

---

