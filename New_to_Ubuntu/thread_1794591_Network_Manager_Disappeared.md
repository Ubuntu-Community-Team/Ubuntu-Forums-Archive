---
title: "Network Manager Disappeared"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by merelda on 2011-07-01
Hi everyone, I'm an absolute newbie on the forum to please bear with my ignorance :) 

I was initially trying to connect my ubuntu and win7 laptop via lan cable to create file sharing. I followed some post and I got stuck, and realised that I had "sudo apt-get purge" my network manager... And not only the network manager disappeared, but my wireless connection stopped working.

I tried to manually reinstall Network Manager by downloading the package on my windows laptop, but a lot of problem occurred such as intltool too old (solved) and no gettext (unsolved)... 

I'm wondering if there's an easier way of getting my Network Manager back or at least get my internet connection back????


This is the response I got from lshw:
*-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:06:03.0
                logical name: eth2
                version: 05
                serial: 00:12:f0:e0:d5:48
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:b8008000-b8008fff



This is the response I got from iwconfig:



lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.


This is the response I got from ifconfig:


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10208 (10.2 KB)  TX bytes:10208 (10.2 KB)




Thanks so much!!!! any input is appreciated!!!!

---

### Post by jtarin on 2011-07-01
Do you have the Ubuntu install CD? Insert your CD then open Synaptic Package Manager and from the search box locate "network manager" right-click and install.

---

### Post by shibu_sawyer on 2011-07-01
what version of ubuntu are you using, if it is 10.10,pls go to system->preferences-->network connections and check whether your connections are available.. or u got to install the manager using the ubuntu cd..

---

### Post by merelda on 2011-07-02
Hi sorry for the late reply.

I am using 10.10, and I don't have the ubuntu cd.. I think I installed it with a flash drive and I reformatted the drive. 

I don't have network connections, I only have network proxy? I'm not sure whether I have connections or not because I don't have my network manager and I don't know how to check through terminal.. 

Thanks so much for the help:)

---

### Post by amjjawad on 2011-07-02
> **merelda said:**
> Hi sorry for the late reply.

I am using 10.10, and I don't have the ubuntu cd.. I think I installed it with a flash drive and I reformatted the drive. 

I don't have network connections, I only have network proxy? I'm not sure whether I have connections or not because I don't have my network manager and I don't know how to check through terminal.. 

Thanks so much for the help:)

Hello and Welcome :)

How do you connect to the internet? Wire? Wireless?

It should be under: System > Preferences > Network Connections

Package Name is: **network-manager-gnome**

Open Synaptic (System > Administration > Synaptic) and type the name of the package in Search Box and hit Enter. If it's listed there and the Check Box is GREEN then it's installed already.

That's the easiest way to check.

I guess the indicator applet has gone so you don't see it anymore on your top panel.

---

### Post by merelda on 2011-07-02
hey thanks for the fast reply,

I'm connecting through wireless, but even if I plug the ethernet cable in I still can't connect to the internet..
I can't use synaptic nor apt-get install because I don't have internet connection, I downloaded the network manager package with my windows pc but I seem to have a lot of dependencies missing and it's taking forever to find all of it and install all of them manually.

I guess the easiest way is to get a 10.10 cd then?

thanks so much :)

---

### Post by amjjawad on 2011-07-02
Yes, get a LiveCD.

---

