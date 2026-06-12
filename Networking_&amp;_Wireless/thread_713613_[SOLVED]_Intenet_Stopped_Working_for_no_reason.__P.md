---
title: "[SOLVED] Intenet Stopped Working for no reason.  Please help!"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by witeboy724 on 2008-03-02
I know there have been posts similar to this before, but none of them seem to solve my problem.  I accidentally hit my power cord and unplugged my computer, then when it restarted the internet wouldn't connect anymore.  I'm pretty new to Ubuntu (7.10), but I checked all of the ifconfig outputs and everything else that I saw suggested and nothing seemed wrong that I could tell.  I'm connected through my college network, so I don't really have any control over the router or anything.  I have to register my mac address for it to even connect.  Restarting and reseting the network and all that didn't help.  So I'm thinking maybe some settings got messed up with the unexpected restart or something.  Is there an easy way to get Ubuntu to reset all the networking settings?  Or something else I could try?  Any help would be much appreciated!

---

### Post by witeboy724 on 2008-03-02
Also... the icon in the top right says the wired network is connected.  Sorry I forgot to mention this was a wired connection and that everything seems fine, but no internet.

---

### Post by superprash2003 on 2008-03-03
type ifconfig in your terminal and post results here

---

### Post by abedbajia on 2008-03-03
i have the same problem only internet on wireless is working
this is result of ifconfig on my pc 

[HTML]eth0      Link encap:Ethernet  HWaddr 00:1B:24:86:58:5F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:9F:E0:6D  
          inet addr:10.0.9.70  Bcast:10.0.9.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe9f:e06d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:996 errors:0 dropped:80 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:375681 (366.8 KB)  TX bytes:57450 (56.1 KB)
          Interrupt:16 Base address:0xc000 Memory:f4000000-f4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/HTML]

---

### Post by abedbajia on 2008-03-03
sorry i forgot to say that synaptic isn't working on both wired and wireless connection 

and when i posted the result of ifconfig i was on wireless connection so that is why no ip or mask on etho0 otherwise everything seems ok

---

### Post by superprash2003 on 2008-03-03
you have 2 adapters eth0 and eth1 .. so i presume 1 is wired and 1 is wireless..eth0 doesnt seem to be getting an ip... go to system->administration->network->choose eth0 and select properties.. incase its set to roaming mode , change it to dhcp or static depending on your setup..
  also type ping google.com in your terminal and post results here.. just to know if you can ping or not!!

---

### Post by boeing777 on 2008-03-03
hi guys, i'm having the exact same problem, i hiberated my computer and the screen turned black so i restarted my computer, ever since then, my internet stopped working, everything is fine, ip address, dns.

both wireless and wired doesn't work now.

---

### Post by boeing777 on 2008-03-03
i can ping my router, but not clients connected to the router, can't ping google either


i have dual boot with vista, internet is working fine on vista.

---

### Post by superprash2003 on 2008-03-03
are you sure you are getting an ip address?? you can find out that by typing ifconfig

---

### Post by boeing777 on 2008-03-03
yes, i'm getting an ip. i can even see my laptop connected in the router's configuration web interface.  it was working last night before  hibernation failure. please help, i've been looking for a solution for hours.

---

### Post by superprash2003 on 2008-03-03
which router are you using?? are you connecting via LAN or USB?

---

### Post by boeing777 on 2008-03-03
i'm using a TPLink router, all computers connected to the router are working fine. even my dual boot windows vista.  i tried restarting the interface, it still doesn't work.  is there any way to reset network settings??

---

### Post by witeboy724 on 2008-03-03
Here are the ifconfig results:

eth0      Link encap:Ethernet  HWaddr 00:0B:6A:A3:C2:70   
          inet6 addr: fec0::8:20b:6aff:fea3:c270/64 Scope:Site 
          inet6 addr: 2002:9207:cab1:8:20b:6aff:fea3:c270/64 Scope:Global 
          inet6 addr: fe80::20b:6aff:fea3:c270/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:16144 errors:0 dropped:0 overruns:0 frame:2488 
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1665188 (1.5 MB)  TX bytes:54575 (53.2 KB) 
          Interrupt:18 Base address:0xd400  
 
eth0:avah Link encap:Ethernet  HWaddr 00:0B:6A:A3:C2:70   
          inet addr:169.254.8.1  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0xd400  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:5032 (4.9 KB)  TX bytes:5032 (4.9 KB) 
 
vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01   
          inet addr:172.16.235.1  Bcast:172.16.235.255  Mask:255.255.255.0 
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08   
          inet addr:172.16.146.1  Bcast:172.16.146.255  Mask:255.255.255.0 
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Keep in mind that I don't have any control over the router.  I tested both the port I'm plugged into and also the cable.  It seems like the problem is in my computer so I just want to replace the network settings with the originals.  I really want to avoid reinstalling Ubuntu if I can...  Any ideas?

---

### Post by boeing777 on 2008-03-03
i finally solved my problem!!! it was VMWARE Server that's causing my problem.  When I installed Vmware, it asked me for all these network settings that I don't know, I think i screwed up there.  Now, I disabled networking for my VMWARE Virtual Machine, my internet is back now.

---

### Post by witeboy724 on 2008-03-03
Oh wow, thanks!  That worked for me too.  I just had to disable the networking on VMware Server and it connected to the internet again.  I'm not sure why this was the problem.  I had it working on both Ubuntu and XP thru VMware before, and I wasn't even running VM when my internet wasn't working.  This is a good solution for now, I guess I need to figure out where I went wrong in the VMware settings.  Thanks again!

---

### Post by boeing777 on 2008-03-03
i don't know too much about networking, but i think it has something to do with bridging or NAT between vmware and ubuntu,

---

### Post by abedbajia on 2008-03-04
[HTML]eth0      Link encap:Ethernet  HWaddr 00:1B:24:86:58:5F  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe86:585f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6920 (6.7 KB)  TX bytes:15490 (15.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19132 (18.6 KB)  TX bytes:19132 (18.6 KB)
[/HTML]
this is result of ifconfig

see there is an ip i duuno what to do

---

