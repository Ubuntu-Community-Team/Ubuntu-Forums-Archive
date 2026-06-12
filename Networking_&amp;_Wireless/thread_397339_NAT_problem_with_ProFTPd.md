---
title: "NAT problem with ProFTPd"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by andrewww85 on 2007-03-30
I'm trying to setup an ftp server on a pc in my home network. It works well in my local network, but it's unreacheable from any other internet host. The server is behind NAT, so I have opened the ports 20 and 21 on my router and on my firewall (Firestarter). I have also set the PASV port range to 60000-65535 and forwarded the same ports on my router. At last I have modified my configuration file adding the line:

MasqueradeAddress *my-dyndnsname.com*

I want to specify that my network schema is like this: AdslRouter(192.168.1.1)-->WirelessAccessPoint(192.168.1.2)-->PC(192.168.1.3)(wired)

When I try to access to [ftp://*my-dyndnsname.com](ftp://*my-dyndnsname.com)*, Firefox says "Connection failed"! :S

I really don't know what is the problem! Please help me!

---

### Post by Mr. C. on 2007-03-30
You don't need port 20 open, only 21 (the command channel).

Do you have your high-level ports open in Firestarter ?

Router's that support PASV ftp peek at the data returned from PASV, and open the port for the specified IP.  Of course, it would expect the LAN address of your FTP server, not a masqueraded one.  Do you know if your router supports PASV ftp through NAT ?

MrC

---

