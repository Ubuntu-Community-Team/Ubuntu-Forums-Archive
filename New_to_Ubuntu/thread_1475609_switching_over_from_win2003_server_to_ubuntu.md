---
title: "switching over from win2003 server to ubuntu"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by pakshore on 2010-05-07
hi
i am currently using a server to share internet with windows server 2003 and isa with bandwidth splitter. i was hoping that if somebody would be kind enough to help me swicth over to ubuntu server.

---

### Post by r-senior on 2010-05-07
I think it would be useful if you could explain more fully what you would like to do.

How are you connecting to the Internet? 
What capabilities does your router have? NAT, DHCP, etc?
What machines will be part of your network? (Win + Ubuntu clients, Ubuntu server only, etc)
What services will your Ubuntu server provide? (DNS, mail, file & print, proxy, NAT, etc)

---

### Post by pakshore on 2010-05-07
currently i have a 4mb adsl connection. the server is only for internet sharing. windows 2003 server is installed on it and dns dhcp running on it nat, firewall and bandwidth management  is done by the microsoft internet security and acceleration software which is also installed on it.  The client machines are running on windows and are connected to the server through wifi AP.
 
so my Ubuntu server should provide dns,dhcp,nat and bandwidth management. the client machine will be running on windows.

---

### Post by bredman on 2010-05-07
To use an Ubuntu machine as your Internet Access Server and proxy, the most common method is to use Squid. See [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

Note that Squid is fairly heavy-duty and would be best for medium to large networks.

---

