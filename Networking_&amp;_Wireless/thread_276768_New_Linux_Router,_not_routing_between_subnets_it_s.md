---
title: "New Linux Router, not routing between subnets it seems, nor is it forwarding ports"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by geekman on 2006-10-13
Hi, just a few days ago i started to setup a new linux router for all of my servers because i found my existing linksys router often crashed in the middle of intense ssh sessions :D. Although a firmware upgrade did the trick i still want to tackle this for when i get my static IP's as it is much more flexible. Anyways, heres the setup. I have my linksys modem/router on 192.168.0.1 which connects all my M$ boxes on 192.168.0.0/24 to the LAN. Then there are my servers, currently about five, all on 192.168.1.0/24. My new router has two interfaces eth0 and eth1, eth0 connects to a switch which connects to my servers, eth1 connects to the linksys which provides the WAN connection. eth0 has an IP of 192.168.1.1 and eth1 has 192.168.0.112, i will be referring to the linux router as niobe (probably :)). Here is my best attempt at a network diagram:


WWW-> Connected to linksys|->M$ PC's
WWW->Linksys(192.168.0.1)->(192.168.0.112-eth1)->Niobe->(192.168.1.1-eth0)->Switch->Servers(192.168.1.0/24)

Ok so heres where i have gotten so far, niobe is able to get internet access and is able to ping to boxes on either subnet. The servers are able to ping each other, niobe and niobe's  other IP on the other subnet (192.168.0.112) but they cannot ping the linksys router. The M$ boxes can ping niobe on its side (192.168.0.112) but can only ping anything on the other subnet if i add the route:
`route ADD 192.168.1.0 MASK 255.255.255.0 192.168
.0.112`

If i dont do this tracert shows that when pinging the box will try to go through the WAN to contact any box on the other subnet. I have been able to get the internet working fully on my servers, except i dont really know how, i did add i route after it broke itself for the third time but this only fixed up pinging on one box. And despite all this there is one server which, when the internet works on all other servers, it can ping and visit any other IP but cannot resolve anything, even if i specify the public IP of a DNS that it can ping for to perform is lookups.

I should also mention that niobe is using IPTables but i am not too sure that it is affecting the connectivity of the servers as i turned off iptables (removed all rules, chains etc...) and still no luck. I dont really know why it is not forwarding correctly but i will post my current iptables script so someone can help. Also i should say that my linksys has NAT and its firewall on, also it is set to direct all ports (something like 0-63353) to the linux router. I know this works because i am able to ssh into the linux router from a remote location, but no other services are being forwarded onto their servers.

I really hope someone can help me out here as i am all out of ideas, and fast because i am coming up on 2weeks of downtime, not that anyone will notice :D but its not good to make a habbit of it.

PS Maybe its not necessary but i forgot to mention all ubuntu boxes are running 5.10

Thanks in Advance

---

### Post by TheWizzard on 2006-10-13
did you do a firmware upgrade on your linksys router? 
for me this was a huge stability gain.

---

### Post by geekman on 2006-10-13
> **TheWizzard said:**
> did you do a firmware upgrade on your linksys router? 

Yes i did:
> **geekman said:**
> Although a firmware upgrade did the trick i still want to tackle this for when i get my static IP's as it is much more flexible.
I now have the latest firmware, and yes it works fine now, but i still want the extra flexibility and probably power of the linux router. When i get some static IP's, instead of assigning each one to a different server's interface, all of them will be assigned to the router, which will be directly connected to the WAN. Then i will have different port forwards setup for each static Public IP to go to a certain server's private IP. To me this setup seems much easier to manage especially if the ammount of servers begins to grow.

Thanks in Advance

---

### Post by TheWizzard on 2006-10-14
mmm, does ring a bel somewhere... but i'm affraid i can't remember what to do exactly. maybe your bookstore/library has nice books on networking. the wiley bibles on linux are quite comprehencive. 
you can also check the yolinux tutorials: 
[http://yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)
or post your question on a more geeky forum. check debian. redhat may provide good general information, but differs when it comes to details. 
hope this helps.

---

### Post by geekman on 2006-10-14
I will do so, and thankyou for your help. I should probably also add to help anyone else out, i was able to get the servers connected to the linksys and therefore the WAN with the following rules:
iptables --insert OUTPUT 1 --source 0.0.0.0/0.0.0.0 --destination 192.168.0.0/24 --jump ACCEPT --out-interface 'eth1'
iptables --insert INPUT 1 --source 192.168.0.0/24 --destination 0.0.0.0/0.0.0.0 --jump ACCEPT --in-interface 'eth1'
iptables --insert FORWARD 1 --source 0.0.0.0/0.0.0.0 --destination 192.168.0.0/24 --jump ACCEPT --out-interface 'eth1'
iptables --insert FORWARD 1 --source 192.168.0.0/24 --destination 0.0.0.0/0.0.0.0 --jump ACCEPT
iptables --table nat --append POSTROUTING --out-interface 'eth1' --jump MASQUERADE
iptables --append FORWARD --protocol tcp --tcp-flags SYN,RST SYN --jump TCPMSS --clamp-mss-to-pmtu

* Thanks to incon on the AustNet IRC Ubuntu channel for this

But i am yet to get the home lan talking with the servers, without the route i mentioned earlier. I am thinking of setting up a bridge but i cant get to grips with it at the moment. I may post back here in a few days for help with port forwarding.

Thanks

---

### Post by mips on 2006-10-14
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

