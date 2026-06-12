---
title: "Windows does not resolve Ubuntu hostname"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by danidemi on 2009-03-04
Hi.

I have two machines connected to a NETGEAR router.
The first one is called "DELLBOX" (192.168.0.100) and runs WINDOWS.
The second one is called "ALOABOX" (192.168.0.101) and runs UBUNTU.

The problem.
From ALOABOX I can either
```
ping DELLBOX
```
and
```
ping 192.168.0.100
```
and I got the expected result, with the usual list of packet received.

But if I run 
```
ping ALOABOX
```
From DELLBOX (the win machine), it seems Windows is not able to resolve the Ubuntu machine hostname.

If, in the other hand I execute
```
ping 192.168.0.101
```
All works well, with the usual list of correctly received ICMP packets.

So briefly...
[LIST]
[*]UBUNTU can ping WIN host using WIN's hostname
[*]WIN **CANNOT** ping UBUNTU host using UBUNTU's hostname
[/LIST]

I think that the problem is in Ubuntu because if I check the "attached devices" page in the administration of my netgear router, I see something as...
```

#  	 IP Address   	 Device Name   	 MAC Address
1 	192.168.0.101 	UNKNOWN 	00:21:9B:17:36:5C
2 	192.168.0.100 	DELLBOX 	00:0D:56:6C:C4:5E

```

Pay attention to the fact that the UNKNOWN machine is actually the Ubuntu machine. So... it seems the netgear router has the same problems Windows has...

Do you have an idea about why that is happening ?

Regards 
Dani

---

### Post by OffAxis on 2009-03-04
can the ALOABOX ping itself?

```
ping -c 4 ALOABOX
```

---

### Post by bodhi.zazen on 2009-03-04
You need to add your ubuntu box to your windows hosts file or (more difficult) set up an internal DNS server.

---

### Post by danidemi on 2009-03-04
I think bodhi.zazen is right.

I think that the reason why the ping works from linux to win but not the other way around is that because Win and the Netgear router are using UPnP, a protocol used to simplify the creation of small networks. I think that through UPnP the Win box "publishes" its hostname to the router. In the other hand the linux box can retrieve the name of the winbox from the router, but since the linuxbox does not publish its hostname, the winbox can ping it only using its IP.

---

### Post by Iowan on 2009-03-04
Unlikely to solve the problem, but just in case...
For a DHCP connection, /etc/dhcp3/dhclient.conf can be modified. On one of my servers, the line reads:```
#send host-name "andare.fugue.com";
``` That line could be un-commented, and your hostname substituted. That lets the DHCP server know your hostname... the trick is passing that info to DNS.

---

### Post by danidemi on 2009-03-05
Answering to a previous question: yes, the aloabox can ping itself.

I modified the dhclient configuration file, rebooted the machine but nothing changed. I think I'll live updating the hosts file in win, since with only two machines in a LAN is really not a big issue.

Thank you for your help.

Dani

---

### Post by Radioman991 on 2009-03-05
+2

> **danidemi said:**
> i think bodhi.zazen is right.

I think that the reason why the ping works from linux to win but not the other way around is that because win and the netgear router are using upnp, a protocol used to simplify the creation of small networks. I think that through upnp the win box "publishes" its hostname to the router. In the other hand the linux box can retrieve the name of the winbox from the router, but since the linuxbox does not publish its hostname, the winbox can ping it only using its ip.

---

