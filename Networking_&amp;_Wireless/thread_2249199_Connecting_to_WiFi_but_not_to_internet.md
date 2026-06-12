---
title: "Connecting to WiFi but not to internet"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by tapasray on 2014-10-20
We have changed our internet provider and WiFi router. After configuration, net connection is available through the Wifi on a laptop running Ubuntu 14.04, a netbook running Windows XP, and a tablet running Android. A second laptop running Ubuntu 14.04 is connecting to the WiFi but not to the net through the WiFi. It IS connecting to the net through ethernet cable, however. 

I came across a similar issue on another thread --
[http://ubuntuforums.org/showthread.php?t=2218513&highlight=Connecting+WiFi+internet](http://ubuntuforums.org/showthread.php?t=2218513&highlight=Connecting+WiFi+internet)

Following the advice posted there, I ran certain commands and got the follollowing outputs. I would really appreciate some help with this. 

Thanks!

-------------------------
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 54:42:49:ff:91:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3137815 (3.1 MB)  TX bytes:3137815 (3.1 MB)

wlan0     Link encap:Ethernet  HWaddr 64:27:37:b1:15:9e  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:feb1:159e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38893937 (38.8 MB)  TX bytes:19572937 (19.5 MB)
------------------------------------------------------------------------------

 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
--------------------------------------------------------------------------------------

ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_seq=1 ttl=47 time=202 ms
64 bytes from 91.189.94.12: icmp_seq=2 ttl=47 time=199 ms
64 bytes from 91.189.94.12: icmp_seq=3 ttl=47 time=203 ms

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 199.248/201.597/203.209/1.776 ms
----------------------------------------------------------------------------------------

ping -c3 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=47 time=314 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=47 time=198 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=47 time=192 ms

--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 192.163/234.997/314.452/56.241 ms

---

### Post by jeremy31 on 2014-10-20
Why don't you run the wireless script from the sticky thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

From what I see you are connected via wifi from the commands you ran
And please use the code tags around terminal output
http://ubuntuforums.org/showthread.php?p=12776168#post12776168

---

### Post by tapasray on 2014-10-20
Many thanks, @jeremy31. Will run and post the output.

---

### Post by Bucky Ball on 2014-10-21
Have you tried comparing the configuration in Network Manager on the 14.04 machine that is connecting with the one that not? See if there are any differences.

Your output appears to show you are indeed online (if you can ping the forums you must be). Do you mean you are not having any success when you attempt to use Firefox or some other web browser?

---

### Post by tapasray on 2014-10-21
Thanks, @Bucky Ball. Actually I haven't compared. Will do when I have both with me. That will be 7/8 hours later. I am in the GMT + 5:30 hrs zone. I have tried both Firefox and Chrome. Neither moves. It looks really strange to me.

---

### Post by Bucky Ball on 2014-10-21
Perhaps check if you are using static IP on one machine and 'auto config DHCP', where your router is serving the IP address on the other. If you're using a static IP you will need to add the DNS IP addresses manually in Network Manager or you won't be able to get online. Your ISP would be able to provide you with the appropriate IPs for their setup, or there are public ones you can use, but I'm not au fait with that.

---

### Post by tapasray on 2014-10-21
@Bucky Ball
I have checked and the settings are identical, except for the IP addresses, which is expected, I think, because it's Automatic (DHCP) and there can't be two devices with the same IP in the same network, I think ... but of course you would know better. It's all really weird!

> **jeremy31 said:**
> Why don't you run the wireless script from the sticky thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

From what I see you are connected via wifi from the commands you ran
And please use the code tags around terminal output
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

@jeremy31, Thanks again and sorry for the extremely late response. I have now managed to run all the commands - update, upgrade, and for identifying the card, and am stuck at this point because of "syntax errors" with various permutations and combinations, two of which I am pasting below --

<sudo apt-get install  <[14e4:4727](rev 01)>>
<bash: syntax error near unexpected token `('>
<pramita@pramita:~$ sudo apt-get install <[14e4:4727] rev 01>>
<bash: syntax error near unexpected token `newline'>

Will really appreciate your help.

---

### Post by Bucky Ball on 2014-10-25
Perhaps try this:

```
sudo apt-get install <[14e4:4727] rev 01>
```

Just a guess ...

---

### Post by tapasray on 2014-10-25
Thanks, @Bucky Ball. Will try and report.

---

### Post by wildmanne39 on 2014-10-25
Hi, go back to that link and run the wireless script and post the output here so we can see what is going on with your wireless.
Thanks

---

