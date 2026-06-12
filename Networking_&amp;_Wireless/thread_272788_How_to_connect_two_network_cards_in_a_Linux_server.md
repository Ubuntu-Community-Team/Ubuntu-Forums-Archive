---
title: "How to connect two network cards in a Linux server"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by arava on 2006-10-07
Hi everyone:

I have a home network and would like to add an ubuntu LAMP server for the outside world. Of course I need to administer it and transfer files to and from it. I would also like to allow a few select friends to update the web files remotely.
Reading various forums, the most popular advice (for security) is to install two ethernet cards into the server. One heavily firewalled towards the Internet and another NIC for internal system administration (with more ports open) connected to the LAN.

The problem is I haven't read a description of how or what to physically connect the second NIC card to! The best I've come up with is a double NAT arrangement:

[HTML]
           +-------------------------------+
           |                               |
           |        I N T E R N E T        |
           |                               |
           +-------------------------------+
                            |
                            |Internet
                            |staticIP
                      +-----------+               +-----------+
                      |  Router1  |               | Linux     |
                      |   NAT1    |               | server    |
                      +-----------+      private1 |           |
        private1_IP      |    |          staticIP | eth0      |
        +----------------+    +------------------>| www       |
        |                                         | ssl       |
        v                                         | dns?      |
 +-------------+                                  |           |
 |   Router2   |                                  |           |
 |    NAT2     |                                  |           |
 |    DHCP     |                                  |           |
 +-------------+                         private2 |           |
  |  |  |  |  |                           dhcpIP  | eth1      |
  |  |  |  |  +---------------------------------->| admin     |
  |  |  |  |                                      | webmin?   |
  |  |  |  |                                      | samba?    |
  |  |  |  |                                      +-----------+
  V  V  V  V                                 
  internal LAN                               
[/HTML]

To keep the design simple and reliable, I would like to use conventional routers/NAT boxes to supply my internal LAN. i.e. the Linux server will only serve the outside world.

What are the advantanges and disadvantages of this method?
What is the conventional method of connecting a server and sharing a single IP?

Thanks in advance for your insights.

---

### Post by arava on 2006-10-16
Does the above make sense at all?
I may be way off the mark, so I'd like to know before I do something stupid...!

What is the "normal" way one connects a LAMP server safely to the Internet while allowing administration over a second NIC?

---

### Post by mips on 2006-10-17
Whatever you do, do NOT enable any routing between the two internal nics.

Ideally the server should sit in a DMZ between two firewalls, just my opinion.

Lock down all ports and then open the ports as needed. If you want to give your friends acces from the web (which I dont like) use something that is secure like ssh.

The two nics would also be in seperate networks subnets.

I suggest you read up on DMZ and firewalling. Also on hardening a linux server. Better option might even be a openbsd box

---

### Post by arava on 2006-10-18
Hi mips

> Whatever you do, do NOT enable any routing between the two internal nics.
Agreed.


> Ideally the server should sit in a DMZ between two firewalls
I had planned to use the port forwarding of Router1 i.e. just 80 for www. I don't know what telnet+ssl uses but I could find that out. Another possibility for updating the html files (that I know next to nothing about) is WebDAV. I know Apache supports it, but how does one enable it?


> Lock down all ports and then open the ports as needed.
Definitely.


> The two nics would also be in seperate networks subnets.
I need more help here. Are you saying that the double NAT is not a good idea?
Actually this is my original question. How best to physically connect the two ethernet NICs to protect my home machines and still allow only one of the server's NIC's to be exposed?


> I suggest you read up on DMZ and firewalling. Also on hardening a linux server.
Yes, I am trying to read some fat linux books instead of a nightcap  :-)


> Better option might even be a openbsd box
I've tried to use freebsd, but I found it too difficult for my level of Linux knowledge. I'm also considering using the stable Debian version because of the package install tool.
Why do you recommend openbsd?

---

### Post by mips on 2006-10-18
> **arava said:**
> 
1- I need more help here. Are you saying that the double NAT is not a good idea?
Actually this is my original question. How best to physically connect the two ethernet NICs to protect my home machines and still allow only one of the server's NIC's to be exposed?

2- Why do you recommend openbsd?

1- TCP/IP design does not allow for two interfaces on the same host to be in the same network, period. It's a design/rule thing and once you sit down and think about it for a while you understand why. I have posted on this issue before but to lazy to look for the posts now.

2- As far as I'm aware it's the most secure OS out there. Not the fastest or the latest & greatest packages but the most secure.

---

### Post by arava on 2006-10-18
> **mips said:**
> 1- TCP/IP design does not allow for two interfaces on the same host to be in the same network, period. It's a design/rule thing and once you sit down and think about it for a while you understand why.Good to know. Thank you.


I'm still wondering if the double NAT arrangement is necessary. If all I have to do is to have different (logical) subnets, then can both server NICs be physically connected to two ports on the same router? In other words, in the diagram above, replace Router2 with a switch/hub.

The two NICs wouldn't "see" each other... right?

Can Router1 "port forward" to a host outside it's own subnet?

---

### Post by mips on 2006-10-19
> **arava said:**
> 
The two NICs wouldn't "see" each other... right?


Depends on what layer of the OSI model you are talking about. At layer 2  and below it's kinda transparent.

---

### Post by merkur2k on 2006-10-19
ok, i am confused...
while a dmz between two firewalls would be the most secure setup, its not like you are running a network for bank or something.
having the server connected to the private net along with the rest of your PCs with hole(s) in the nat router for the various services is plenty secure for a home network. in order to get to the other machines, the linux machine still has to be compromised first. add some access control lists to the various admin services to allow your friends in.
by "telnet+ssl" I will assume you mean ssh, which runs on port 22.

---

