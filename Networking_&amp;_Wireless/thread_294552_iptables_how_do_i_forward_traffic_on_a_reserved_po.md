---
title: "iptables: how do i forward traffic on a reserved port"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by discord on 2006-11-06
Hello,

I wish to use a "reserved: port (below 1024) for traffic using the bittorrent client Axureus. I am behind a restrictive firewall but I know some of the "reserved" ports are open. If I use azureus in windows I can choose to use port 22 for traffic and it works fine. However in linux when I try to use the same port I get the message

 Testing port 22 ... Unable to test: Invalid port given, or test service failed.Another application may already be using this port.

Is there a way I can use iptables to allow myself to use the "reserved" port. I guess windows allows the administrator users to use these "reserved: ports

---

### Post by NetworkGuy on 2006-11-06
If I read your post right, you are trying to tell Axureus to use port 22.  Maybe you need to look at this a different way.

What I recommend is to use IPTables to convert Axureus normal traffic to port 22.  If your restrictive firewall allows both inbound and outbound traffic on that port, it should work.  The traffic inbound from the Internet on port 22 would hit IPTables.  IPTables would convert the data from port 22 to whatever port Axureus is looking for.  Same for outbound, Axureus sends data on it's normal port and IPTables will convert it to port 22 before it leaves your PC.

However, I don't know enough about IPTables (yet) to give you the IPTables syntax to do it.

> I guess windows allows the administrator users to use these "reserved: ports
You are correct.  This was one of the main complaints by the security folks when XP came out.

---

### Post by discord on 2006-11-06
yes that is exactly what i want to do. I actually found out how to do this with a google search before but am not having luck searching today. Maybe we have some iptables gurus in here who could help me with the line.

---

### Post by handy on 2006-11-07
This is a great tutorial.

I hope it helps.

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

