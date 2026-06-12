---
title: "Need to reboot to fix WAN"
date: 2017-07-18
forum: Networking &amp; Wireless
---

### Post by Matthew_Johnston on 2017-07-18
Hi Forum,

I originally installed Ubuntu for use as a desktop environment, but I've switched to a hybrid desktop/server system where my laptop sits at home and I either SSH or NX into it from my ipad or a less powerful machine whenever I want or need its power. I've recently hit a roadblock. I'm running 16.04 Studio.
I have it connected to both LAN and WLAN so I have a backup in case one fails. Both interfaces are connecting via DHCP but the router always assigns them the same static IP when it recognizes their MAC addresses. I then have obscure ports opened on the router forwarded to give me independent access to SSH and NX on both network interfaces (and a free DDNS setup for my router).
At some unpredictable interval after boot I will lose WAN connectivity. At this point I can ssh into my router, ssh into my computer from the router, reboot it, and regain access from WAN. I have not had the wherewithall to test whether I have outgoing WAN access or not when this happens. I also didn't save the dmesg output last time that happened but I can tell you that I remember it happened after the computer tried to renew its DHCP addresses on both interfaces.

I will update with better info next time this happens, likely tomorrow.
Thanks for any preliminary thoughts you might be able to offer though!

---

### Post by BenginM on 2017-07-19
Salutations! and welcome to the forums .

If i got this right, I think what you want to solve this issue is to set networking manually without using a GUI like network manager or wicd , using ..
/etc/wpa_supplicant.conf

etc/networking/interfaces

[maybe this is a good reference ]("https://ubuntuforums.org/showthread.php?t=684495"):  

If you're having  networking issue , you'll probably want to pepole here to see some logs .. so please se the stick thread on the main netwoking page .. you might want to run the wierless info script later.

---

### Post by Matthew_Johnston on 2017-07-20
Thanks for the reply!

It's not that my network connections aren't  working, I have a working connection on both interfaces every time I  boot. It's just that they both fail at the same time for some reason I  can't explain.
Here are some clues:
```
$ ifconfig
enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
       inet 192.168.0.150  netmask 255.255.255.0  broadcast 192.168.0.255
       inet6 fe80::2ad2:44ff:fe18:8aa5  prefixlen 64  scopeid 0x20<link>                                                      
       ether 28:d2:44:18:8a:a5  txqueuelen 1000  (Ethernet)                                                                    
       RX packets 6288786  bytes 1834334484 (1.8 GB)                                                                           
       RX errors 0  dropped 0  overruns 0  frame 0                                                                             
       TX packets 7208163  bytes 9556073732 (9.5 GB)                                                                           
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0                                                              
       device interrupt 19                                                                                                                           
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536                                                                                   
       inet 127.0.0.1  netmask 255.0.0.0                                                                                       
       inet6 ::1  prefixlen 128  scopeid 0x10<host>                                                                            
       loop  txqueuelen 1000  (Local Loopback)                                                                                 
       RX packets 8860  bytes 772745 (772.7 KB)                                                                                
       RX errors 0  dropped 0  overruns 0  frame 0                                                                             
       TX packets 8860  bytes 772745 (772.7 KB)                                                                                
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0                                                                 
                                                                                                          
wlp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500                                                         
       inet 192.168.0.151  netmask 255.255.255.0  broadcast 192.168.0.255                                             
       inet6 fe80::6a17:29ff:fe4f:d6c5  prefixlen 64  scopeid 0x20<link>                                                     
       ether 68:17:29:4f:d6:c5  txqueuelen 1000  (Ethernet)                                                                    
       RX packets 580647  bytes 126870925 (126.8 MB)                                                                           
       RX errors 0  dropped 0  overruns 0  frame 0                                                                             
       TX packets 97368  bytes 16028959 (16.0 MB)                                                                              
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 

```
The last entries in dmesg:
```
$ dmesg
[89024.759084] wlp8s0: authenticate with 04:a1:51:16:aa:8a                                                           
[89024.761896] wlp8s0: send auth to 04:a1:51:16:aa:8a (try 1/3)                                                      
[89024.783172] wlp8s0: send auth to 04:a1:51:16:aa:8a (try 2/3)                                                      
[89024.807451] wlp8s0: authenticated                                                                                 
[89024.808491] wlp8s0: associate with 04:a1:51:16:aa:8a (try 1/3)                                                    
[89024.850350] wlp8s0: associate with 04:a1:51:16:aa:8a (try 2/3)                                                    
[89024.885401] wlp8s0: associate with 04:a1:51:16:aa:8a (try 3/3)                                                    
[89024.924025] wlp8s0: association with 04:a1:51:16:aa:8a timed out                                                  
[89025.076623] wlp8s0: authenticate with c4:a8:1d:86:bb:70                                                           
[89025.079088] wlp8s0: send auth to c4:a8:1d:86:bb:70 (try 1/3)                                                      
[89025.081928] wlp8s0: authenticated                                                                                 
[89025.082517] wlp8s0: associate with c4:a8:1d:86:bb:70 (try 1/3)                                                    
[89025.089135] wlp8s0: RX AssocResp from c4:a8:1d:86:bb:70 (capab=0x431 status=0 aid=5)                              
[89025.103356] wlp8s0: associated                                                                                    
[91367.677476] wlp8s0: authenticate with 70:62:b8:67:0b:1c                                                           
[91367.680477] wlp8s0: send auth to 70:62:b8:67:0b:1c (try 1/3)                                                      
[91367.682812] wlp8s0: authenticated                                                                                 
[91367.683871] wlp8s0: associate with 70:62:b8:67:0b:1c (try 1/3)                                                    
[91367.690761] wlp8s0: RX AssocResp from 70:62:b8:67:0b:1c (capab=0x411 status=0 aid=3)                              
[91367.697700] wlp8s0: associated                                                                                    
[94184.517392] wlp8s0: disconnect from AP 70:62:b8:67:0b:1c for new auth to 04:a1:51:16:aa:8a                        
[94184.519887] wlp8s0: authenticate with 04:a1:51:16:aa:8a                                                           
[94184.524494] wlp8s0: send auth to 04:a1:51:16:aa:8a (try 1/3)                                                      
[94184.545140] wlp8s0: send auth to 04:a1:51:16:aa:8a (try 2/3)                                                      
[94184.566829] wlp8s0: send auth to 04:a1:51:16:aa:8a (try 3/3)                                                      
[94184.593874] wlp8s0: authentication with 04:a1:51:16:aa:8a timed out                                               
[94184.744854] wlp8s0: authenticate with 70:62:b8:67:0b:1c                                                           
[94184.747192] wlp8s0: send auth to 70:62:b8:67:0b:1c (try 1/3)                                                      
[94184.749536] wlp8s0: authenticated                                                                                 
[94184.750899] wlp8s0: associate with 70:62:b8:67:0b:1c (try 1/3)                                                    
[94184.755038] wlp8s0: RX AssocResp from 70:62:b8:67:0b:1c (capab=0x411 status=0 aid=3)                              
[94184.761175] wlp8s0: associated

```

Oddly, it doesn't mention my other interface, enp7s0 yet it also does not have WAN access at this point.

Pinging my gateway:
```
$ ping 192.168.0.1                                                                 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.                                                                 
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.87 ms                                                            
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=4.17 ms                                                            
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=6.77 ms                                                            
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=26.3 ms                                                            
^C                                                                                                                   
--- 192.168.0.1 ping statistics ---                                                                                  
4 packets transmitted, 4 received, 0% packet loss, time 3004ms                                                       
rtt min/avg/max/mdev = 3.874/10.291/26.345/9.337 ms

```

Pinging google.ca:
```
$ ping google.ca                                                                   
PING google.ca (172.217.2.99) 56(84) bytes of data.                                                                  
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=29 ttl=55 time=12.1 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=30 ttl=55 time=25.7 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=31 ttl=55 time=16.1 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=32 ttl=55 time=17.3 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=33 ttl=55 time=21.3 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=34 ttl=55 time=18.4 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=35 ttl=55 time=18.0 ms                               
64 bytes from yyz10s05-in-f3.1e100.net (172.217.2.99): icmp_seq=36 ttl=55 time=17.9 ms                               ^C                                                                                                                   
--- google.ca ping statistics ---                                                                                    
46 packets transmitted, 8 received, 82% packet loss, time 45892ms                                                    
rtt min/avg/max/mdev = 12.147/18.401/25.758/3.685 ms

```

Traceroute to google.ca:
```
$ traceroute google.ca                                                             
traceroute to google.ca (172.217.2.163), 30 hops max, 60 byte packets                                                 
1  router1.astrosynthesist (192.168.0.1)  5.427 ms  5.417 ms  5.412 ms                                                      
2  * * *                                                                                                            
3  * * *                                                                                                             
4  * * *                                                                                                             
5  * * *                                                                                                             
6  * * *                                                                                                             
7  * 108.170.250.241 (108.170.250.241)  16.104 ms 108.170.250.225 (108.170.250.225)  16.082 ms                       
8  108.170.226.211 (108.170.226.211)  16.037 ms 108.170.226.209 (108.170.226.209)  24.416 ms  24.416 ms              
9  yyz10s06-in-f3.1e100.net (172.217.2.163)  24.411 ms  25.159 ms  25.141 ms

```

Note that my default interface is enp7s0, and I don't know how to make wlp8s0 do the ping or traceroute, however I know the results would be similar as I don't have incoming WAN access to either interface anyways when this happens.

---

### Post by BenginM on 2017-07-20
I'am aware that you have a network connection , it was a shoot in the dark as it's hard to tell what's going on without looking at the logs ,but now we see..

" disconnect from AP 70:62:b8:67:0b:1c for new auth to 04:a1:51:16:aa:8a "

is it possible that it keeps authenticating to one of two APs, each represents a frequency band transmitted by the Router (2.4GHz & 5GHz)!

if that's the case , you may want to lock your connection to the AP's BSSID" setting your AP's BSSID in network manager.

dose enp7s0 shows up with ifconfig -a !

though , i'am not sure as to why you're tryin' to trace-hop google.ca .. do you think you're getting latency lag from your ISP/router!

wait what, how is it that enp7s0 is the default , but wlp8s0 is in use! is 7s0 in monitor mode or something..!

you may want to run the wireless info script in 
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

and post the result in a [CODE] tag

---

### Post by Matthew_Johnston on 2017-07-21
It is very possible that it is authenticating between different APs. I  have three APs in my house, with 3 2.4 GHz sources and 2 5 GHz sources,  however I don't think that is currently the problem (though I'll see  what happens if I lock my wifi to one BSSID like you say).
```
 $ ifconfig -a
         enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu  1500                                                                    
        inet 192.168.0.150  netmask 255.255.255.0  broadcast 192.168.0.255                                                      
        inet6 fe80::2ad2:44ff:fe18:8aa5  prefixlen 64  scopeid 0x20<link>                                               
        ether 28:d2:44:18:8a:a5  txqueuelen 1000  (Ethernet)                                                            
        RX packets 6501754  bytes 1965662466 (1.9 GB)                                                                   
        RX errors 0  dropped 0  overruns 0  frame 0                                                                     
        TX packets 7369436  bytes 9581674047 (9.5 GB)                                                                   
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0                                                      
         device interrupt  19                                                                                                                

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536                                                                            
        inet 127.0.0.1  netmask 255.0.0.0                                                                               
        inet6 ::1  prefixlen 128  scopeid 0x10<host>                                                                    
        loop  txqueuelen 1000  (Local Loopback)                                                                         
        RX packets 14885  bytes 1330007 (1.3 MB)                                                                        
        RX errors 0  dropped 0  overruns 0  frame 0                                                                     
        TX packets 14885  bytes 1330007 (1.3 MB)                                                                        
         TX errors 0  dropped 0 overruns 0  carrier 0  collisions  0                                                                               

wlp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu  1500                                                                    
        inet 192.168.0.151  netmask 255.255.255.0  broadcast 192.168.0.255                                                  
        inet6 fe80::6a17:29ff:fe4f:d6c5  prefixlen 64  scopeid 0x20<link>                                                
        ether 68:17:29:4f:d6:c5  txqueuelen 1000  (Ethernet)                                                            
        RX packets 920744  bytes 199637605 (199.6 MB)                                                                   
        RX errors 0  dropped 0  overruns 0  frame 0                                                                     
        TX packets 177936  bytes 29005742 (29.0 MB)                                                                     
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
When  both enp7s0 and wlp8s0 are connected to a network, my computer uses  enp7s0 as its default interface to make connections over LAN and WAN. My  router shows activity on 192.168.0.150, not 192.168.0.151 unless I  specifically connect to 151.
I'm trace hopping google.ca because my  WAN speed drops to either zero or near zero on both enp7s0 and wlp8s0.  I'm just providing as much information as I can in the hopes that it  gets somewhere. Look at my ping to google.ca. I had an 82% packet loss.  Since I don't know how to specify which interface to ping from, that  ping was only done over the default enp7s0. I should also do a ping from  wlp8s0 but I don't know how to do that yet.
I'll do the wireless info script a bit later and post the results. Thanks again for your help.

---

### Post by Matthew_Johnston on 2017-07-22
I ran the script and wasn't too happy with all of the personal information in the output. I might edit the file to remove some things like all of my saved SSIDs and such, but I think that there must be another way to track the problem since this problem occurs with both my wireless and my ethernet at the same time. If I have time to go through the output of that script and only post the relevant, non-personal stuff, I will.

---

### Post by Matthew_Johnston on 2017-08-08
The problem seems to go away when my ethernet connection is terminated.  Surprisingly there are no log updates to go with that. So the problem is  not with wifi, it has something to do with the ethernet.

---

### Post by BenginM on 2017-08-09
Well, that's a good catch , now you may wish to start troubleshooting the Ethernet wired whilst wifi is disabled.

---

