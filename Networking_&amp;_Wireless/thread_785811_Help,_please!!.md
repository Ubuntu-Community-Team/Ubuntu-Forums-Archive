---
title: "Help, please!!"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by AmadeusOK on 2008-05-07
Hi All:
I'm relatively new to Ubuntu. I started using it last November and then I upgraded to 8.04. Now, I'm having problems with my wireless internet connection:

It doesn't work at all. One funny thing is that every time I use the Network Setting after entering the ESSID, the Password type, and the Network password (which contains 10 characters), and then clicking OK, and closing it, Internet still doesn't work but if I go back to the Network Setting again, it has 17 dots instead of the 10 I typed in the password box. Anyone could explain why's that?

I had the same problem at the beginning with Ubuntu 7.10. After several trials, I got access to Interner. I honestly don't remember what did I do differently. It was working okay and then for some reasons I had to take it to my office. It had some problems at the beginning but finally it worked. I brought the laptop home two days ago and since then these things are happening again.

Please, I need help. I feel so frustrated without being able to connect to internet for almost 48 hours. Thanks a lot.

---

### Post by superprash2003 on 2008-05-07
i guess you are able to connect to your network but not able to access the internet... please go to the terminal and type ifconfig and post output here

---

### Post by AmadeusOK on 2008-05-08
Hey there,
Thanks for replying my post. This is what I got:

```

eth0      Link encap:Ethernet  HWaddr 00:11:43:5e:71:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:98:1f:e2  
          inet addr:10.198.86.3  Bcast:10.198.87.255  Mask:255.255.248.0
          inet6 addr: fe80::20e:35ff:fe98:1fe2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29491108 (28.1 MB)  TX bytes:7407512 (7.0 MB)
          Interrupt:7 Base address:0xe000 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84800 (82.8 KB)  TX bytes:84800 (82.8 KB)



```

---

### Post by superprash2003 on 2008-05-08
could you also post the output of iwconfig ... sorry, i should have asked this earlier!!

---

### Post by AmadeusOK on 2008-05-09
If I use the iwconfig command I get this:

```

lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

---

### Post by AmadeusOK on 2008-05-19
Apparently, no one can help me with this.

---

