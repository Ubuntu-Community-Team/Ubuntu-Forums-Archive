---
title: "internet not working"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by ettercap on 2009-05-18
Hello every1

Internet(DSL) suddenly stopped working in my 9.04...

Just after installing i used this command "sudo pppoeconf"
to connect.... i updated my system n restarted ...now when i do the same i cannot access the net Mozilla replies with " Address not Found"!

And i also get the "Device not managed" when i click the network icon (right side of the top pane)

what do i do ? can i any 1 help ???

Thanks in advance !

---

### Post by Dark_Stang on 2009-05-18
DSL can be a pain in the butt sometimes because the service providers don't have a set standard (unlike cable which is either DHCP or static). You may have to setup the connection manually. Go System > Administration > Networking. Select your network card and try to setup your connection from there. Good luck.

---

### Post by shadow120 on 2009-05-18
were going to need more info.  run ifconfig in a terminal or iwconfig if its wireless and post the output here

---

### Post by ettercap on 2009-05-19
now it suddenly started working !! :D

net works now...

@dark_stang .. i added it @ system>preferences>network_connections
but the network icon still shows "device not managed" i.e., i cannot select it !

```

abhijith@abhijith-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:74:a4:44  
          inet6 addr: fe80::21a:4dff:fe74:a444/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14942191 (14.9 MB)  TX bytes:624955 (624.9 KB)
          Interrupt:255 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1664 (1.6 KB)  TX bytes:1664 (1.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.195.198.107  P-t-P:117.195.192.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:10458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14710564 (14.7 MB)  TX bytes:466677 (466.6 KB)

```

Can any 1 tell me what is wrong ?
Thank u

---

### Post by Game Over on 2009-05-19
I am having this exact same problem. It's going to take me a second to do the ifconfig and iwconfig because it on another computer. 

Is anyone else missing NetworkManager?

---

### Post by superprash2003 on 2009-05-19
device not managed error - [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

