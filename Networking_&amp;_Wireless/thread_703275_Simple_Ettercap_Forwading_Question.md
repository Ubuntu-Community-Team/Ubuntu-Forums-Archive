---
title: "Simple Ettercap Forwading Question"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by phoenix910 on 2008-02-21
Hey guys, I am using ettercap and can run it fine on BackTrack, but on Ubuntu I get:
SEND L3 ERROR: 28 byte packet (0800:01) destined to 10.0.0.3 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted) 
) 
SEND L3 ERROR: 28 byte packet (0800:01) destined to 10.0.0.1 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted) 
) 

and so on. Now I have done
echo 1 > /proc/sys/net/ipv4/ip_forward

Which should set up ip forwarding yeah? And I have uncommented the iptables lines in the /etc/etter.conf file. What else can I do to get it forwarding?

-Stephen

---

### Post by SpaceTeddy on 2008-02-21
i don't know how what exactly ettercap has to do with forwarding packets, since it is a sniffer/anaylser. 

To Allow of ip packets thought your machine, that command is quite enought. I would suggest that you also enable it in the sysctl.conf (found in /etc) so that it automaticially enabled upon boot.

Having ip forwarding enables means that you can use your machine as a gateway for other,  give that your machine has internet access AND that you have proper network setup (which might involve a NAT rule if you are using it to agregate a network to use a single IP).

---

### Post by phoenix910 on 2008-02-23
Hi, thanks for the reply. Ettercap can also be used for MITM attacks via ARP poisoning, and as of that, it needs to pass the packets through. I have already tried editing that file, and it still won't work. What else can I do?

-Stephen

---

### Post by SpaceTeddy on 2008-02-23
oh, you want to do nasty things with it... well, then my only guesses would be
1.) your iptable says you are not allowed to send those packets
2.) you are not running ethercap as root

remeber... do not use any software on others that you do not want used on you !!!
respect privacy

---

### Post by tjwoosta on 2008-05-03
i realize its been a while that this post has been unanswered but i too am having the same problem with ettercap in ubuntu hardy 
(in gutsy everything worked fine)

i have tried running as root but i always get the same error as mentioned above 
(when im not running as root i cant even select an interface so i know its definatly working as root)

and just to let you guys know im not using this for illegal purposed or anything nasty like that, i am simply trying to test my own network security (trying to learn so i know how to defend myself against attackers)

---

### Post by phoenix910 on 2008-05-03
> **SpaceTeddy said:**
> oh, you want to do nasty things with it... well, then my only guesses would be
1.) your iptable says you are not allowed to send those packets
2.) you are not running ethercap as root

remeber... do not use any software on others that you do not want used on you !!!
respect privacy

Thank you for your help, and don't worry, I'm not using this for nasty things. I simply have two computers and a router sitting next to me that I am trying to do this with, in order to grasp a better concept of how these things work. I do respect people's privacy, and wouldn't do this to someone.

And tjwoosta, I am going to try this one more time now that I have successfully done it on other OS's, and now that Hardy is out. If I get it working, I shall let you know.

-Stephen

---

