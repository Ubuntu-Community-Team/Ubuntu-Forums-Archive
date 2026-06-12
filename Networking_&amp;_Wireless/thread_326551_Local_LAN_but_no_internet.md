---
title: "Local LAN but no internet"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by boisgle on 2006-12-27
This is my first attempt at loading a linux client. I am an experienced pc tech and have a CCNP, but I cannot seem to get Ubuntu 6.1 to get through my router. I currently have a network setup with a Windows 2003 server that runs DNS and DHCP. I need to go out on the internet to get repositories so that I can load ubuntu on a machine with hardware raid. The ubuntu machine boots into the client without issue. The machine pulls a IP lease from my DHCP server and can ping any machine on my network. I cannot although ping the router. It says that it is an unreachable host. This sounds to me like a DNS issue. I have tried to hard code the IP/subnet mask/gateway and I get the same issue. The router is not set to filter anything out. I even tried to put the ubuntu machine in the DMZ without success.](*,) 
Does anyone have an idea about this issue? Or at least point me in a direction. Like I said, I am a linux newbie, so responsed may have to be very specific as I lean this OS.

---

### Post by kidders on 2006-12-27
Hi there,

I'm just trying to get a picture of your network. Is the router on the same subnet as the Ubuntu box? Are the two directly connected to eachother (through a hub/switch), or is there other stuff between them? What's set as your Ubuntu box's default route?

---

### Post by dbott67 on 2006-12-27
From the Ubuntu machine, can you post the output of:
```
route -n
```

-Dave

---

### Post by boisgle on 2006-12-28
All the machines in this network are on the same subnet. There is one switch between the PC and the router. It is unmanaged. PC pulls an ip of 198.100.100.12 and the router/gateway is 198.100.100.100. The SNM is 255.255.255.0. Standard stuff. I understand that these are not private IP addresses, but since I know they will always be NAT'd, I thought it would be a _bit_ more security than the 192.168.x.x that most routers default to.
I may just say the heck with it and hook the cable modem directly to the PC, get the repositories, get the client installed, and then deal with the issue after the client is installed and functioning on the local network.

As for the command route -n, I am not near the machine now, but will try it tonight and post the output later.

Thank you.

---

### Post by dbott67 on 2006-12-28
You might try switching to the Class A subnet (10.x.y.z) rather than using public IPs.  I don't think that what you're doing would cause the problem, however, you may have name resolution problems for any IPs in that range:
```
Location: United States [City: Manassas, Virginia]


OrgName:    Tobyhanna Army Depot 
OrgID:      TAD
Address:    7990 Science Applications Court
City:       Vienna
StateProv:  VA
PostalCode: 20110
Country:    US

NetRange:   192.100.100.0 - 192.100.100.255 
CIDR:       192.100.100.0/24 
NetName:    TOBY-NET
NetHandle:  NET-192-100-100-0-1
Parent:     NET-192-0-0-0-0
NetType:    Direct Assignment
NameServer: CON1R.NIPR.MIL
NameServer: CON2R.NIPR.MIL
NameServer: EUR1R.NIPR.MIL
NameServer: EUR2R.NIPR.MIL
NameServer: PAC1R.NIPR.MIL
NameServer: PAC2R.NIPR.MIL
Comment:    
RegDate:    1991-04-12
Updated:    2006-04-11

RTechHandle: MIL-HSTMST-ARIN
RTechName:   Network DoD 
RTechPhone:  +1-800-365-3642
RTechEmail:  **********@nic.mil 

# ARIN WHOIS database, last updated 2006-12-27 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

```

---

### Post by kidders on 2006-12-28
Hmmm...

I've attached my impression of your LAN (excuse the crude diagram). Assuming it's accurate, I can't seem to figure out a way **ping 198.100.100.100** could be failing *only* on the Ubuntu box :-( I must have the wrong idea, I think.

---

### Post by boisgle on 2006-12-28
I figured it out. 
I guess I jumped the gun when I said that the router was not filtering. 
I had this pc running windows at one time and had MAC filtering turned on within the router. I did have the MAC address in there, but forgot that I had reloaded the router at one point and the MAC was no longer in the list. I placed it in there and voila, everything works. Thats for everyone's input though.
I guess it is just better to get away from it for awhile and think about it. I always seem to get the answer after a long rest.

Thx again.:-D

---

