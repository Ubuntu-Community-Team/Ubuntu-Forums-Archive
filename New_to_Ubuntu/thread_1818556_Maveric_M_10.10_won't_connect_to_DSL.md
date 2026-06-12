---
title: "Maveric M 10.10 won't connect to DSL"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by chris_labonte on 2011-08-04
I'm an ABSOLUTE beginner...

1.  Internet worked fine
2.  Lost power in house
3.  Modem 'reset' (I believe)
4  Lost internet on Ubuntu Desktop re-established on PC tablet & iphone
5.  typed 'ifconfig' into command prompt & got int address
6.  typed int adress into 'ping' network tools from system/administration/network tools and got 100% successful transmission.
7.  ran 'system testing' program on internet it detected the 'Realtek Semiconductor...
8.  ran system test on connection but it seems to freeze when generating report.

---

### Post by lmarmisa on 2011-08-04
Hi Chris,

could you post the result of the command **ifconfig**?. This is the result on my computer:

```

luis@UB1010ENG:~$ ifconfig
eth4      Link encap:Ethernet  HWaddr 08:00:27:dc:54:f1  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fedc:54f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26470 (26.4 KB)  TX bytes:14900 (14.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4616 (4.6 KB)  TX bytes:4616 (4.6 KB)

luis@UB1010ENG:~$ 

```

---

### Post by chris_labonte on 2011-08-05
Imarmisa - of course THANKS for taking an interest, 
Formatting is a bit off as I needed to transfer from desktop to XP machine...

clabonte@clabonte-ER903AA-ABA-a1424n:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:15:f2:e5:21:90  
          
inet6 addr: fe80::215:f2ff:fee5:2190/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:308 (308.0 B)  TX bytes:2816 (2.8 KB)
          
Interrupt:21 Base address:0xe400 



lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:0 
          
RX bytes:240 (240.0 B)  
TX bytes:240 (240.0 B)

---

### Post by lmarmisa on 2011-08-05
Try to use the code tags (icon **#**) for a correct view of the commands.

You have no IPv4 address associated to your interface **eth0**. I suppose that your router/modem is configured as the DHCP server for the negotiation of the IP adress on your LAN.

First of all try to check if you have a hardware latchup problem related to the loss of power. Switch off your computer and your modem and remove their power plugs and the LAN cable. Wait a few seconds. Connect the cable and the plugs again and switch on the two devices.

Check if the problem is solved after this test.

Best regards,

Luis

---

### Post by chris_labonte on 2011-08-05
Louis,
Thanks again,

Yes router is DHCP.  I have tried all the power off/on steps to no avail.  Also have plugged the notebook into the same cable same router port and it get's the signal.
  

But (excuse my ignorance) i thought if I got a 'ping' this would show that the 'latchup' was OK...


You have no IPv4 address associated to your interface **eth0**. I suppose that your router/modem is configured as the DHCP server for the negotiation of the IP adress on your LAN.

First of all try to check if you have a hardware latchup problem related to the loss of power. Switch off your computer and your modem and remove their power plugs and the LAN cable. Wait a few seconds. Connect the cable and the plugs again and switch on the two devices.

Check if the problem is solved after this test.

Best regards,

Luis[/QUOTE]

---

### Post by Wim Sturkenboom on 2011-08-05
> **chris_labonte said:**
> 
But (excuse my ignorance) i thought if I got a 'ping' this would show that the 'latchup' was OK...
That depends on what you ping. If you ping localhost (127.0.0.1), the network card is not used.

---

### Post by dineshs on 2011-08-06
Please run```
sudo dhclient eth0
``` and see if there is any progrss.

---

### Post by lmarmisa on 2011-08-06
Chris,

if you have plugged your notebook into the same Ethernet cable and you were able to connect to Internet in this case, I recommend this second simple test.

Boot into an Ubuntu Live CD / USB and check if the DHCP negotiation is made and if you have normal access to the network.

Type the command **ifconfig** in order to check if the DHCP protocol is completed. I have marked in orange the line containing the information related to IP address, mask and broadcast address. Try to post the output of the command while you computer is running Ubuntu Live CD.

Best regards,

Luis

---

### Post by chris_labonte on 2011-08-06
Thanks dineshs

ran dhclient and got...

clabonte@clabonte-ER903AA-ABA-a1424n:~$ sudo dhclient eth0
[sudo] password for clabonte: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/00:15:f2:e5:21:90
Sending on   LPF/eth0/00:15:f2:e5:21:90
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.7 from 192.168.0.1
DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.7 from 192.168.0.1
bound to 192.168.0.7 -- renewal in 35566 seconds.
clabonte@clabonte-ER903AA-ABA-a1424n:~$ 
clabonte@clabonte-ER903AA-ABA-a1424n:~$

---

### Post by dineshs on 2011-08-06
Is it working now?If not what do you get for```
route -n
ping 4.2.2.1 -c3
```

---

### Post by chris_labonte on 2011-08-06
Luis,

Thanks, great suggestion, I have pasted the results below, but - more to the point :) I pulled up firefox and it worked when running from the CD...

So I guess a re-install would solve yes?

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:e5:21:90  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fee5:2190/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39230 (39.2 KB)  TX bytes:12561 (12.5 KB)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ubuntu@ubuntu:~$

---

### Post by chris_labonte on 2011-08-06
um... still following louis' advice and running in boot CD - you-want-i-should go back to my standard desktop

---

### Post by dineshs on 2011-08-06
> um... still following louis' advice and running in boot CD - you-want-i-should go back to my standard desktopYes and post the result of sudo lshw -C network

---

### Post by chris_labonte on 2011-08-06
I ran the 
'route-n ping' in boot CD, said 'invalid option --'c' and invalid --'3'

---

### Post by chris_labonte on 2011-08-06
Just ran it in desktop and got same 'invalid option' response

---

### Post by dineshs on 2011-08-06
> **chris_labonte said:**
> I ran the 
'route-n ping' in boot CD, said 'invalid option --'c' and invalid --'3'The commands are seperate.From your installed system please post the results of
```
sudo lshw -C network 
```
```
route -n
```and
```
ping 4.2.2.1 -c3
```

---

### Post by lmarmisa on 2011-08-06
The problem seems solved. I think that your IP address is **192.168.0.7**.

Try this command:

```

luis@UB1010ENG:~$ ping -c 4 google.com
PING google.com (74.125.39.99) 56(84) bytes of data.
64 bytes from fx-in-f99.1e100.net (74.125.39.99): icmp_req=1 ttl=50 time=83.5 ms
64 bytes from fx-in-f99.1e100.net (74.125.39.99): icmp_req=2 ttl=50 time=124 ms
64 bytes from fx-in-f99.1e100.net (74.125.39.99): icmp_req=3 ttl=50 time=119 ms
64 bytes from fx-in-f99.1e100.net (74.125.39.99): icmp_req=4 ttl=50 time=105 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3009ms
rtt min/avg/max/mdev = 83.522/108.483/124.896/16.047 ms
luis@UB1010ENG:~$

```

---

### Post by dineshs on 2011-08-06
> lmarmisa;11124129]The problem seems solved. I think that your IP address is **192.168.0.7**.
The result was from live CD not from the installed OS

---

### Post by lmarmisa on 2011-08-06
> **dineshs said:**
> The result was from live CD not from the installed OS

@dineshs

The command **dhclient** (post #9) was able to negotiate the IP address. But it seems that the dhcp client was disabled at startup. 

@chris

Please, select System -> Preferences -> Network Connections -> eth0 -> Edit -> IPv4 Settings and check if the metod **Automatic (DHCP)** is defined.

---

### Post by chris_labonte on 2011-08-06
RE- Commands seperate -duh (told you I was a beginner)

Here is what I got, missed the space in the first 'root -n' command...

clabonte@clabonte-ER903AA-ABA-a1424n:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:e5:21:90
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff
clabonte@clabonte-ER903AA-ABA-a1424n:~$ route-n
route-n: command not found
clabonte@clabonte-ER903AA-ABA-a1424n:~$ ping 4.2.2.1 -c3
connect: Network is unreachable
clabonte@clabonte-ER903AA-ABA-a1424n:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
clabonte@clabonte-ER903AA-ABA-a1424n:~$

---

### Post by lmarmisa on 2011-08-06
Chris,

I believe that if you type the command

```

sudo dhclient

```you will get access to the network until a new restart of your system. I would like to check that point.

Simply type these commands and post the results:

```

sudo dhclient
ifconfig
ping -c 3 google.com

```Finally open Firefox and check if you have access to Internet.

Best regards,

Luis

---

### Post by chris_labonte on 2011-08-06
Luis,

Here are the results... (no access via ffox)

clabonte@clabonte-ER903AA-ABA-a1424n:~$ sudo dhclient
[sudo] password for clabonte: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:15:f2:e5:21:90
Sending on   LPF/eth0/00:15:f2:e5:21:90
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.7 from 192.168.0.1
bound to 192.168.0.7 -- renewal in 32468 seconds.
clabonte@clabonte-ER903AA-ABA-a1424n:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:e5:21:90  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fee5:2190/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:458 (458.0 B)  TX bytes:6117 (6.1 KB)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

clabonte@clabonte-ER903AA-ABA-a1424n:~$ ping -c3 google.com
PING google.com (74.125.224.116) 56(84) bytes of data.
64 bytes from 74.125.224.116: icmp_req=1 ttl=56 time=45.7 ms
64 bytes from 74.125.224.116: icmp_req=2 ttl=56 time=46.1 ms
64 bytes from 74.125.224.116: icmp_req=3 ttl=56 time=45.8 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10175ms
rtt min/avg/max/mdev = 45.786/45.936/46.126/0.141 ms
clabonte@clabonte-ER903AA-ABA-a1424n:~$

---

### Post by lmarmisa on 2011-08-06
Hmmm. 

According to the previous commands your DHCP client got the IP adress **192.168.0.7** and your system was able to **ping** google (* --- google.com ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 10175ms rtt min/avg/max/mdev = 45.786/45.936/46.126/0.141 ms*). The **DNS** service was also used for connecting google. So, the conclusion is that you had full access to internet after you typed the command **dhclient**. 

I do not understand why Firefox has no access to Internet. Maybe you used an instance of Firefox that was open before you typed the command.

---

### Post by chris_labonte on 2011-08-06
Nope I re-opened it but it was 'stuck in ' offline mode,  I unchecked this box and am now up and running...Working fine :)

 (but honeslty (really)) I did check this prior to this entire discussion and this did not fix the problem...

In any event it works now,  THANKS,

BTW I would LOVE to know what you think the problem was (light a little candle in my programming darkness :))

---

### Post by lmarmisa on 2011-08-06
> **chris_labonte said:**
> Nope I re-opened it but it was 'stuck in ' offline mode,  I unchecked this box and am now up and running...Working fine :)

 (but honeslty (really)) I did check this prior to this entire discussion and this did not fix the problem...

In any event it works now,  THANKS,

BTW I would LOVE to know what you think the problem was (light a little candle in my programming darkness :))

Chris,

I am not sure that your problem is completely solved.

I would like to know if the DHCP client is really created at startup. 

Please, restart your system, open a terminal and type the command **ifconfig** again. If you see the IP address 192.168.0.7, the problem is solved. Otherwise we will have to update the network setup of your interface eth0.

---

### Post by chris_labonte on 2011-08-06
You are crrect once again,
I restarted and re typed ifconfig and got the 127.0.01 IP not the 192 one

---

### Post by lmarmisa on 2011-08-06
First of all, you know a workaround for getting access to internet. Symply type the command:

```

sudo dhclient

```

But I would like to recover the normal access to internet.

Try this procedure. Select System -> Preferences -> Network Connections -> Wired -> eth0 -> Edit -> IPv4 Settings.

Tick **Connect automatically**, **Require IPv4...** and **Available to all users**. Select method **Automatic (DHCP) addresses only**. Apply (authentication will be required). Do not close the Network Connections window.

Now change the method to **Automatic (DHCP)**. Apply again. I attach a capture.

Finally close the Network Connections setup.

Reboot your system. I would like that the problem will be solved.

---

### Post by chris_labonte on 2011-08-06
perfect! REBOOT & WORKS FINE
THANKS!!!

---

### Post by lmarmisa on 2011-08-06
Great!!!. :)

Please, mark the thread as SOLVED (look at Thread Tools).

Best regards for you and for dineshs. His help was very important!!.

Luis

**COMMENT:** you ask me about my opinion of this problem. Some network config file was corrupted when the power was lost and the dhcp client was not being created at startup.

---

### Post by chris_labonte on 2011-08-06
Will do,
Ubuntu ROCKS

---

