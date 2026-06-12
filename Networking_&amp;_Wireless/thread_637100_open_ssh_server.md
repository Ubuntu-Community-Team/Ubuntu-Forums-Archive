---
title: "open ssh server"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by superuser84 on 2007-12-10
Hi,

I want to enable SSH server on my laptop. When I type "netstat -tulpn", I get.

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5033/cupsd          
tcp6       0      0 :::22                   :::*                    LISTEN     6660/sshd           
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          5262/avahi-daemon:  
udp        0      0 0.0.0.0:68              0.0.0.0:*                          5841/dhclient       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5262/avahi-daemon:  

I want to change the port from 22 to 512. But changing the entry in the file /etc/ssh/ssh_config and restarting the SSH server does not update the entry.

Basically I want to disable Telnet and enable SSH only.

Many Thanks,
J.

---

### Post by mpokrywka on 2007-12-10
You probably edited wrong config file, you should edit /etc/ssh/ssh**d**_config and restart daemon

---

### Post by superuser84 on 2007-12-11
Thanks a lot. Now the port is updated to 512, but still SSH to the machine does not work.

However, If I try to telnet to my machine, I get the following message...

[username@client-machine]$telnet server-machine
Trying server-machine...
Connected to server-machine.
Escape character is '^]'.

Password: [SSL not available]


I want to disable telnet and log-in via SSH.

Many thanks in advance for your help.

J.

---

### Post by mpokrywka on 2007-12-11
"SSH to the machine does not work" - are you sure you are connecting to proper machine?
Try "ssh -v -p 512 server_machine"
-v == verbose debug
-p 512 == use dst port 512
There will be many lines of debug info, make sure that you are connecting to proper host (among first few lines there should be "Connecting to host [ip.add.re.ss] port xx")

Maybe you checked running services on your laptop with (netstat -tunlp) but you are trying to connect to other host (server-machine)? To be sure, run "netstat -tunlp" from local console of the server. I wonder how you got telnet server running, because ubuntu (and many other distributions) do not install it by default and netstat in first post do not show any app listening on port 23.

---

