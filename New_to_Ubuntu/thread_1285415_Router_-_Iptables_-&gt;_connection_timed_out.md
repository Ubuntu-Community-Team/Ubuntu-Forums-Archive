---
title: "Router - Iptables -&gt; connection timed out"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by trigsenior on 2009-10-07
Hello =)


Mindless comment
I am not sure if this is the right section , Was unsure on which of the section to put it in , so as im a begginer went here.
end/


Problem
I recently gained access to my inventel livebox and installed ssh ( dropbear). That listens on port 22 and i can connect to THOUGH only on my local network. I want to be able to connect from out side my network , though when i try [email]root@lbox.homelinux.com[/email] (Real ip Feel free to port map) i get connection timed out.
end/


I am not sure but i think it is a iptables problem, Here is ifconfig and iptables -L 



```


ifconfig
br0       Link encap:Ethernet  HWaddr 00:23:48:07:3E:80  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1430356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1433749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:970963154 (925.9 MiB)  TX bytes:993620850 (947.5 MiB)

br1       Link encap:Ethernet  HWaddr 00:23:48:07:3E:7E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:23:48:07:3E:7E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:23:48:07:3E:7F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:590646 errors:10 dropped:0 overruns:0 frame:0
          TX packets:789328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138984406 (132.5 MiB)  TX bytes:857262878 (817.5 MiB)
          Interrupt:30 Base address:0x6800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213595 (208.5 KiB)  TX bytes:213595 (208.5 KiB)

nas1      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576458 errors:0 dropped:1 overruns:0 frame:0
          TX packets:439661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:591879998 (564.4 MiB)  TX bytes:124099540 (118.3 MiB)

nas2      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nas3      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nas4      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nas5      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nas6      Link encap:Ethernet  HWaddr 00:23:48:07:3E:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-Point Protocol  
          inet addr:86.214.27.61  P-t-P:86.214.27.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:565942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:586868661 (559.6 MiB)  TX bytes:109946177 (104.8 MiB)

usb0      Link encap:Ethernet  HWaddr 00:23:48:07:3E:80  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wl0       Link encap:Ethernet  HWaddr 00:19:7E:29:A3:BE  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:601 errors:0 dropped:0 overruns:0 frame:36088
          TX packets:24262 errors:706 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:131564 (128.4 KiB)  TX bytes:8906780 (8.4 MiB)


```


```
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
input_hotspot  all  --  anywhere             anywhere            
web_in     all  --  anywhere             anywhere            
voip_in    all  --  anywhere             anywhere            
voip_in    all  --  anywhere             anywhere            
input_firmware_push  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
block      all  --  anywhere             anywhere            
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
DROP       tcp  --  anywhere             anywhere            state INVALID,NEW,RELATED 
DROP       udp  --  anywhere             anywhere            state INVALID,NEW,RELATED 
DROP       tcp  --  anywhere             ANantes-157-1-20-61.w86-214.abo.wanadoo.fr tcp dpt:www flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:22 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
forward_hotspot  all  --  anywhere             anywhere            
upnp       all  --  anywhere             anywhere            
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
ACCEPT     tcp  --  anywhere             emilien-desktop     tcp dpt:22 
block      all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
voip_out   all  --  anywhere             anywhere            
voip_out   all  --  anywhere             anywhere            

Chain block (2 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp state NEW,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:20 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:20 state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            tcp dpt:netbios-ns 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-ns 
DROP       tcp  --  anywhere             anywhere            tcp dpt:netbios-dgm 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-ssn 

Chain forward_hotspot (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain input_firmware_push (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  80.12.110.129        ANantes-157-1-20-61.w86-214.abo.wanadoo.fr tcp dpt:50805 flags:FIN,SYN,RST,ACK/SYN limit: avg 5/min burst 1 

Chain input_hotspot (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain upnp (1 references)
target     prot opt source               destination         

Chain voip_in (2 references)
target     prot opt source               destination         

Chain voip_out (2 references)
target     prot opt source               destination         

Chain web_in (1 references)
target     prot opt source               destination         

```


I added to The iptables 

```
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

Little effect.

---

### Post by Sarmacid on 2009-10-07
Seems that server is behind a router. If it is, you have to configure the router to forward traffic on port 22.

---

### Post by trigsenior on 2009-10-07
I can conenct to the host behind the router , though i want to connect to the router its self.

---

### Post by Sarmacid on 2009-10-07
You need to go to the administration interface of your router and get it to forward incoming traffic on port 22 to the machine you want to access with ssh. Then you can ssh with your router's address and will be redirected to your machine.

---

### Post by trigsenior on 2009-10-07
Never very good at explaing =/

Here goes ;

At the momment to connect to my router on port 22,
I have to connect to myrouter.com -p 22222 which forwards me to
my server behind the router. So


me => ssh(myrouter.isp) => router listens port -p 2222 => forward to 192.168.0.26(My server)

I want the router to not forward me but as to act as a server 
so

me => ssh(myrouter.isp) => connects to router(ssh)


As at the moment i can only access the router(ssh) if i connect to the server behind the router.

---

### Post by running_rabbit07 on 2009-10-07
I don't think that is possible.

---

### Post by trigsenior on 2009-10-08
how can i drop theses rules 

```

DROP       tcp  --  anywhere             anywhere            state INVALID,NEW,RELATED 
DROP       udp  --  anywhere             anywhere            state INVALID,NEW,RELATED 

```

Ok i managed to make it work 


```

#!/bin/sh
echo "Stopping firewall and allowing everyone..."
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

```


Though now speak of the wicked i can't access the server behind the router , how can i forward port 2222 to a host behind the network?

If i try to access the web interface i get 

```


401 Unauthorized
Authorization required.


```

Il have a look at Html files

---

### Post by trigsenior on 2009-10-08
Ok i worked out howto forward to my internal host

/mnt/jffs2/jffs2_3/root # iptables -t nat -A PREROUTING -p tcp -i <external interface> -d <external ip> --dport 22222 -j DNAT --to 192.168.1.180:22             

/mnt/jffs2/jffs2_3/root # iptables -A FORWARD -p tcp -i <internal interface> -d  <internal ip>  --dport 22  -j ACCEPT

---

