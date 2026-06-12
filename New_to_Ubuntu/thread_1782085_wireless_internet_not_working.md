---
title: "wireless internet not working"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by fozzie54 on 2011-06-14
Hello ...the wireless internet on my netbook stopped working.......specs are as follows
CPU                             [Intel® Atom™ N550 processor ]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_00250087601&cc=GB&contentType=0") (1.5GHz) [Intel® Atom™ N455 processor ]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_00250087601&cc=GB&contentType=0") (1.66GHz)                                                                                                       OS                             Genuine Windows® 7 Starter                                                                                                       Chipset                             Intel® NM10                                                                                                       Memory                             DDR3 667, Max: 2GB                                                                                                       LCD Size                             10” (1024 x 600) WSVGA LED                                                                                                       Graphics                             Intel® GMA 3150                                                                                                       Graphics VRAM                             share with system memory                                                                                                       HDD (GB)                             2.5" 160GB or above SATA                                                                                                       Optical Drive                             N/A                                                                                                       Audio                             HD Audio, Stereo speakers                                                                                                       Webcam                             1.3M                                                                                                       Card Reader                             SD/MMC                                                                                                       LAN                             10/100                                                                                                       Wireless LAN                             802.11 b/g/n                                                                                                       Bluetooth                             BT2.1+EDR                                                                                                       D-Sub (VGA)                             1                                                                                                       HDMI                             N/A                                                                                                       USB 2.0 port                             3
MSI WIND U 160DX.....using Ubuntu 11.04...Natty..
I installed this on Sunday and it worked srtraight away....and now it won't connect...same thing happened with Mint 11...after using Mint 10..it worked all the time on Mint 10.
I have three other computers all working ( not at same time) with wireless...so its not my ISP...
My Linux knowledge is very very basic...I really like Ubuntu ..so I hope I can resolve this issue..
Thanks for any replies and help...
Fozzie

---

### Post by ptm791 on 2011-06-15
If you right-click the internet icon in the upper right, is "enable networking" checked?

---

### Post by nirab on 2011-06-15
could you please go to the terminal and run 

$ ifconfig

and post the output please

---

### Post by fozzie54 on 2011-06-15
Hello ...thank you hat for your reply.....I had given up and was about to install another Distro...not tI want to...
eth0      Link encap:Ethernet  HWaddr 40:61:86:b4:c0:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 6c:62:6d:14:d2:26  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:fe14:d226/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:758372 (758.3 KB)  TX bytes:123788 (123.7 KB)

here is as copied...
Many thanks..

---

### Post by computerandu on 2011-06-15
What is the output of the following command:

sudo rfkill list

---

### Post by nirab on 2011-06-15
I think you should be already connected according to your ifconfig ..... could you ping any sites and check if you are already connected

$ ping google.com

if you cant ping the site the plz run the above command and post the output

$ rfkill list

Maybe there are problems with configurations in your router ????? Have you checked that out ?????

---

### Post by fozzie54 on 2011-06-16
Hello ...and thanks to all....I found the Ubuntu Desktop Guide ...on this site...so I will use my brain and fix it myself.....great guide.....


Cheers 

Fozzie

---

