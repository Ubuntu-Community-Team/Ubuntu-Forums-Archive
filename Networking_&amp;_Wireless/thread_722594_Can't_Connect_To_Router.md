---
title: "Can't Connect To Router"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by perito on 2008-03-12
I run my Ubuntu Live CD 7.10
I do see the router, I connect to it, it asks for WPA password, I give it, it says waiting for key (84%) and stays like this forever
so I manually configure it, and make it take dhcp instead of roaming, and supply the password and name of connection, now it says (manually configured) but still no internet connection...

so I take out the CD and run Kubuntu 7.04
and guess what? it connects to the internet through the router in a sec without any problems using dhcp !!!!
WHY IS THIS HAPPENING???????????????????????

how can I get ubuntu to connect to the net?
i think its not aquring IP address successfully or something like that... but im not sure.

---

### Post by perito on 2008-03-12
I run my Ubuntu Live CD 7.10
I do see the router, I connect to it, it asks for WPA password, I give it, it says waiting for key (84%) and stays like this forever
so I manually configure it, and make it take dhcp instead of roaming, and supply the password and name of connection, now it says (manually configured) but still no internet connection...

so I take out the CD and run Kubuntu 7.04
and guess what? it connects to the internet through the router in a sec without any problems using dhcp !!!!
WHY IS THIS HAPPENING???????????????????????

how can I get ubuntu to connect to the net?
i think its not aquring IP address successfully or something like that... but im not sure.

---

### Post by perito on 2008-03-12
shouldnt it get easier and better as the versions get newer ? 
how come the old version connects ok and the newer one cant connect?

---

### Post by perito on 2008-03-12
shouldnt it get easier and better as the versions get newer ? 
how come the old version connects ok and the newer one cant connect?

---

### Post by MattBD on 2008-03-12
Have you tried it with an Ethernet connection to the router instead of wireless? That might be worth trying as if it works OK then that means it's a wireless problem, but if it doesn't then I guess it could be a more general networking issue.

---

### Post by perito on 2008-03-13
I run my Ubuntu Live CD 7.10
I do see the router, I connect to it, it asks for WPA password, I give it, it says waiting for key (84%) and stays like this forever
so I manually configure it, and make it take dhcp instead of roaming, and supply the password and name of connection, now it says (manually configured) but still no internet connection...

so I take out the CD and run Kubuntu 7.04
and guess what? it connects to the internet through the router in a sec without any problems using dhcp !!!!
WHY IS THIS HAPPENING???????????????????????

how can I get ubuntu to connect to the net?
i think its not aquring IP address successfully or something like that... but im not sure.

---

### Post by perito on 2008-03-13
PLEASE HELP ME GET THE INTERNET CONNECTION
im trying to connect to my rounter with WPA ency
I think its not getting the IP address via DHCP
so I did this
sudo lshw -businfo

got this```

*-network 
                description: Ethernet interface 
                product: 88E8039 PCI-E Fast Ethernet Controller 
                vendor: Marvell Technology Group Ltd. 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: eth0 
                version: 14 
                serial: 00:a0:d1:79:09:cb 
                capacity: 100MB/s 
                width: 64 bits 
                clock: 33MHz 
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
        *-pci:1 
             description: PCI bridge 
             product: 82801G (ICH7 Family) PCI Express Port 2 
             vendor: Intel Corporation 
             physical id: 1c.1 
             bus info: pci@0000:00:1c.1 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-network DISABLED 
                description: Wireless interface 
                product: PRO/Wireless 3945ABG Network Connection 
                vendor: Intel Corporation 
                physical id: 0 
                bus info: pci@0000:03:00.0 
                logical name: eth1 
                version: 02 
                serial: 00:1b:77:3b:93:b4 
                width: 32 bits 
                clock: 33MHz 
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated

```
is *-network DISABLED the problem?
how to enable it? coz in the network setting it is Enabled ...

---

### Post by sillyxone on 2008-03-13
it could be the connection manager. I experienced various problems with NetworkManager (cannot connect to unsecured network, cannot reconnect after resume ...) until switching to Wicd.

---

### Post by handydan918 on 2008-03-13
Please post the output of ```
ifconfig
```

And ALWAYS disable encryption if you have a problem getting wireless to work!  
You can re-enable it when you establish a connection.

---

### Post by perito on 2008-03-13
```

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      unassociated  ESSID:"NoConnection"   
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power:16 dBm    
          Retry limit:15   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:608   Missed beacon:0 
 
ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:79:09:CB   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17  
 
eth1      Link encap:Ethernet  HWaddr 00:1B:77:3B:93:B4   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:608 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Base address:0xe000 Memory:f0700000-f0700fff  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 


```

now what?

---

### Post by TeoBigusGeekus on 2008-03-13
[http://ubuntuforums.org/showthread.php?t=705391]("http://ubuntuforums.org/showthread.php?t=705391")

---

### Post by handydan918 on 2008-03-13
If you've already disable encryption at the router, try ```
sudo dhclient
```

---

### Post by Paris Heng on 2008-03-13
Yes, use Wicd, it worked perfect!

---

### Post by perito on 2008-03-13
i installed wicd
and it siad "the networkmanager applet could not find some required resources. it cant continue"

then i run wicd
i see my connection
i connect to it
it connects " Connected to MyConnection at 84 (IP: 192....)

but I still have no internet !!!!!!!!
what should i do now
howcome Im connected ... but no internet ?!

---

### Post by handydan918 on 2008-03-13
Ya know, I keep saying to disable encryption, and I keep hearing about everything else.
Good luck!

---

### Post by perito on 2008-03-13
ok the weirdest thing just happened to me
i removed the WPA
and tried to connect, it did exactly like before
so I typed the command sudo dhclient to show u the results
and then I got internet !
so I was :| and I was typing here and telling u what is going on, and then I did the same command agian... and then no internet
does this command do anything? or is my laptop going crazy?!
I did have internet for like 50 sec and then :(
whats going on ?!?!?!
here are the command
```
ubuntu@ubuntu:~$ sudo dhclient 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth1/00:1b:77:3b:93:b4 
Sending on   LPF/eth1/00:1b:77:3b:93:b4 
Listening on LPF/eth0/00:a0:d1:79:09:cb 
Sending on   LPF/eth0/00:a0:d1:79:09:cb 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPOFFER from 192.168.1.1 
DHCPREQUEST on eth1 to 255.255.255.255 port 67 
DHCPACK from 192.168.1.1 
bound to 192.168.1.5 -- renewal in 1745 seconds. 
ubuntu@ubuntu:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 9908 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth1/00:1b:77:3b:93:b4 
Sending on   LPF/eth1/00:1b:77:3b:93:b4 
Listening on LPF/eth0/00:a0:d1:79:09:cb 
Sending on   LPF/eth0/00:a0:d1:79:09:cb 
Sending on   Socket/fallback 
DHCPREQUEST on eth1 to 255.255.255.255 port 67 
DHCPACK from 192.168.1.1 
bound to 192.168.1.5 -- renewal in 1756 seconds. 
ubuntu@ubuntu:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 9994 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:a0:d1:79:09:cb 
Sending on   LPF/eth0/00:a0:d1:79:09:cb 
Listening on LPF/eth1/00:1b:77:3b:93:b4 
Sending on   LPF/eth1/00:1b:77:3b:93:b4 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPREQUEST on eth1 to 255.255.255.255 port 67 
DHCPACK from 192.168.1.1 
bound to 192.168.1.5 -- renewal in 1563 seconds. 
ubuntu@ubuntu:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 10256 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:a0:d1:79:09:cb 
Sending on   LPF/eth0/00:a0:d1:79:09:cb 
Listening on LPF/eth1/00:1b:77:3b:93:b4 
Sending on   LPF/eth1/00:1b:77:3b:93:b4 
Sending on   Socket/fallback 
DHCPREQUEST on eth1 to 255.255.255.255 port 67 
DHCPACK from 192.168.1.1 
bound to 192.168.1.5 -- renewal in 1397 seconds. 
ubuntu@ubuntu:~$  



```

---

### Post by perito on 2008-03-13
WHAT IS GOING ON?!?!?!?!?!?
this is from ubuntu
im going crazy, does it go online whenever it wants?
how did it go online !?

PS: Not using WICD, I rebooted from a liveCD

---

### Post by perito on 2008-03-13
does dhclient command DO anything or only checks and display results...
is this command making me go online/offline or is it something else?

---

### Post by perito on 2008-03-13
i terribly need help
im so confused

---

### Post by perito on 2008-03-13
well... things are getting more and more confusing .......
I got a connection even when I put my WPA back
BUT
I can only go to [www.google.com](www.google.com)
I can search for whatever i want, it will display the results
but each time i try to go to other websites, it just stops
it stays
Connectiong to [www.ubuntu.com](www.ubuntu.com)....
forever...
does anybody know whats going on?

---

### Post by ugm6hr on 2008-03-14
Lets start again...

Can you connect with a wired network?  If yes, that will make things easier.

Does your router use DHCP or fixed IP?  If it is fixed IP, that may be the problem.

Since you managed to connect briefly, try this again:
```
lshw -C network
```

The OP has started another thread, so this has been closed.

---

