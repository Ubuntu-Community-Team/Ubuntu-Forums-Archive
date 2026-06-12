---
title: "wireless problems"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by skata94 on 2009-10-06
i am running version 2.6.28-11 and i got a sony vaio with a intel Pro wireless 3945abg it says that i am still connected to the internet but wont load new pages will someone help me with my problem. The best way that i can explain wat is goin on is the internet is communicating with the compuiter then just stops but knows its still there just doesnt want to talk to it. make since? any feed back would be appreciated.

---

### Post by oboedad55 on 2009-10-07
> **skata94 said:**
> i am running version 2.6.28-11 and i got a sony vaio with a intel Pro wireless 3945abg it says that i am still connected to the internet but wont load new pages will someone help me with my problem. The best way that i can explain wat is goin on is the internet is communicating with the compuiter then just stops but knows its still there just doesnt want to talk to it. make since? any feed back would be appreciated.

It will help a lot if you post the brand name and model (if applicable) of your computer and the brand and model of your wireless adapter. If you put this command into a terminal it should list all your hardware: sudo lshw

---

### Post by wirepuller134 on 2009-10-07
Intel directed me to this page, after searching their site for the Linux driver.  [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) 
  The solution might be to simply hook up wired and do all of the updates.  This solved a connection issue with one of our Lenovo laptops with built in wireless.

---

### Post by Peter09 on 2009-10-07
have you got an ip address?

can we see the ouput of the terminal command

```
ifconfig
```

---

### Post by skata94 on 2009-10-07
> **Peter09 said:**
> have you got an ip address?

can we see the ouput of the terminal command

```
ifconfig
```


This is what i got when i put that command in terminal:

eth0      Link encap:Ethernet  HWaddr 00:13:a9:2b:cb:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20848 (20.8 KB)  TX bytes:20848 (20.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:40:a7:38  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe40:a738/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47600875 (47.6 MB)  TX bytes:1070631 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-40-A7-38-37-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by skata94 on 2009-10-07
> **wirepuller134 said:**
> Intel directed me to this page, after searching their site for the Linux driver.  [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) 
  The solution might be to simply hook up wired and do all of the updates.  This solved a connection issue with one of our Lenovo laptops with built in wireless.


Thanks tried but no luck

---

### Post by bt-linux on 2009-10-07
i am a beginner with ubuntu netbook remix 9.04

i am having problems getting on the wireless network at my school- the computer shows that it is picking up the wireless but it will not let me allow me to connect. it attempts to connect but does not.

please help!

---

### Post by skata94 on 2009-10-07
> **oboedad55 said:**
> It will help a lot if you post the brand name and model (if applicable) of your computer and the brand and model of your wireless adapter. If you put this command into a terminal it should list all your hardware: sudo lshw



I am running a sony vaio VGN-SZ230P and i have a Intel Pro Wireless 3945ABG 

I tried the terminal command and got command not found is all i got

---

### Post by skata94 on 2009-10-07
It sounds like the network at ur school is setup any big network and u need administrative privileges to connect to the internet see if u can get a ip address and subnet then see wat happens

---

### Post by Winston and Julia Smith on 2009-10-07
I'm getting a problem where is shows that I'm connected to my home network, but when I open FireFox it says "address not found" no matter which site I try to access.

---

### Post by Peter09 on 2009-10-08
Skate99, you have a connection because yo have been dealt an IP address (assuming that you have not set up a static address.) It looks to me like a permissions issue - what are you trying to connect to?

---

### Post by Peter09 on 2009-10-08
Winston and Julia - your problem looks like a DNS issue, please start a new thread on this (so as not to muddle the current one) and I will respond.

---

### Post by skata94 on 2009-10-08
> **Winston and Julia Smith said:**
> I'm getting a problem where is shows that I'm connected to my home network, but when I open FireFox it says "address not found" no matter which site I try to access.


u need to get the drivers for your wireless card and install windows wireless drivers program in the software manager and find where the driver is if u r still running windows go through the device manager to find this info out and where the driver is

---

### Post by skata94 on 2009-10-08
> **Peter09 said:**
> Skate99, you have a connection because yo have been dealt an IP address (assuming that you have not set up a static address.) It looks to me like a permissions issue - what are you trying to connect to?


I am trying to connect to a home wireless network with a 64bit security.  The host computer is running Vista

---

### Post by Peter09 on 2009-10-09
The fact that firefox does not connect is more likely to be DNS.
Try the following command in a terminal (which I presume is the ip address of your router)

```
ping 192.168.2.1
```If it works then you are connected.

Right click on the network icon and select the connection information item. It will show you some details of your connection - what is in the 'Primary DNS' field?

---

### Post by skata94 on 2009-10-11
> **Peter09 said:**
> The fact that firefox does not connect is more likely to be DNS.
Try the following command in a terminal (which I presume is the ip address of your router)

```
ping 192.168.2.1
```If it works then you are connected.

Right click on the network icon and select the connection information item. It will show you some details of your connection - what is in the 'Primary DNS' field?


in the Primary DNS field is 192.168.2.1 Which is the same as my Default route

scratch that it was pinging it then it just stopped and wouldnt load a page again i went to a friends house and connected to his wireless and it worked just fine so i think i have a problem with the router i think i have another one i am using a linksys router right now i think i got a netgear i willl change it and see if it changes anything thanks for all the help.

---

