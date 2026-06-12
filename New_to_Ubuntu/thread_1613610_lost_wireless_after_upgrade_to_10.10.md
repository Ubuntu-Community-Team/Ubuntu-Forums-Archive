---
title: "lost wireless after upgrade to 10.10"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-11-04
I have a Dell Inspiron E1505 that worked wirelessly fine until I upgraded to 10.10 now it won't I am copying some of the info below. It says the driver is installed and activated. I need the wireless here at our library as we only have a few ethernet wall jacks. I reinstalled 10.10 again-a clean install from the CD as I have a separate home partition with no luck I need help on this nothing I've tried works.
Dell Inspiron E1505
This driver is activated and currently in use

These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

```
librarian@Dell8:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:206  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

librarian@Dell8:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b7:61:e1  
          inet6 addr: fe80::215:c5ff:feb7:61e1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11182501 (11.1 MB)  TX bytes:1062954 (1.0 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:54:b8:38  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe54:b838/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:567 errors:0 dropped:0 overruns:0 frame:39414
          TX packets:55 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62160 (62.1 KB)  TX bytes:11876 (11.8 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

librarian@Dell8:~

```

---

### Post by bkratz on 2010-11-04
Please copy/paste the output of 

rfkill list

to see if it is hard or soft blocked

---

### Post by Rasa1111 on 2010-11-04
I have the same problem on a compaq presario C500 laptop. 
Ive created a thread, but still no one can help me fix it. 

 Then I downgraded it to 10.04, thinking that would help..
 but still nothing. 

Wireless says active, and connection at 100%, (same driver you're using)
but still cannot access anything on the web, unless connected to ethernet.. :(

---

### Post by cmcanulty on 2010-11-05
I work on the library computers on Thursdays so I will run and post then, thank you very much.

---

### Post by Hippytaff on 2010-11-05
Broadcom is notoriously annoying and due to the nature of the proprietariness of the drivers, not that compatible with linux, though that is set to change...
Ndiswrapper can work by wrapping the windows driver, but it's a pain to set up.
 
[http://lucasmanual.com/mywiki/bcm43xx](http://lucasmanual.com/mywiki/bcm43xx)
 
I haven't read this thoroughly, but it's the kind of thing you can look into

---

