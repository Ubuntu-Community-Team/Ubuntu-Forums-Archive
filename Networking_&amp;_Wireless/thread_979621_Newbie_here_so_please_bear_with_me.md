---
title: "Newbie here so please bear with me"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by cookey6109 on 2008-11-12
Just installed Ubantu last night and I cant get onto my home network. This is really new to me so if anyone can please help with getting my IP address settings sorted. It might take a little time getting used to so please bear with me.

Just the best place to start and getting connected with help me massively. Thanks
Alan

---

### Post by Sealbhach on 2008-11-12
Hi,first we need to see what kind of network cards you have. Type this in a terminal and copy and paste the result here:

```
lshw -C network 
```


.

---

### Post by beilwei123 on 2008-11-12
I fully support you, this is my task. I hope you better[**Shanghai massage**|**Shanghai escort**](http://www.lovemassage.com.cn)|[**massage Shanghai**|**massage in Shanghai**](http://www.lovemassage.com.cn)|[**Shanghai massage**|**Shanghai escort**](http://www.lovemassage.cn)|[**massage Shanghai**|**massage in Shanghai**](http://www.lovemassage.cn)|[**Shanghai massage**|**Shanghai escort**|**massage Shanghai**|**massage in Shanghai**](http://www.okmassage.net)

---

### Post by superprash2003 on 2008-11-12
also post output of ifconfig

---

### Post by cookey6109 on 2008-11-12
> **Sealbhach said:**
> Hi,first we need to see what kind of network cards you have. Type this in a terminal and copy and paste the result here:

```
lshw -C network 
```


.

Warning you should run this program as a supoer-user.
*-network
description: Ethernet Interface
product: Intel Corporation
physical id 8
bus info pci@0000:03:08.0
logical name eth0
version 04
serial 00:16:76:ab:77:56
witdth 32bits
clock 33MHZ
capabilities bus_master cap list ethernet physical
configuration broadcast=yes driver=e100 driver version 3.5.23-k4NAPIfirmware=n/a latency 64 max latency=56 mingnt=8 module=e100 mulicast =yes
*-network Disabled
description ethernet interface
physical id 2
logical name pan0
serial ca:39:15:7f:32:ac
capabilities ethernet physical
configuration broadcast=yes driver=bridge driverversion=2.3 firmware=n/a multicast=yes

---

### Post by cookey6109 on 2008-11-12
> **superprash2003 said:**
> also post output of ifconfig

Also noticed that when I went into network manager it was set on loopback to the glorious 127.0.0.1

---

### Post by jonobr on 2008-11-12
Hello

As per superprash2003 post, go to application-> accessories->terminal.
When it opens enter ifconfig and post the results here, 
IT looks like its seeing your device you need to see what its getting when it comes up,
cheers

---

### Post by cookey6109 on 2008-11-12
> **jonobr said:**
> Hello

As per superprash2003 post, go to application-> accessories->terminal.
When it opens enter ifconfig and post the results here, 
IT looks like its seeing your device you need to see what its getting when it comes up,
cheers

ethO    Link encap:Ethernet  HWaddr 00:16:76:ab:77:56
        UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
        RX packets:7 errors:0 dropped:0 overruns:0 frame:0
        TX packets:11 errors :0 dropped :0 overruns:0 carrier:0
        colloisions:0 txqueuelen:1000
        RX bytes:3070 (3.0kb)  TX bytes:2924 (2.9kb)

lo      Link encap: local Loopback
        inet addr:127.0.0.1 Mask 255.0.0.0
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:246 errors:0 dropped:0 overruns:0 frame:0
        TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:15408 (15.4kb)  TX bytes:15408 (15.4kb)

---

### Post by cookey6109 on 2008-11-12
> **jonobr said:**
> Hello

As per superprash2003 post, go to application-> accessories->terminal.
When it opens enter ifconfig and post the results here, 
IT looks like its seeing your device you need to see what its getting when it comes up,
cheers

just clicked on connection information and been given what it called active Network Connection ip address,dns,primary route subnet all perfect but now need to connect to www still not working?

---

### Post by cookey6109 on 2008-11-12
> **cookey6109 said:**
> just clicked on connection information and been given what it called active Network Connection ip address,dns,primary route subnet all perfect but now need to connect to www still not working?

now im really confused went into Terminal and done ifconfig and it gave me the 127.0.0.1 address again but still showing my 192 address in the Active Connections???????

---

### Post by jonobr on 2008-11-12
Hello


HAve you been working on your ethernet interface?

What I see as strange is that I notice the MTU size for eth0 is set to 64? it should be a lot higher, around 1500 for the ethernet cards.

When running ifconfig, only use ifconfig eth0

lo is your internal loopback address, eth0 is the one you want to work with.

---

### Post by cookey6109 on 2008-11-12
> **jonobr said:**
> Hello


HAve you been working on your ethernet interface?

What I see as strange is that I notice the MTU size for eth0 is set to 64? it should be a lot higher, around 1500 for the ethernet cards.

When running ifconfig, only use ifconfig eth0

lo is your internal loopback address, eth0 is the one you want to work with.

ok and how do i make those changes. Also in Linux what are the correct proxy settings?

---

### Post by jonobr on 2008-11-12
To change the MTU size you need to actually go and specifically modify files so they survive a reboot which made me think you had modified them for some reason.

Heres some quick info on modifying your MTU, but I would be cautious about changing this at it must have been changed to that for a reason.
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html)



For changing proxy settings its usually just edit-> preferences, advanced and then the network tab.
Select connection and the proxy settings should be in there.
However, if your not using a proxy then you shouldn't have to worry about this.

Good look and again,,,,,,, Careful with the MTU

---

### Post by superprash2003 on 2008-11-13
your ifconfig output doesnt show any ip like 192.x.x.x then how can you see it?

---

### Post by cookey6109 on 2008-11-13
> **superprash2003 said:**
> your ifconfig output doesnt show any ip like 192.x.x.x then how can you see it?

when i click the connection information icon top right it shows active network connections. All the correct info is up there and ready to go. Just have no internet connectivity yet

---

### Post by cookey6109 on 2008-11-13
> **jonobr said:**
> To change the MTU size you need to actually go and specifically modify files so they survive a reboot which made me think you had modified them for some reason.

Heres some quick info on modifying your MTU, but I would be cautious about changing this at it must have been changed to that for a reason.
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Tweaking_MTU_Settings.html)



For changing proxy settings its usually just edit-> preferences, advanced and then the network tab.
Select connection and the proxy settings should be in there.
However, if your not using a proxy then you shouldn't have to worry about this.

Good look and again,,,,,,, Careful with the MTU

tried to do this and it gave me the message
SIOCSIFMTU: Operation not permitted

Any ideas
Remember I am a newbie on Linux
Thanks

---

### Post by cookey6109 on 2008-11-13
> **cookey6109 said:**
> tried to do this and it gave me the message
SIOCSIFMTU: Operation not permitted

Any ideas
Remember I am a newbie on Linux
Thanks

learning fast though

---

### Post by Sealbhach on 2008-11-13
Put "sudo" before the command. This gives you temporary system administrator privileges for this command.


.

---

### Post by cookey6109 on 2008-11-13
ok i managed to change the mtu to 1500 but only temporalary and the internet still was not working ?
 any ideas guys?

---

### Post by jonobr on 2008-11-13
Ok

Do another ifconfig for us and post to see whats what.
Recommend starting some ping tests to see whats happening.

in a terminal

ping 127.0.0.1 
if it works
ping the ipaddress reported (hopefully) in ifconfigs response

if that works type nslookup pingplotter.com
see what it says back to you , it should give an answer like
216.92 or so,

if that fails, ping your default router gateway,
if you did not change it, Im guessing its 192.168.1.1.
If that doesnt respod it may be just because ICMP is blocked or the wrong IP address.
Do a traceroute pingplotter.com.
See what that does, if that doesnt work to a traceroute to the ip address of pingplotter.com 

end up pinging pingplotter.com


Post back any findings

---

### Post by superprash2003 on 2008-11-14
post output of ifconfig one more time please..And as mentioned above ping your gateway and post output..

---

