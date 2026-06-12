---
title: "Samba shares: work under Windows, don't work under Ubuntu"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by jemdos on 2008-04-30
Greetings from Sunny Spain 8)

My little homelan is composed of a laptop windows computer & two desktop computers, say A & B, under Ubuntu 6.06 and 7.04. Both of them are file servers, so I have some folders shared using samba. The laptop is a new Dell and I could get it cheaper with Vista than with Ubuntu (go figure...)

So, the shares are under Ubuntu. The windows laptop computer can access them faultlessly. But A & B cannot see each other shares. They cannot even see the "workgroup" lan.

I've tried several faqs, including some from samba.org. But I've not nailed down the problem. I've only noticed that, althought the /etc/samba/smb.conf states that dns are not allowed, when nmbd ask for A from B (or B from A) it goes outside my homelan and to Internet (it checks for IP adresses of my ISP).

Because I can dual boot A & B to windows xp, I've checked out whether under windows A can "see" ubuntu B shared folders and viceversa. They both do.

Looks like the samba-server side works perfectly, but the client side does not for no reason I am aware of. It's driving me nuts.

Any help would be very very very much appreciated. Thanks for reading this desperate plea 8)

---

### Post by Iowan on 2008-04-30
> **jemdos said:**
>  Both of them are file servers, so I have some folders shared using samba.
Are they set up as servers - or as desktops running Samba Server?  I suppose actual question is whether they have GUI or not. 
... Which leads to: how are you checking from A>B or B>A.  
I'm wondering if the servers have an addressing problem - since they're trying to go outside the LAN.

OK, I've babbled enough.

---

### Post by MaindotC on 2008-04-30
Are the shares password protected?

---

### Post by jemdos on 2008-05-02
Thanks for answering, sorry about myself answering with such delay. 8(

The desktop computers are desktops running samba server, they both do other duties 8)... and they both run samba clients. Both run under gnome GUI all the time.
Checking A>B and B>A is done atempting to do Places > Net (my system is not in english) under the gnome top menu bar. 
I do think there's an addressing problem, but I think there's also a firewall problem (iptables/firestarter) thought I'm not sure how to rule it out.
For instants, I allow SMB traffic to the IPs of my LAN, but it keeps stopping part of the traffic. It rejects some connections to the typical SMB ports, thought I keep saying to the firewall it has to allow them. And then again, the windows machine does indeed connect!

The shares are password protected? Hmm. One share is a NTFS folder, the other one is a linux folder. Both are shared write protected. The user/owner of both folders/files is the same, the password is the same, and the windows machine does connect to both, after asking for the correct user and password. But under linux, both A and B *even* don't see the workgroup, just that there exist a "windows lan". Moreover, disabling the firewall (firestarter) does allow one computer (A) to "see" there is a homelan, that there are three computers, but it can only browse itself. The other one (B) just sees there's a homelan workgroup, but it cannot browse anything.

---

### Post by jetsam on 2008-05-02
Have a look at this page:
[http://www.swerdna.net.au/linhowtosambabrowse.html]("http://www.swerdna.net.au/linhowtosambabrowse.html")
Although Mandriva focused, it generally applies to Ubuntu and has some good advice on stabilizing network browsing.  

If one of your servers is on all the time, I'd recommend option three -- a wins server.  If you try this, be sure you only designate one of the machines as a wins server-- two will cause conflicts.  I use Samba as a wins server, and it works very well.  I think it actually makes Windows network neighborhood browsing faster.    

If you don't have a server on all the time, you might try option two.

**Edited to add**: Firestarter can cause trouble with Samba.  It might be easier to uninstall it, fix samba browsing, and then re-install Firestarter and figure out how to configure it.

---

### Post by MaindotC on 2008-05-02
At this time you cannot connect to password-protected shares using Hardy.  See the post in my signature.

---

### Post by jemdos on 2008-05-03
Greetings from Sunny Spain

Thanks to all the people who have answered my question 8) The issue is not solved yet, but I've learned a lot from you all (and with my struggle against computer gnomes ;) ).

I've almost ruled out the firewall as the culprit of this strange behaviour. I've uninstalled firestarter and things were unchanged. I have not the knowledge to battle with iptables, thought I think the traffic it keeps stopping has nothing to do with my problem. But I have to investigate that more.

I've successfully connected directly through the shares, using a web browser with the smb://user@A/sharedfolder url or under Places > Connect to server dialog. But I have to give computer all the data needed to connect: computer server, shared item, workgroup name and user. I of course have used on both computers the smbclient -a and -d commands. (I'm typing this thing without checking correct computer grammar, I think you'll understand... it's 08:00 am here and I'm writting all this before leaving home for several hours).

*But* I've narrowed the issue to at least *two* strange behaviours. 

First, not A neither B could get the computer name of each other. In both cases they were checking it *outside* my lan. Both computer have a "dns proxy = no" statement which theoretically "prevent(s) nmbd to search for NetBIOS names through DNS" but, alas, they kept looking outside. 

As a temporal solution, and because B computer has a IP static address, I've included its name in the hosts file of A and at least A can connect directly to the shares. In order to get to the A shares from B I have to use the IP address of A (annoying but doable).

Second, to my amazement there is no way to set up correctly the domain master of the lan. It has to be A, but no matter how much I play with both smb.conf files, what I get is (a) B becomes the master or (b) there's no master. B is Ubuntu 6.06, A is 7.10.

I need that A becomes the master because (1) it has the newest files (2) it has the files I use the most (3) it has the biggest hard drive (SATA II 500GB against ATA 300GB in B) and (4) the fastest cpu. I needed B shares as a kind of backup and recovery system, so it was not needed all the time.

But I cannot understand why Ubuntu seems to override the instructions set in smb.conf files. I've checked out both samba.org and [http://www.swerdna.net.au/linhowtosambabrowse.html](http://www.swerdna.net.au/linhowtosambabrowse.html) (great link) and followed its instructions. But nmblookup -M workgroup keeps telling me A never ever gets master.

I think this w/o master situation leads to that nautilus cannot "see" my workgroup. That's the initial issue I haven't resolved yet. The windows computer does work better under this situation because it seems vista "remembers" the computers hooked to the lan. Yesterday I had an issue just when the lan got w/o master browser. Vista showed the computers in its lan folder, but then it could no reach them, with an error that such computer did not exist. At least Ubuntu does not show computers that is not "seeing".

Thanks to all, I'll try to keep you posted

---

### Post by MaindotC on 2008-05-03
At This Time You Cannot Connect To Password-protected Shares Using Hardy.  See The Post In My Signature.

---

### Post by jetsam on 2008-05-03
There's no Hardy involved here, though.  Jemdos is using 6.06 and 7.04.

------------------------

> First, not A neither B could get the computer name of each other. In both cases they were checking it *outside* my lan. Both computer have a "dns proxy = no" statement which theoretically "prevent(s) nmbd to search for NetBIOS names through DNS" but, alas, they kept looking outside.

I don't understand this either.  You may be right that the problem is related.  Judging by wireshark, this doesn't happen on my set-up, but places-->network does create a bunch of MDNS requests.  This is because of avahi, but it doesn't cause any problems for me.  

----------------------

> Second, to my amazement there is no way to set up correctly the domain master of the lan. It has to be A, but no matter how much I play with both smb.conf files, what I get is (a) B becomes the master or (b) there's no master. B is Ubuntu 6.06, A is 7.10.

This makes me think something is blocking traffic and preventing A from participating in Master Browser selection.  Use these two commands to double check your firewall:

```
sudo iptables -L
```
```
sudo iptables -t nat -n -L
```
The commands should output empty tables with policy ACCEPT, like so:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

-----------------------

One other change that might help-- in the globals section of your smb.conf files, set:
```
name resolve order = bcast host lmhosts wins
```

This change helped a number of people with browsing problems in this thread:
[http://ubuntuforums.org/showthread.php?t=685218]("http://ubuntuforums.org/showthread.php?t=685218")

-----------------------

I hope some of that helps.  These problems can be difficult.

---

### Post by jemdos on 2008-05-04
> **jetsam said:**
> 
----------------------



This makes me think something is blocking traffic and preventing A from participating in Master Browser selection.  Use these two commands to double check your firewall:

```
sudo iptables -L
```
```
sudo iptables -t nat -n -L
```
The commands should output empty tables with policy ACCEPT, like so:


Here you are:

A output
--------

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  mygateway1.ar7       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  mygateway1.ar7       anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.1.255       
DROP       0    --  BASE/8               anywhere            
DROP       0    --  anywhere             BASE/8              
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.12         mygateway1.ar7      tcp dpt:domain 
ACCEPT     udp  --  192.168.1.12         mygateway1.ar7      udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE/8              
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  192.168.1.255        anywhere            
ACCEPT     0    --  B computer name      anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:microsoft-ds 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            


B output
---------

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

        
Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.1.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.1.0/24       anywhere            udp dpt:microsoft-ds 
LSI        all  --  anywhere             anywhere            

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  mygateway1.ar7       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  mygateway1.ar7       anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  BASE/8               anywhere            
DROP       all  --  anywhere             BASE/8              
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.10         mygateway1.ar7      tcp dpt:domain 
ACCEPT     udp  --  192.168.1.10         mygateway1.ar7      udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE/8               anywhere            
DROP       all  --  anywhere             BASE/8              
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

> **jetsam said:**
> 
---------------------------------------------

One other change that might help-- in the globals section of your smb.conf files, set:
```
name resolve order = bcast host lmhosts wins
```

This change helped a number of people with browsing problems in this thread:
[http://ubuntuforums.org/showthread.php?t=685218]("http://ubuntuforums.org/showthread.php?t=685218")

-----------------------

I hope some of that helps.  These problems can be difficult.

It has helped, in the sense now Nautilus "sees" the computers and the shares. B is still not able to see A shares, but now knows there exist an A. A can see B (static IP) and its shares, but I cannot open them *unless* I connect to them first using "Places > Connect to Server". This way it asks me for the password, then successfully connects. So I'd say one issue is resolved through "bcast", but not the unability to get Netbios names correctly.

---

### Post by jetsam on 2008-05-04
OK.  Firestarter has left a lot of iptables firewall rules even though you've uninstalled it.  

I'm not very good with iptables, but I believe you're blocking broadcast traffic.  This is very likely to be causing your problems.  

Try this.  It should clear your iptables rules:

```
sudo iptables -P INPUT ACCEPT && sudo iptables -P OUTPUT ACCEPT && sudo iptables -P FORWARD ACCEPT && sudo iptables -F && sudo iptables -X
```

verify it worked with:

```
sudo iptables -L
```

---

### Post by jemdos on 2008-05-04
> **jetsam said:**
> OK.  Firestarter has left a lot of iptables firewall rules even though you've uninstalled it.  

I had uninstalled, then installed it again, because I saw no difference. I only discarded old rules and bested the others, 


 
> **jetsam said:**
> 
Try this.  It should clear your iptables rules:

```
sudo iptables -P INPUT ACCEPT && sudo iptables -P OUTPUT ACCEPT && sudo iptables -P FORWARD ACCEPT && sudo iptables -F && sudo iptables -X
```

verify it worked with:

```
sudo iptables -L
```

IT NOW WORKS!!!!

Holy cow. Don't know why, because through firestarter I supposed I had allowed SMB ports inside LAN (after all, outside the LAN the router is also supposed to stop them, but I don't trust my router much either).

I suppose I'll begin again with a short set of rules 8) And I must learn something about iptables, because it looks like firestater does not a great job setting it up.

Thanks a lot to all the people, and specially jetsam. 8) I owe you all a cyberbeer. XD

---

### Post by jetsam on 2008-05-04
Excellent.  I'm glad I could help.  :)

To tell you the truth, I don't even use Firestarter because I've read it's hard to get working with Samba.  I do think my router does a pretty good job as a firewall.

This thread on the forums looks like it has a good explanation of the problem and may help you explore further:
[Samba and Firestarter-- the real story]("http://ubuntuforums.org/showthread.php?t=190542&highlight=firestarter+samba")

---

