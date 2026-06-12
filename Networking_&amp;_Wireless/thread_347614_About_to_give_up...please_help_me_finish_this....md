---
title: "About to give up...please help me finish this..."
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by jk610 on 2007-01-27
Ive posted twice already in here and no one wants to help me :( . I have a linksys WUSB54G and im working in edgy. 


Ndiswrapper -l

Driver present, hardware present


I did the ndiswrapper -m and modprobe ndiswrapper and rebooted. I then configured my network card as requested and it says activated. Now I dont know where to go from here. I try to open a website and of course doesnt work. Is it a problem that my card comes up on eth1 and not wlan0? Is there anything I can do about this? I really really want to use Ubuntu but I cant stand not having internet! Please help me!!!

---

### Post by JamieC on 2007-01-27
Open a new terminal window (Applications -> Accessories -> Terminal) and post the output of the following:-
```

iwconfig

```

```

ifconfig

```

---

### Post by jk610 on 2007-01-27
jk@OSIRIS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

jk@OSIRIS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:79:D3:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0C:41:D9:83:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2468 (2.4 KiB)  TX bytes:2468 (2.4 KiB)

---

### Post by hggdh on 2007-01-27
Also, please post the output of 'dmesg | grep ndis'.

---

### Post by JamieC on 2007-01-27
You need to specify the SSID of your router:
```

sudo iwconfig wlan0 essid <ssid> mode Managed


```

Then:
```

iwconfig

```

---

### Post by jk610 on 2007-01-27
I did what both of you said...



jk@OSIRIS:~$ dmesg | grep ndis
[17179619.652000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179619.720000] usbcore: registered new driver ndiswrapper
jk@OSIRIS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"LINKSYS"  
          Mode:Managed  Channel=14  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by JamieC on 2007-01-27
> 
[...]
Access Point: Invalid 
[...]


You didn't specify a valid SSID (e.g the SSID of your router).

---

### Post by jk610 on 2007-01-27
oh woops...I got it right this time...


eth1 IEEE 802.11b ESSID:"linksys"
Mode:Managed Channel=14 Access Point: 00:16:B6:1A:C0:94
Sensitivity=0/200
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by hggdh on 2007-01-27
Interesting. ndiswrapper was loaded, and it did not find your hardware...

Do you have the native driver loaded (lsmod  | grep prism54)? If you do, this may explain part of it. You cannot use both ndiswrapper and the native driver at the same time.

---

### Post by jk610 on 2007-01-27
also if i do :


sudo iwlist eth1 scan 



it comes up with connections in my area!!

---

### Post by jk610 on 2007-01-27
> **hggdh said:**
> Interesting. ndiswrapper was loaded, and it did not find your hardware...

Do you have the native driver loaded (lsmod  | grep prism54)? If you do, this may explain part of it. You cannot use both ndiswrapper and the native driver at the same time.


im not sure.. i didnt blacklist anything ..i just ran that command it and didnt do anything..just went to a new line.

---

### Post by hggdh on 2007-01-27
run 'lshw -C Network', and post the output

---

### Post by jk610 on 2007-01-27
jk@OSIRIS:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:79:d3:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 multicast=yes
       resources: iomemory:feaff000-feafffff ioport:df40-df7f irq:201
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0c:41:d9:83:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

---

### Post by JamieC on 2007-01-27
Post the output of the following command:
```

cat /etc/network/interfaces

```

---

### Post by jk610 on 2007-01-27
Oh no! I restarted my computer and now the wireless doesnt show up in network manager, iwconfig, or under ndiswrapper -l. Yikes!!

Damn it I got so close.

---

