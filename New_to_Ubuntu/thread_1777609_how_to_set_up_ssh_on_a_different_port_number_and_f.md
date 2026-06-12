---
title: "how to set up ssh on a different port number and firewall issues"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-07
On the server, I want to ssh with different port number other than 22, also set firewall accordingly to allow out going traffic from port 80, and only allow couple client computers that has static IP to ssh.

I checked [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
registered ports are from 1024-49151
and dynamic/private ports are those from 49152-65535

has anyone used a dynamic/private port numbers for ssh?  Or is there a specific unassigned registered port number set that I shoud use? What is preffered?

In addition to that how do I permit the specific port to open on the firewall with gufw? I also have ufw installed
For a server for port 80, do I need to allow incoming, and deny outgoing ???

I checked [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

is that all I need for proper set up?
> 
sudo ufw allow 80
sudo ufw allow 22(or whatever the ssh port is)


I also found this. On terminal
> 
-A RH-Firewall-1-INPUT -s 192.168.1.0/24 -m state --state NEW -p tcp --dport 22 -j ACCEPT
-A RH-Firewall-1-INPUT -s 202.54.1.5/29 -m state --state NEW -p tcp --dport 22 -j ACCEPT

I am assuming 192.168.1.0/24 is the router set and 202.54.1.5/29 is the IP set for the servers. Is that correct?

How do I allow an IP from client and deny any other for ssh?

I did get some overview from this link [http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html;](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html;) however, I dont see any part where it states to block any IP for ssh except your client 

Please, advise.  Thank you so much.

---

### Post by ecridium on 2011-06-08
Try this sites :
[http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html](http://techie-buzz.com/foss/change-default-ssh-port-in-linux.html)
[http://ubuntuforums.org/showthread.php?t=253460](http://ubuntuforums.org/showthread.php?t=253460)
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

In my experience you may need to know open outgoing port of the modem/gateway router.  You also may need port forwarding.

---

### Post by alphacrucis2 on 2011-06-08
> **007casper said:**
> I am assuming 192.168.1.0/24 is the router set and 202.54.1.5/29 is the IP set for the servers. Is that correct?

No. Each line is an iptables rule that specifies a permitted source subnet that's allowed to start a NEW connection to TCP 22. The -j ACCEPT at the end of each line means that if the input packet matches the rule then jump to ACCEPT (ie permit the packet to pass). The first line specifies a source subnet of 192.168.1.0/24. The /24 is specifying the bit prefix or netmask ie. /24 = 255.255.255.0 meaning the subnet consists of 192.168.1.0 through 192.168.1.255. The second line specifying source subnet 202.54.1.5/29 is a bit odd as 202.54.1.5 does not start on a /29 subnet boundary, so I assume they mean just the host 202.54.1.5 is allowed. Normally a host subnet would be written as 202.54.1.5/32 or otherwise just the plain host address 202.54.1.5. If they really wanted a /29 subnet, then the last octet should start with 0, 8, 16 etc.

iptables rules are processed sequentially unless a -j diverts the processing. For example if you wanted to specifically block a packet you can end the rule line with -j DROP or -j REJECT. If the packet reaches the end of the list of rules without matching anything then what happens depends on the default policy. For example the default policy set for INPUT could be ACCEPT which means allow anything that doesn't match a rule. If the default was DROP means that anything that doesn't explicitly match a rule will get dropped. If you google iptables howto you should get some good info.

---

### Post by doas777 on 2011-06-08
> **007casper said:**
> On the server, I want to ssh with different port number other than 22, also set firewall accordingly to allow out going traffic from port 80, and only allow couple client computers that has static IP to ssh.

I checked [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
registered ports are from 1024-49151
and dynamic/private ports are those from 49152-65535

has anyone used a dynamic/private port numbers for ssh?  Or is there a specific unassigned registered port number set that I shoud use? What is preffered?


the registered ports are up for grabs. most developers use 4-digit ports, just make sure it does not conflict with a common service (most services on the iana port-numbers document are not common). you can use this block if you are really worried about it:
#               6772-6784  Unassigned 

[FONT=Verdana]any port associated with a protocol that you do not personally use on your network will 
probably do fine.[/FONT]
[FONT=Verdana]I'd avoid the dynamic range just for firewall compatibility with whatever 
site you are accessing the service from.[/FONT]

---

