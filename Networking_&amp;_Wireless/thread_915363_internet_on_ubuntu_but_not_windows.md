---
title: "internet on ubuntu but not windows"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by evonwells on 2008-09-09
okay a few days ago my wireless (laptop internal hardware a toshiba M-55 satalite) was working fine under ubuntu but now it only works while i'm in windows, while in ubuntu the hardware says "connection" detected but any web broser just thinks for a bit then comes up with the error page with a big yellow triangle

---

### Post by evonwells on 2008-09-10
anyone know anything out there?

---

### Post by Muflon on 2008-09-10
If you are using a Wifi connection then try using an ethernet cable to see if that gives a different result.  This will help to narrow down the source of the problem.

Muflon

---

### Post by hawksbill on 2008-09-10
You're not giving us a whole lot to go on. How are you connecting via wifi or ethernet? Have you done any updates lately? what does your ifconfig status say? What driver are you using for your networking card?

---

### Post by evonwells on 2008-09-10
> **hawksbill said:**
> You're not giving us a whole lot to go on. How are you connecting via wifi or ethernet? Have you done any updates lately? what does your ifconfig status say? What driver are you using for your networking card?

heres the whole situation as far as I know. 

I have RECENTLY gotten ubuntu,I do not know what an IFconfig is. all I know is that after windows killed my desktop I decided to switch to ubuntu on both of my computers. The problem computer in question is a toshiba M-55 S135 laptop, the network adapter is the stock internal wireless, it worked with ubuntu up untill a few days ago and then quit, web pages act like they are loading but never can, the hardware check says i'm connected but still, no internet. When I switch to windows on the same PC (partitioned) It works fine, with no problems.

---

### Post by evonwells on 2008-09-10
I ran the Ifconfig in a terminal and it gave me this

ath0      Link encap:Ethernet  HWaddr 00:11:f5:64:94:42   
          inet6 addr: fe80::211:f5ff:fe64:9442/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:4406 (4.3 KB) 
 
ath0:avahi Link encap:Ethernet  HWaddr 00:11:f5:64:94:42   
          inet addr:169.254.6.194  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
 
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:88:a0:c5   
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
          RX packets:1248 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:63012 (61.5 KB)  TX bytes:63012 (61.5 KB) 
 
wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-64-94-42-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5639 errors:0 dropped:0 overruns:0 frame:124 
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199  
          RX bytes:694584 (678.3 KB)  TX bytes:17396 (16.9 KB) 
          Interrupt:22

---

### Post by superprash2003 on 2008-09-10
there seems to be a problem with the ip.. your not getting an ip on your wifi interface.Try using static ip address.. by going to system->admin->network and choose your wifi card and click on properties uncheck roaming mode and type in ip address manually and try

---

### Post by evonwells on 2008-09-10
i did that, entered the ip subnet and gateway all manually (got them from windows if that matters) and for the most part it's usually not on roaming mode. Any ideas?

---

### Post by hawksbill on 2008-09-12
Try this in the terminal:

sudo -i
#this puts your terminal session in super user mode.
ifconfig ath0 down

iwconfig ath0 destroy
#closes your interface connection then removes it completely
modprobe ath_pci

wlanconfig ath0 create wlandev wifi0 wlanmode sta
#creates a new interface for your driver
ifconfig ath0 up

modprobe wlan_scan_sta

wlanconfig ath0 list scan

#At this point you should get a read out of the available networks. If all goes well use your network manager to attempt a connection.

Hope this helps.

---

