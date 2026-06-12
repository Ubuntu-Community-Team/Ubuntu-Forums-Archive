---
title: "how to configure samba for wireless access"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by sniperweydz on 2008-04-04
hello to all,

i have a windows network at home and i installed samba on my Ubuntu machine and i was able to network all our computers. but when i use my wireless interface to access my windows network i cant see any of the computers connected in our home network.

how can i configure samba to use my wireless interface and also my wired interface?

my laptop is the ubuntu machine and it has 2 network interface.


tnx for reading this post....

---

### Post by keratos on 2008-04-04
If I understand you correctly are you saying that the machines hardwired are correctly networked and shares are visible across the LAN ?? This is my interpretation from your initial statement.

Its not entirely clear where your 802 adapter is, but I'll assume your laptop has an ethernet and an 802 wireless adapter.

Please help us in future by supplying more data whenever you post.

With this in mind then I would suggest it is not your Samba that is configured incorrectly, but your wireless interface.

Check your channel, SSID, WPA/WEP (etc) keys, Workgroup settings etc.

---

### Post by superprash2003 on 2008-04-04
yes keratos is right.. you need to check your network configuration.. please go the terminal, type ifconfig and post results here

---

### Post by sniperweydz on 2008-04-04
sorry about the lack of details. here is my situation. before we only have wired network, and i was able to network our computers and file sharing was working 100% but then i decided to get a wireless access point for my laptop ,i was able to use the wireless with internet browsing etc. but when i tried to locate the other computers in our network it is no longer visible, but before they are visible if i hard wire my laptop with our router, but when i go wireless they are no longer visible.

is there a special configuration for samba for wireless access? BTW my laptop is the one with ubuntu and samba the rest of the computers are windows

---

### Post by sniperweydz on 2008-04-04
here is the result for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:19:21:BE:59:3B  
          inet addr:192.168.3.103  Bcast:192.168.3.127  Mask:255.255.255.128
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:B8:53:FC  
          inet addr:192.168.3.5  Bcast:192.168.3.127  Mask:255.255.255.128
          inet6 addr: fe80::216:6fff:feb8:53fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4957 errors:2 dropped:2 overruns:0 frame:0
          TX packets:4597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4105526 (3.9 MiB)  TX bytes:680438 (664.4 KiB)
          Interrupt:5 Base address:0xe000 Memory:feafe000-feafefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7458 (7.2 KiB)  TX bytes:7458 (7.2 KiB)


i was using wireless when i did this....

tnx for your patience

---

### Post by superprash2003 on 2008-04-04
what is the ip address of the windows machine you want to connect to?have you tried pinging the machine?

---

### Post by sniperweydz on 2008-04-04
i tried to ping them but i cant with the wireless. with wired connection i can ping them perfectly

---

### Post by superprash2003 on 2008-04-04
are you able to ping the router?

---

### Post by sniperweydz on 2008-04-04
unfortunately i cant. but when i go to boot in windows the network files are visible even if im in wireless mode. its really strange on how i cant ping the router but i have internet access.

---

### Post by superprash2003 on 2008-04-04
what is your router's ip?

---

### Post by sjul on 2008-04-04
I'm not sure if this will help you (I'm a total newbie), but this is easy to try and it allowed me to view folders in the network:
[http://ubuntuforums.org/showthread.php?t=744517](http://ubuntuforums.org/showthread.php?t=744517)

good luck!
-Suzanne

---

### Post by keratos on 2008-04-06
Go into your routers web interface (usually something like 192.168.0.1 or 192.168.1.1 - check your router documentation).

Your router will have a "show devices connected" or "recongised". This lists the LAN ip addresses of connected nodes (your PC should be one, lets see if the wireless laptop is the other!!). Record them and post the output here.

I think you have something wrong in the laptop setup - the fact you cannot ping the router suggests its not even on the same subnet or bad/incorrect SSID/encryption. Lets start here. Post that  output.

---

