---
title: "Ping via Hostname not resolving"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by kaminsky59 on 2014-01-15
I have searched throughout this forum and through the internet but have not been able to find anything that matches my setup.

I have a Netgear router that provides DHCP to my network. I recently set up an Ubuntu 12.04 server with a hostname and an IP address. I have a laptop that runs Ubuntu Desktop and a PC that runs Windows 7. The server has Samba on it as well.

Now the situation. I can SSH into the server using its IP address but not HOSTNAME and can ping the outside world from the server using hostname i.e. ping [www.google.com](www.google.com) works just fine. I can ping other computers on my network via IP as well without any problem. I can ping the server via HOSTNAME from my WINDOWS PC but I cannot ping my server via hostname from my LINUX laptop. 

From my windows PC I can access the server that is found on my network using the IP address but when I try to access \\servername it does not resolve (Windows cannot access \\servername)

Any help would be appreciated. 

Thank you

---

### Post by bapoumba on 2014-01-15
Moved to Networking.

---

### Post by bab1 on 2014-01-15
> **kaminsky59 said:**
> I have searched throughout this forum and through the internet but have not been able to find anything that matches my setup.

I have a Netgear router that provides DHCP to my network. I recently set up an Ubuntu 12.04 server with a hostname and an IP address. I have a laptop that runs Ubuntu Desktop and a PC that runs Windows 7. The server has Samba on it as well.

Now the situation. I can SSH into the server using its IP address but not HOSTNAME and can ping the outside world from the server using hostname i.e. ping [www.google.com](www.google.com) works just fine. 

DNS uses zones.  You do not have a local LAN zone set up.  The DNS servers that resolve the Internet are configured and are working fine however.
> 
I can ping other computers on my network via IP as well without any problem. I can ping the server via HOSTNAME from my WINDOWS PC but I cannot ping my server via hostname from my LINUX laptop. 

Linux will not resolve LAN DNS unless you set this up.  IDK about Windows but it sure sounds like it is setup by default on that OS.
> 
From my windows PC I can access the server that is found on my network using the IP address but when I try to access \\servername it does not resolve (Windows cannot access \\servername)

There are 2 types of naming conventions here.  The computer can have both a DNS hostname and a NETBIOS computer name.  Ping uses DNS hostnames and Network Neighborhood (Samba shares) uses NETBIOS.  In addition Windows uses UNC notation ( the \\ convention).  It depends upon what you are trying to do and what OS the computer is running.

PING uses DNS hostnames (e.g. ping hostname or ping hostname.dns_domain.tld)  if you are looking for a Windows share you would use this convention: //NETBIOS_NAME/SHARE for a Linux or Windows host and alternatively \\NETBIOS_NAME on a WIndows host.

All of this means nothing until we apply it in the real world.  Is "the server" using a fixed IP address?  How did you create the hostname on "the server"  Dose the Netgear router have local LAN DNS configuration.  With Linux you can setup local LAN hosts resolution (Local DNS) via the hosts file on each machine.  This means you have toset each machine up with the hostname to IP address mapping.

Windows/Samba file sharing is a little different.  There are multiple ways to create NETBIOS NAMES.  Are you setting up file sharing on the server?

---

### Post by kaminsky59 on 2014-01-17
> **bab1 said:**
> 
All of this means nothing until we apply it in the real world.  Is "the server" using a fixed IP address?  How did you create the hostname on "the server"  Dose the Netgear router have local LAN DNS configuration.  With Linux you can setup local LAN hosts resolution (Local DNS) via the hosts file on each machine.  This means you have toset each machine up with the hostname to IP address mapping.

Windows/Samba file sharing is a little different.  There are multiple ways to create NETBIOS NAMES.  Are you setting up file sharing on the server?

- The server is using a fixed IP. When I installed Ubuntu Server it automatically set using DHCP but I changed the /etc/network/interfaces file for static. 
- The hostname was also created during the initial installation. 
- I checked the Netgear router and it only has Dynamic DNS which doesn't help in this local network situation
- Yes I would like to set up file sharing for both Windows/Linux

For the brute force method of mapping the Hostname to IP address, I'm assuming I have to set my Linux laptop to static to correctly map it on the server.

---

### Post by bab1 on 2014-01-17
> **kaminsky59 said:**
> - The server is using a fixed IP. When I installed Ubuntu Server it automatically set using DHCP but I changed the /etc/network/interfaces file for static. 
- The hostname was also created during the initial installation. 
- I checked the Netgear router and it only has Dynamic DNS which doesn't help in this local network situation
- Yes I would like to set up file sharing for both Windows/Linux

For the brute force method of mapping the Hostname to IP address, I'm assuming I have to set my Linux laptop to static to correctly map it on the server.

No need to change the IP addressing method just yet.  Do you have directories on the laptop you wish to share?  From the laptop post the output of these 2 commands```
cat /etc/hosts

hostname
```

Now ssh into the Ubuntu server and post the same info for it.

---

