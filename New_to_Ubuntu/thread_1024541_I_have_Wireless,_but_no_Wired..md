---
title: "I have Wireless, but no Wired."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by CCCody on 2008-12-29
I don't have Wired internet, and am currently using someones wireless to type this. 

All the lights on my modem are on and I don't know where to begin.

When I start up the computer I get Auto Etho or something, but it doesn't connect to the internet. I think Ubuntu detects my ethernet card, I ran the System test or whatever.

I'm just really confused and would like some help, thanks.

I'm running 8.10

---

### Post by tibellus on 2008-12-29
Hi. Have you tried typing in a terminal "iwconfig"? This will show you if Ubuntu detected any wireless networks and their strenght. Please post a reply with your result.

---

### Post by CCCody on 2008-12-29
When I typed that in I got this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

---

### Post by RichardLinx on 2008-12-29
> **tibellus said:**
> Hi. Have you tried typing in a terminal "iwconfig"? This will show you if Ubuntu detected any wireless networks and their strenght. Please post a reply with your result.
His wireless is working fine, It's his wired connection that is causing him trouble. @OP, I don't know much about this sort of thing but it may be a good idea to post what kind of wireless card you have, If possible I suggest you try checking if your modem is working correctly by trying another computer/OS on it.

---

### Post by CCCody on 2008-12-29
> **RichardLinx said:**
> His wireless is working fine, It's his wired connection that is causing him trouble. @OP, I don't know much about this sort of thing but it may be a good idea to post what kind of wireless card you have, If possible I suggest you try checking if your modem is working correctly by trying another computer/OS on it.

It is working correctly, I just reinstalled from Windows and it was working fine then.

All the lights are on the modem and I'm currently stuck using my neighbor's wireless.

It automatically sets up with Auto Eth0 or something when I start up, but it won't connect to the internet.

---

### Post by tibellus on 2008-12-29
Nice. You've got to set up a few things. Go to System -> Administration -> Network. There you will see the available connections. You will need to unlock the menu first. Select the "Wireless Connection" entry afterwards. Click on "Properties". In the new window that will appear, uncheck "Enable roaming mode" if you have it checked. At ESSID enter the name of your wireless network, in case it doesn't show up in the drop-down list (and I think it doesn't). Select the type of authentication you're using and for "Connection Settings" use DHCP for the moment. Click on "Ok" and then close the Network Settings app. Let me know of the results.

---

### Post by tibellus on 2008-12-29
Okay, I'm stupid. :| I don't know why I thought you're having a problem with your wireless.

---

### Post by RichardLinx on 2008-12-29
It's ironic that the wireless works but the problem is with the wired after hearing so many stories about Linux having horrid wireless support. :) After a quick search (Google) I found that this command might be of some use:

```
ifconfig -a
```

I have no Idea what It does but It may be of some use, post the output here since It's probably of some use.

---

### Post by RichardLinx on 2008-12-29
> **tibellus said:**
> Okay, I'm stupid. :| I don't know why I thought you're having a problem with your wireless.

It happens to the best of us. :D

---

### Post by CCCody on 2008-12-29
This is what I get from that command:

> eth0      Link encap:Ethernet  HWaddr 00:1d:09:54:43:1d  
          inet6 addr: fe80::21d:9ff:fe54:431d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95658 (95.6 KB)  TX bytes:37694 (37.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:44:c6:80:4d  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fec6:804d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33277 errors:0 dropped:0 overruns:0 frame:36048
          TX packets:22687 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45729014 (45.7 MB)  TX bytes:2024179 (2.0 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

pan0      Link encap:Ethernet  HWaddr 06:1a:11:30:b4:d2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by labinnsw on 2008-12-29
I had a similar problem once and I knew the modem was working because I dual booted with Windows and a fresh installation of Ubuntu on which it worked.

To solve the problem I backed up my information (bookmarks, data, and Evolution) to an external hard drive. Did a fresh installation of Ubuntu with the network connection in place and restored my settings and stuff. Took a lot less time than it took to figure out what the problem was.

---

### Post by RichardLinx on 2008-12-29
Hmmm... Well by the looks of it your modem has been detected but for some reason it isn't sending or receiving packets, I don't know to much about networking but judging from this (I very well could be wrong) I'd say you just need to configure your wired connection properly. As to how... [http://ubuntuforums.org/showthread.php?t=167534](http://ubuntuforums.org/showthread.php?t=167534)

That thread should point you in the right direction.

---

### Post by CCCody on 2008-12-29
> **RichardLinx said:**
> Hmmm... Well by the looks of it your modem has been detected but for some reason it isn't sending or receiving packets, I don't know to much about networking but judging from this (I very well could be wrong) I'd say you just need to configure your wired connection properly. As to how... [http://ubuntuforums.org/showthread.php?t=167534](http://ubuntuforums.org/showthread.php?t=167534)

That thread should point you in the right direction.

No dice :(

I tried this but it didn't seem to work either.

[http://www.linuxquestions.org/questions/linux-hardware-18/no-wired-internet-connection-in-ubuntu-8.10-684272/](http://www.linuxquestions.org/questions/linux-hardware-18/no-wired-internet-connection-in-ubuntu-8.10-684272/)

---

