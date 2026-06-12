---
title: "configuring network - documentation ?"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by ndnd on 2008-11-14
Hi,
I am new to linux admininstration...I recently installed server edition of ubuntu-the latest one.

I am trying to configure my network and I have all my settings. However, I couldn't find any documentation as to what exactly should I edit etc. based on my dhcp network. 

I gathered from few sources...

That I need to edit the file below
> #sudo nano /etc/network/interfaces

AND 
I can look at the current settings by 

> sudo ifconfig
etho Link encap:Ethernet HWaddr 00:1e:37:86:6b:24
       inet addr:192.168.1.101 Bcast:192.168.1.255
       Mask:255.255.255.0
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
       Tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
       Memory : fe200000-fe220000
lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:4 errors:0 dropped:0 overruns:0 frame:0
        TX packets:4 errors:0  dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:352 (352.0 B) TX bytes:352 (352.0 B)
=====================

Question: 
Is there any documentation/tutorial for configuring dhcp , wirless..network...? If there are specific steps posted somewhere please let me know (I couldn't find them)

All I am looking for is to get my laptop - connect to the internet via Lan or wireless whichever is easier. 

I already looked at the Ubuntu documentation but could only find information on what is network etc. nothing related to configuration (maybe I missed it!) 

Any help is appreciated. 
Thanks in advance!

---

### Post by Sam Lars on 2008-11-14
[https://help.ubuntu.com/](https://help.ubuntu.com/) is very helpful for basic things like this.
Here is the internet and networks information.
[https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html)

There is also the community documentation, and here is what they have for internet and networks.
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

---

### Post by ndnd on 2008-11-15
Thanks Sam Lars,
This documentation was helpful. I somehow got my server to ping a windows machine in the same network (this was via lan). 

However, I am still not very clear. It seems there are lot more complex tasks listed...but not the simple one..

I somehow managed to start the Lan based (I simply typed my IP address settings in the 
etc/network/interfaces file 
Restarted the network 
> sudo /etc/init.d/networking restart

Question 1 :(Regard LAN)
So my question is what happens when I take my laptop to some other location ? How can I set it to expect a DHCP based IP address ?


From what I gather (> [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)) there is a network-admin app that one can use. However, the settings done through this app DO NOT write to 

> /etc/networking/interfaces

file. I would prefer to edit that file to get my network running smoothly. 

Any information that tells me the different settings or edits one can do in the file (if there are samples - of a file configured for connecting to DHCP - lan or DHCP - wireless ?)

---

### Post by Sam Lars on 2008-11-15
The network applet on the panel is the preferred method for managing network settings.  It should automatically take care of almost anything that you would need to do.  If you don't like its look and feel, you could also try Wicd.
For DHCP on an interface, you would set the interfaces file to say this for it:
```
auto eth0
iface eth0 inet dhcp
```
You also don't want to change the definition of the lo interface in that file.
Searching these forums should get you plenty of examples of /etc/network/interfaces files for you to learn from.

---

### Post by ndnd on 2008-11-17
Thanks. 
I couldn't find documentation as I was using the forum's search. Once I used 'google' search - I found all the examples. My dhcp is running great! 

Now I will be able to figure out the wireless..

---

