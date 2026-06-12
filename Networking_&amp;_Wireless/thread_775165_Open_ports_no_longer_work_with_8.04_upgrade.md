---
title: "Open ports no longer work with 8.04 upgrade?"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Impulse666 on 2008-04-29
I had 7.10 and many versions before all configured simply through my router's firewall page for open port access. I just upgraded to 8.04 and haven't been able to get it working. Previous upgrades never needed any work. Well i have the port forwarded from my router to my local ip address, and i have the client set up to accept the port. Yet in all [tests]("http://www.canyouseeme.org/") it says the port is closed. The same configuration works in dual-booted XP mode great. 

Side note: I just installed Deluge (I had been using KTorrent on Ubuntu, as i have before, both standard and KDE4 versions tried) and specified a port. It linked me to it's own port test, and it came back positive. I then checked canyouseeme.org and it worked as well. But when I close Deluge the tests say the connection is refused. Deluge makes it all work, yet speeds are not up to par (files tested on 10k seeds).

oh well. Here it goes...

```
nick@desktop:~$ sudo iptables -L
[sudo] password for nick: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:38586 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:38586 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:38586 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:38586 
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
nick@desktop:~$
```

```
nick@desktop:~$ sudo nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-04-29 22:10 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.151 seconds
nick@desktop:~$ 
```

```
nick@desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
38586:tcp                  ALLOW   Anywhere
38586:udp                  ALLOW   Anywhere

nick@desktop:~$ 
```

```
nick@desktop:~$ netstat -lnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
nick@desktop:~$ 
```

Any help is GREATLY appreciated, as this has completely stumped me. :(

---

### Post by Impulse666 on 2008-04-30
Well it looks like its either XP or back to 7.10 for me now. Still nothing.

---

### Post by Impulse666 on 2008-05-01
Problem solved. But I moved over to the Fedora family first. I assume it would work in Ubuntu as well.
(Just posted so others would know if they had a similar problem.)

the tests at:
[www.canyouseeme.org](www.canyouseeme.org)
[http://whatsmyip.org/ports/](http://whatsmyip.org/ports/)
[http://www.utorrent.com/testport.php?port=6881](http://www.utorrent.com/testport.php?port=6881)

are reliant upon having your client open and listening for incoming connections. With KTorrent closed, the test will fail, but open KTorrent/Azureus/Transmission and test (after configuring the client for the specific port) and the test will be success. :)

This is all done in addition to your router forwarding ports to your local IP address.

Enjoy.

---

