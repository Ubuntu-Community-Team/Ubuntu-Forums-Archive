---
title: "FIrewall problem"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by draco86 on 2007-02-20
I configured firestarter to be permessive by default with the outbound traffic and I allowed aMule in the inbound traffic.

Firestarter  works, but deny me to surf on the Internet.

Why?

---

### Post by TheWizzard on 2007-02-20
open firestarter, click the events tab. 
now try to connect to the internet. do you see events?

---

### Post by BrowneR on 2007-02-21
i have a similar problem myself.

i had firestarter up and running fine however i have had to purge it and reinstall and now i am experiencing similar problems.

when firestarter is running i can ping remote hosts, resolve hostnames, and things such as bittorent run fine however i cannot browse with firefox.

as soon as i stop firestarter firefox works fine. i have no proxies or fancy stuff setup in firefox.

in firestarters event log i see inbound connection replys from the remote site i am trying to access being blocked which is why firefox fails to load the site. outbound requests get sent fine but when the remote site trys to connect in with a reply it is being blocked. these are on some high port >30000. the remote site seems to retry and then eventually give up.

maybe an issue with connection tracking?

i am running a custom compiled 2.6.20 kernel with netfilter and all relevant connection tracking built as modules. maybe netfilter is broken or misconfigured somehow?

```

sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  speedtouch.lan       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  speedtouch.lan       anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
ACCEPT     icmp --  anywhere             anywhere            icmp host-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp timestamp-request 
ACCEPT     icmp --  anywhere             anywhere            icmp timestamp-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-request 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-reply 
LSI        icmp --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
LSI        udp  --  anywhere             anywhere            udp dpt:33434 
ACCEPT     icmp --  anywhere             anywhere            icmp host-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-request 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-reply 
LSI        icmp --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  ChrisWL.lan          speedtouch.lan      tcp dpt:domain 
ACCEPT     udp  --  ChrisWL.lan          speedtouch.lan      udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6890 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6890 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (6 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST reject-with icmp-port-unreachable 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     icmp --  anywhere             anywhere            icmp echo-request reject-with icmp-port-unreachable 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere    
```

---

### Post by draco86 on 2007-02-27
When the firewall blocks my connection I can't suft on the Internet and I can't ping any IPs.

And I in the Event tab firestarter don't show anything.

---

### Post by TheWizzard on 2007-02-27
> **draco86 said:**
> When the firewall blocks my connection I can't suft on the Internet and I can't ping any IPs.

And I in the Event tab firestarter don't show anything.

the event tab should show something if you ping to outside.

your outbound policy should be permissive!

---

### Post by Platinum89 on 2007-02-27
How does one even get Firestarter in the system to begin with? I've searched the update manager and my system. It doesn't exist in either case.:confused: 

(Ubuntu 6.06)

---

### Post by TheWizzard on 2007-02-27
> **Platinum89 said:**
> How does one even get Firestarter in the system to begin with? I've searched the update manager and my system. It doesn't exist in either case.:confused: 

(Ubuntu 6.06)

```
sudo aptitude install firestarter
```

aptitude? read: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by draco86 on 2007-02-27
> **TheWizzard said:**
> the event tab should show something if you ping to outside.

your outbound policy should be permissive!

My outbound policy is permissive!!

However... 

I forgot to say that I have a adsl connection (pppoe) created with pppoeconf and sometimes linux create many pppoe connection, so I have ppp0, ppp1, ppp2.
But I have configured the connection correctily.

So I think that the firewall proble is related with this problem (the firewall is configured to check ppp0).

So... what I have to do?

---

### Post by TheWizzard on 2007-02-27
> **draco86 said:**
> My outbound policy is permissive!!

However... 

I forgot to say that I have a adsl connection (pppoe) created with pppoeconf and sometimes linux create many pppoe connection, so I have ppp0, ppp1, ppp2.
But I have configured the connection correctily.

So I think that the firewall proble is related with this problem (the firewall is configured to check ppp0).

So... what I have to do?

ok. open firestarter
preferences -> firewall -> network settings

change the internet connected network device to the one you're actually using and start configuring

---

### Post by Platinum89 on 2007-02-27
> **TheWizzard said:**
> ```
sudo aptitude install firestarter
```

aptitude? read: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

That did the trick. Thank you for the help ;)

---

### Post by draco86 on 2007-02-27
> **TheWizzard said:**
> ok. open firestarter
preferences -> firewall -> network settings

change the internet connected network device to the one you're actually using and start configuring

It doesn't exist preferences -> firewall -> network settings.

---

### Post by ihatethedekoys on 2007-02-28
I was having this same problem with firestarter. I ended up removing it and iptables.

I'm on 2.6.20.1 kernel.

---

### Post by TheWizzard on 2007-02-28
> **draco86 said:**
> It doesn't exist preferences -> firewall -> network settings.

yes it does. what do you see when you open preferences??

---

### Post by draco86 on 2007-02-28
> **TheWizzard said:**
> yes it does. what do you see when you open preferences??

I see many things (like about me, gnome control center, theme) but no firewall.

Firestarter is in Administration.

PS: I have forgotten to say that aMSN WORKS, is the only application that bypass the firewall

---

### Post by auroraborealis on 2007-03-01
He meant within Firestarter.

Open Firestarter > Preferences (next to Lock Firewall) > Firewall > Network Settings

---

