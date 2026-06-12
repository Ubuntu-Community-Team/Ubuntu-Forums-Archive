---
title: "ubuntu home net issue"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by muu on 2007-01-09
I have a wi-fi network with an ubuntu box and a laptop (windows).
The laptop is fine, it can see the network and the ubuntu box, it is 192.168.0.10.
The ubuntu box can see the net, but not the laptop, it is 192.168.0.11.
Here is the output from route:
<fixed>
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
</fixed>
Can someone lead me to the error of my ways?  TIA.

---

### Post by Soarer on 2007-01-09
How do you mean, it can't 'see' the Windows box? Can it ping it's IP? If so, you need the Samba client (smbclient) installed on the Ubuntu box then you will be able to connect to shared folders on the Windows box.

---

### Post by muu on 2007-01-09
No, what I mean is that I cannot ftp from the ubuntu box to the win box.

When I try to ftp win -> ubuntu, the win box shows a connection, but hangs.
I look at the syslog in ubuntu and it shows the connection but nothing more.
I am assuming that the ftp is having the same problem I see in telnet, which
is that when ubuntu sends out packets destined for the win box, they don't get there.

???

---

### Post by Soarer on 2007-01-09
Can you ping either box from the other? That's the first step.

Secondly, do you have an FTP server set-up on the Ubuntu box?

---

### Post by muu on 2007-01-09
yes, i can ping ubuntu from windows
cannot ping windows from ubuntu (but can ping anyplace else on net, eg [www.yahoo.com](www.yahoo.com))

both are running ftp telnet

---

### Post by hal10000 on 2007-01-09
If you want to get an ftp connection from windows to ubuntu, you have to install a ftp-server program like the wu-ftp package, not only the ftp program, which just is a client to connect to other ftp servers

Do you have a firewall running on either of your boxes? If so, then tmporarily stop them and try ping again.

---

