---
title: "internet not working in ubuntu 10.04"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by ashish_envy on 2010-05-27
hey i am new to ubuntu.....
and i don't know wat to do wid d setting...
bt i have enter into network connection and then click on to d wired one do the connection manually ....and i have entered ip address , netmask , gateway !

till now no network is coming.... bt at d same time it is working fine on windows...

i have type ifconfig -a
results

root@ashish-desktop:/home/ashish# ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:be:e8  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:19:d1:13:4c:1f  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:14516 (14.5 KB)  TX bytes:14516 (14.5 KB) 



till now helplesss ...........

pls help me .....

---

### Post by peterthewolf on 2010-05-27
Between you and me I think less mobile phone abbreviation might help.

---

### Post by cariboo on 2010-05-27
To check if networking is set up properly, turn of wireless, and type:

```
sudo dhclient eth0
```

the above command should give eth0 an ip address.

To set up a static ip address, you have to press enter after adding an ip address, then enter the netmask and press enter, finally enter the gateway ip address and press enter. When you click apply, the password box should come up.

Once you have done the above networking needs to be restarted, you can either reboot, or open a terminal and type:

```
sudo service networking restart
```

---

