---
title: "simple home network problem"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by uptwn4500 on 2009-04-20
Hi,

I have been searching the forums for hours but I can't seem to make my home network work.  I am trying to share files between a ubuntu 8.1 laptop and a vista desktop via wireless router.  It was working previously but stopped for some reason.  I have samba installed and like I said it had all been working out of the box perfectly for months.  When I click on places-network, there is an icon for "windows network" but when I click it it says "unable to mount location/ failed to retrieve file list from server"  Before it used to show the workgroup.  From my vista computer (my vista computer actually finds my ubuntu computer) it says my hostname is invalid; I changed my hostname but I still get the same message.  In reading these forums all day it seems the following information is helpful in diagnosing problems so here it is:

__________________________________________________________________________

andy@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:23:95:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:55:16:7b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe55:167b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4604531 (4.6 MB)  TX bytes:719968 (719.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-55-16-7B-36-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



________________________________________________________________________

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
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

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.3          192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.3          192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

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

_________________________________________________________________________

Please help!  I am really stuck- I am clueless as to why my computers wont connect anymore:(

---

### Post by lisati on 2009-04-20
It might need a little more tinkering. A "how to" on setting up samba which works with 7.04, 8.10 and 9.04 (I haven't used 8.04) can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
I've used it to get four different machines with different flavours of Windows & Ubuntu exchanging files without too many hassles.

---

### Post by uptwn4500 on 2009-04-20
Just wanted to point out that both computers can connect to the internet, just not to each other...

thanks again

---

### Post by inobe on 2009-04-20
> **uptwn4500 said:**
> Just wanted to point out that both computers can connect to the internet, just not to each other...

thanks again

follow steps 1 to 11 under **"Share files and folders with other computers"**

then steps 1 to 6 under [B]"Accessing shared folders via Windows"
[/B]

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

if your fast enough and don't make any mistakes you should have a fully setup home network in ten minutes.

---

### Post by uptwn4500 on 2009-04-20
Hi,
Thanks so much for the help.

Unfortunately, I ran through both links and tutorials that you all have recommended step by step and the problem remains unchanged.  I am not sure what I have done wrong but my computers are unable to find each other on the network... when I try to type in the ip address from the vista machine I now get the error message "A device attached to the system is not functioning"

As before both computers can connect to the internet through the same wireless router, just cant find each other- and this has all been working flawlessly for months before it seemed to stop working inexplicably...

Any other ideas?

Thanks,
Andy

---

### Post by uptwn4500 on 2009-04-20
but, I just realized if I type the ip address manually into nautilus smb://192.168.1.2 it will connect again?!  why wont it do that automatically anymore?  It used to all just happen by itself...

---

### Post by cybergalvez on 2009-04-20
I've had trouble with connecting via the Places>Network too sometimes.  Have you tried to just use the places>Connect to server option? does that give you the same problems?  Does Vista report that anyone is trying to connect to it? can you connect to your vista computer with another windows comuputer?

---

### Post by uptwn4500 on 2009-04-20
cybergalvez

if I try using the "connect to server" using the vista computer's name "kates-pc" I get the same "unable to mount / failed to retrieve files from server" error message.  If I try to connect using the same ip address that just worked in nautilus I get a message that reads , "cannot display location / No application is registered as handling this file"  I dont have another windows computer to try this out with...

Thanks,
Andy

---

### Post by uptwn4500 on 2009-04-20
just to throw it out there, my Vista computer is dual-boot with ubuntu.  I just rebooted in to ubuntu to see if both ubuntu machines could find each other but they cant...  again, both can connect to the internet throught he same router but just cant find each other :(

So, I guess I can't blame the Vista computer as much as I'd like too ;)

---

### Post by inobe on 2009-04-20
it looks like you have file and folder sharing via nautilus, i have no experience with that setup.

---

### Post by uptwn4500 on 2009-04-20
> **inobe said:**
> it looks like you have file and folder sharing via nautilus, i have no experience with that setup.
lol perhaps I should upgrade this thread to be "a moderately complicated home network probem"

Thanks anyways, I appreciate the link which will be quite useful if I end up having to reinstall to fix this

Thanks,
Andy

---

### Post by cybergalvez on 2009-04-20
> **uptwn4500 said:**
> cybergalvez

if I try using the "connect to server" using the vista computer's name "kates-pc" I get the same "unable to mount / failed to retrieve files from server" error message.  If I try to connect using the same ip address that just worked in nautilus I get a message that reads , "cannot display location / No application is registered as handling this file"  I dont have another windows computer to try this out with...

Thanks,
Andy

what happens if you use the IP address with connect to server?

---

### Post by RMBoschetti on 2009-04-29
Hi there! I have a network problem, could someone help me?

I have 3 machines connected through a WI-FI DLS modem - router
1) File server - Vista
2) Desktop - Ubuntu 9.04
3) Laptop - Ubuntu 9.04

The server is able to see the 2 machines and to get in the shared folders which I defined through Samba , but the Ubuntu machines don't see Vista. (Samba is installed, testparm doesn't find particular errors and the network users are active as explained in many forums).

Vista is set properly because every folder has been shared and if I connect other Vista machines they can easily get in the network.

When I select the "connect to server" in Ubuntu and enter the IP of the server,  user name and group name , I get only errors. I tried to ping Vista and everything is ok, then I tried, instead of entering the server IP (192.168.2.2 got from Vista through ipconfig in DOS) , to use the server name, and in this case it continues to ask me the password. Btw the ubuntu machine is able to connect perfectly to the internet.

But what is getting me crazy is that one day, while I was trying to fix this problem, the server asked to reboot for other reasons, so I did it and when it returned to my laptop, without having done anything , I could see my server and the HD connected to it.
When I restarted Ubuntu it was impossible to connect again to the server.

This laptop has a dual boot (Vista) and if I use Vista it's able to connect perfectly to the server, so it shouldn't be a hardware problem.

Ok I should post my smb.conf but after having changed so many times the file (I spent hours to read "how to" and tips in a lot of forums) I don't think that it could help.

Any ideas?????????

---

