---
title: "Encore, Mrv800c, can not connect problem"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by sagaz on 2007-03-22
Hello everybody, first of all thank you in advance for your help and support....I am a linux /ubuntu newby so I need some help for going wireless.....

I have and encore ENPWI-G wireless pcmcia card and so far I have installed it...I guess! 
ndiswrapper -l shows HW presen driver present...

I can see all available networks by typing iwlist wlan0 scan, but can not connect to any network although I have configured my essid and wep key with the administration network utility ...

Everything seems to be ok but I have been unsuccesful in connecting to any network with my wless card....I am using dapper on a toshiba laptop....

Could somebody help me, please, with this? ....What is missing? What am I doing wrong?

Doing some research i have found the following error main error loading /lib/firmware/mrv8k-b.fw for device /class/firmware/0000:07:00.0 with driver mrv8k

Could you please help me to understand and work around it?


Here is an iwconfig output...

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now this is the ifconfig output

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:70:7F:ED
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe70:7fed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1201887 (1.1 MiB)  TX bytes:139172 (135.9 KiB)
          Interrupt:5 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:03:2F:33:5A:C9
          inet6 addr: fe80::203:2fff:fe33:5ac9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:26010000-26020000


I feel I am close but can not get there...Please any help will be appreciated....


People please, any suggestions?

---

### Post by macabro22 on 2007-04-25
I have EXACTLY the same problem. It used to work on Edgy Eft, now it doesn't.  Whatheheck?

---

### Post by macabro22 on 2007-05-19
I got it working!

Check it out here: [http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

---

