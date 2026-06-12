---
title: "Networking Disabled"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Quarkrad on 2009-02-10
I got myself in a mess attempting to configure a dedicated IP address for my Ethernet connect PC (Ubuntu 8.10).  After all sorts of issues I have finally got it back to square one with automatic connection.  I have internet/ethernet connectivity, it all works, but there is a warning triangle bottom right of my network icon in the task bar.   When I put the cursor over the icon and left click it says:  NetworkManager is not running.  Sometimes I get a message Networking Disabled - yet it is working. At the moment if I right click the icon and choose Edit Connections, there is nothing in the Wired tab.  Before I had something like eth0.
As it all now works I am a bit nervous to change anything but when you boot up and the desktop loads it looks like (the warning triangle on the icon) there is no network connection.  Very odd.

---

### Post by x33a on 2009-02-10
see under system -> preferences -> session if the network manager is on the list or not.

---

### Post by newbee70 on 2009-02-10
> **Quarkrad said:**
> I got myself in a mess attempting to configure a dedicated IP address for my Ethernet connect PC (Ubuntu 8.10).  After all sorts of issues I have finally got it back to square one with automatic connection.  I have internet/ethernet connectivity, it all works, but there is a warning triangle bottom right of my network icon in the task bar.   When I put the cursor over the icon and left click it says:  NetworkManager is not running.  Sometimes I get a message Networking Disabled - yet it is working. At the moment if I right click the icon and choose Edit Connections, there is nothing in the Wired tab.  Before I had something like eth0.
As it all now works I am a bit nervous to change anything but when you boot up and the desktop loads it looks like (the warning triangle on the icon) there is no network connection.  Very odd.

have you right clicked on your network icon and clicked on enable networking?

---

### Post by Quarkrad on 2009-02-11
Thanks for replies.  Network Manager is shown as running in System, Pref, Sessions and Networking is Enabled if I right click on the icon.  I would expect these to be so because I do having networking and it all works.  It's just that UBUNTU is reporting to me that Networking is disabled and there is a warning triangle on top of the two PC's networking icon in the task bar.   Not sure why Ubuntu thinks it has no networking when it does?????

---

### Post by pastalavista on 2009-02-11
in terminal type ```
ifconfig
``` and post the output here.

---

### Post by x33a on 2009-02-11
did you create the connection using pppoeconf?

if that's the case, then the network manager will show the error. and if this is the case, simply remove network manager from startup, and you are good to go.

---

### Post by Quarkrad on 2009-02-14
this is the ouput of ifconfig

liz@liz-winfast:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6c:de:29:85  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fede:2985/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6141620 (6.1 MB)  TX bytes:824852 (824.8 KB)
          Interrupt:19 Base address:0xe400 

liz@liz-winfast:~$ 


I do not believe I created a connection using pppoeconf as I do not know what pppoeconf is specifically but it is possible it was created automatically.


Thanks for help - I still have great connectivity to the internet - everything is fine apart from these strange messages from Ubuntu telling me I have no connection????

---

