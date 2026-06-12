---
title: "cant connect to open tcp port"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by bored_coder_ca on 2006-11-29
Hi all,

I am trying to diagnose a problem with the apache derby network server. The root cause of this problem seems to be ubuntu. The server connects and runs on port 1527. If i connect from the same machine to port 1527 (via localhost) it works fine. But when i try to connect via from another machine i get a connection refused error. I have duplicated this behavior with a simple perl script that listens on port 9999.

any ideas for why this doesnt work? I dont have a software firewall installed (unless ubuntu comes with one installed on version 6.10).

thanks,

---

### Post by scoon on 2006-11-29
Hey there, 

Can you check the logs in apache, they'll definitely be helpful here. 

-scoon

---

### Post by bored_coder_ca on 2006-11-29
Hi, 

I went through the logs and there is no information regarding the problem that I can see. I'm guessing that the problem is in ubuntu itself because i cant remotely connect to a simple perl script that I created. Do you have to 'allow' ports to be remotely connectable in ubuntu?

thanks

---

### Post by bmillsap on 2006-11-29
Just in case, what does the output of "sudo iptables -L" look like?

---

### Post by bored_coder_ca on 2006-11-29
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by scoon on 2006-11-29
> **bored_coder_ca said:**
> Hi, 

I went through the logs and there is no information regarding the problem that I can see. I'm guessing that the problem is in ubuntu itself because i cant remotely connect to a simple perl script that I created. Do you have to 'allow' ports to be remotely connectable in ubuntu?

thanks

Hey there, 

Can you connect to the script via another machine/os ?

-scoon

---

### Post by bored_coder_ca on 2006-11-29
no i cant connect to it from another machine.
here is a summary
from the machine the script/db is installed (ip 192.168.2.6):
**telnet localhost 1527** or **9999** works
**telnet 192.168.2.6 1527** or **9999** doesnt work

from the remote machine
[B]
telnet 192.168.2.6 1527[/B] or **9999** does not work

thanks

---

### Post by scoon on 2006-11-29
Hey there, 

My guess is that you should double check your telnet config on the machine you are trying to get to.  Also, telnet isn't the safest proto to use.  What about ssh?

-scoon

---

### Post by bmillsap on 2006-11-29
Can you ping 192.168.2.6 from itself?

---

### Post by bored_coder_ca on 2006-11-29
im only using telnet to demonstrate connectivity. i use ssh for everything else.

I can ping 192.168.2.6 from itself

thanks,

---

### Post by scoon on 2006-11-29
Hey there, 

So, can you ssh to the machine?

-scoon

---

### Post by bored_coder_ca on 2006-11-29
yeah i can ssh to the machine, i did a port scan and the only 2 ports open on this machine is ssh (22) and an inet daemon i have running on port 6789

---

### Post by scoon on 2006-11-29
> **bored_coder_ca said:**
> yeah i can ssh to the machine, i did a port scan and the only 2 ports open on this machine is ssh (22) and an inet daemon i have running on port 6789

Hey there, 

Neither of those open ports seem to be the one you want to connect to?  Am I wrong here?

-scoon

---

### Post by bored_coder_ca on 2006-11-29
No im trying to connect to apache derby (1527) and the perl script (9999).

---

### Post by bored_coder_ca on 2006-11-29
I tried the same script on my laptop (also ubuntu 6.10) and i have the same problem. Any ideas?

---

### Post by scoon on 2006-11-29
> **bored_coder_ca said:**
> No im trying to connect to apache derby (1527) and the perl script (9999).

Hey there, 

So don't those ports (1527, 9999) need to be open as well?

-scoon

---

### Post by bored_coder_ca on 2006-11-30
yeah thats the problem. Though both the programs seem to be running and waiting for connections on port 9999 and 1527 respectively the port scan says that they are not open.

---

### Post by bjd on 2006-11-30
Maybe the ports are bound to a specific ip address or even localhost, instead of the all interfaces.
What's the output of *netstat -ant* on the server?

---

### Post by bored_coder_ca on 2006-11-30
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3971          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6789            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:9999          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::ffff:127.0.0.1:1527   :::*                    LISTEN     
tcp6       0      0 ::ffff:192.168.2.6:22   ::ffff:192.168.2.:54250 ESTABLISHED
tcp6       0      0 ::ffff:192.168.2.6:22   ::ffff:192.168.2.:43338 ESTABLISHED
tcp6       0    768 ::ffff:192.168.2.6:22   ::ffff:192.168.2.:54249 ESTABLISHED

---

### Post by bjd on 2006-11-30
*tcp6 0 0 ::ffff:127.0.0.1:1527 :::* LISTEN*
That line indicates the server is only listening on the localhost interface and thus not reachable from the outside.
Check docs and/or config files for an option to set the interaface to bind to.

more info about this for apache derby here:
[http://db.apache.org/derby/docs/dev/adminguide/cadminnetservsecurity.html](http://db.apache.org/derby/docs/dev/adminguide/cadminnetservsecurity.html)

---

### Post by bored_coder_ca on 2006-11-30
ok thanks, I look into it

---

### Post by bored_coder_ca on 2006-11-30
yeah it works now, thanks alot

---

