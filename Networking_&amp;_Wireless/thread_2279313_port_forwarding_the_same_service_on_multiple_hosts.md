---
title: "port forwarding the same service on multiple hosts"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2015-05-22
Okay, this isn't really an ubuntu specific question but I figure this is a good place to ask.

I am running ESXi and have about a half dozen guests on it.  If I want to enable a service, say SSH for example and make it accessible to the outside world, I have to go into my router and forward port 22, but that literally only allows me to forward just one host.  Now if I wanted to forward all of the hosts and assign each one a separate EXTERNAL port number, eg; 22220 for ESXi itself, 22221 for VM 1, 22222 for host 2, 22223 for host 3, etc.  while keeping the service running on port 22 on each guest VM.  How would I accomplish this?  in my router (a crappy Netgear CG3000DV2) I have the ability to set custom internal and external rules, like this

[table="width: 500", class: grid"]
[tr]
[td] [/td][td]External[/td][td] [/td][td]Internal [/td][td] [/td][td][/td][td] [/td]
[/tr]
[tr]
[td]Name[/td][td]Start Port[/td][td]End Port[/td][td]Start Port[/td][td]End Port[/td][td]Protocol[/td][td]Local IP Address[/td]
[/tr]
[tr]
[td]VNC[/td][td]5900[/td][td]5900[/td][td]5900[/td][td]5900[/td][td]TCP/UDP[/td][td]192.168.0.100[/td]
[/tr]
[/table]

Now, to me it seems logical that if I configure the port forwarding like this:
[table="width: 500", class: grid"]
[tr]
[td] [/td][td]External[/td][td] [/td][td]Internal [/td][td] [/td][td][/td][td] [/td]
[/tr]
[tr]
[td]Name[/td][td]Start Port[/td][td]End Port[/td][td]Start Port[/td][td]End Port[/td][td]Protocol[/td][td]Local IP Address[/td]
[/tr]
[tr]
[td]VNC[/td][td]5900[/td][td]5900[/td][td]5901[/td][td]5901[/td][td]TCP/UDP[/td][td]192.168.0.101[/td]
[/tr]
[/table]

It should allow me to connect to port 5900 on guest 2 (192.168.0.101) via port 5901 from outside of my home network.  But every time I try to do this I get a less than informative error saying "port overlap".  If I configure the port the other way around, I get the same error.  I am sure that I am NOT the first person in the world to want to be able to access the same service on multiple ports on multiple hosts from outside of their network.

And before ANYONE suggests it, yes I am FULLY aware that I could set up a VPN.  I in fact already have both L2TP and PPTP set up on one of these guests.  But many times, I find myself in places where ports used by L2TP and PPTP are blocked by the firewall, or I working in the cloud and am already behind a VPN and cant connect to another.

Not only that, but in many cases, you can't change the configured port of a service, ie; RDP on Windows Server 2K8R2 (my vCenter server).  And even if I could, I wouldn't want to because I'd constantly be trying to remember which host is assigned which port for which service, which even if I had that information readily available somewhere, STILL WOULDN'T WORK in many cases, such as RDP on Windows.  Linux may be capable of specifying a port for RDP, but Windows literally is only capable of listening on port 3389.  No amount of adding a colon and port number after the host name or IP is going to change that.

The workaround I'm using at the moment is to SSH tunnel in to the VNC service of one physical box on my home network and then RDP or VNC in to individual hosts, but performance is absolutely terrible.  And having to constantly change port forwarding in my router is cumbersome.  Not only that, but I'm constantly having to blow away my ssh config due to mismatched RSA keys when I ssh into my DNS.

There HAS to be a simple, elegant solution for all of this.

---

### Post by Keith_Helms on 2015-05-23
I think this feature is called Port Address Translation (PAT) and Netgear consumer routers don't support it.  You might pick up that capability by installing one of the open source router firmwares on the device - DD-WRT or OpenWRT.

---

### Post by N00b-un-2 on 2015-06-05
I kind of figured that might be the case.  unfortunately, my router is not on the compatibility list for DD-WRT or OpenWRT (I've checked...)

---

