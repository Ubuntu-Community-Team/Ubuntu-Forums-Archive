---
title: "DSL is showing the connection but internet is not working in mozilla"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by kumar01Aug on 2010-08-01
Dear All,

I have connected my machine to DSL in ubuntu 10.04.  I have configured the detials of DSL as per service provider in DSL tab of network manager. There is network connection as network manager shows the TCP/IP, subnet  mask, router. but i cannot able to surt the net in firefox mozilla or i can not able to ping.

kindly help to establish connection in mozilla under ubuntu 10.04 with DSL connection

---

### Post by k3lt01 on 2010-08-01
Hi Kumar. Follow [the instructions in this post from another thread]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and see how you go.

Let us know what happens.

P.S. Welcome to the Ubuntu family :popcorn:

---

### Post by kumar01Aug on 2010-08-01
Hello k3lt01,

I have done as per the post, but still i am unable to connect to internet. The network manager is showing the connection and all details like IP, DNS, router, subnet mask etc. But i am not able to ping in terminal as well as not able to do surf in mozilla in ubuntu 10.04. The internet connection is working is fine in windows vista, so there is no problem in cable and modem. I think there is a problem in Ubuntu 10.04. Please help me.

---

### Post by thegod_slayer on 2010-08-01
try the command interface.
type** pppoeconf** in the terminal
and then just click ok till u reach the username screen
write your username  and then the password.
and then enjoy.
all these configurations should be done while keeping the modem on.
and connected.
after the connection is configured you nned to switch it on everytime by writing** pon dsl-provider**.
and switch it off by writing** poff.**

---

### Post by dineshs on 2010-08-03
before attempting pppoeconf please post the output of
```
ifconfig -a
```and```
ping -c3 4.2.2.1
```in ubuntu

---

### Post by kumar01Aug on 2010-08-06
> **dineshs said:**
> before attempting pppoeconf please post the output of
```
ifconfig -a
```and```
ping -c3 4.2.2.1
```in ubuntu

Dear DineshS,

I am putting the output as you requested.

The following output is before configuring PPPoE
   [LEFT][LEFT][FONT=&quot]
[/FONT][/LEFT]
[LEFT][FONT=&quot]before connection;;[/FONT][/LEFT]
[LEFT]
[FONT=&quot][/FONT][/LEFT]
[LEFT][FONT=&quot]ifconfig -a[/FONT][/LEFT]
[LEFT][FONT=&quot]
[/FONT][/LEFT]
[LEFT][FONT=&quot] eth0      Link encap:Ethernet  HWaddr 00:13:a9:bf:d2:f3  
          inet6 addr: fe80::213:a9ff:febf:d2f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178519 (178.5 KB)  TX bytes:4187 (4.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14920 (14.9 KB)  TX bytes:14920 (14.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:0f:e5:9b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[/FONT]    [LEFT][LEFT][FONT=&quot]$ ping -c3 4.2.2.1  [/FONT]
[/LEFT][/LEFT]
[FONT=&quot] connect: Network is unreachable
[/FONT][/LEFT]
[LEFT]
[FONT=&quot][/FONT][/LEFT]
[LEFT][FONT=&quot]After configuring the PPPoE and connection established, i got following output: ------[/FONT][/LEFT]
[LEFT]
[/LEFT]
[LEFT]ifconfig -a[/LEFT]
[LEFT]
[FONT=&quot][/FONT][/LEFT]
[LEFT]    [LEFT][LEFT][FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:13:a9:bf:d2:f3  
          inet6 addr: fe80::213:a9ff:febf:d2f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153709 (153.7 KB)  TX bytes:3771 (3.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14920 (14.9 KB)  TX bytes:14920 (14.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.20.42.29  P-t-P:219.90.103.134       Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:700 (700.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:0f:e5:9b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ ping -c3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
[/FONT][/LEFT][/LEFT]
  [/LEFT]
[LEFT]
[FONT=&quot][/FONT][/LEFT]
[LEFT]please find the output of plog after connection:----[/LEFT]
[LEFT]
[/LEFT]
[LEFT]    [LEFT][LEFT][FONT=&quot]pppd[2074]: Connect: ppp0 <--> eth0
pppd[2074]: CHAP authentication succeeded: Welcome to Hayhway.
pppd[2074]: CHAP authentication succeeded
pppd[2074]: peer from calling number 00:24:8C:DA:CD:19 authorized
pppd[2074]: Cannot determine ethernet address for proxy ARP
pppd[2074]: local  IP address 10.20.42.29
pppd[2074]: remote IP address 219.90.103.134
pppd[2074]: primary   DNS address 219.90.103.44
pppd[2074]: secondary DNS address 219.90.103.45
[/FONT][/LEFT][/LEFT]
  
[FONT=&quot][/FONT][/LEFT]
[LEFT][FONT=&quot]This the output after connecting to the service provider, but i am unable to ping the address as well as surf the internet in firefox mozilla. Kindly help to solve this DSL problem in ubuntu 10.04.[/FONT][/LEFT]
[LEFT]
[FONT=&quot][/FONT][/LEFT]
[LEFT][FONT=&quot]I also observed another problem. After configuration of PPPoE, i am unable to access "network connection" from panel from the desktop. I hope the ubuntu lacks the user friendliness for simple internet connection.[/FONT][/LEFT]
[LEFT][FONT=&quot]
[/FONT][/LEFT]
[LEFT][FONT=&quot]regards,[/FONT][/LEFT]
[LEFT][FONT=&quot]kumar  
[/FONT][/LEFT][/LEFT]

---

### Post by cjack007 on 2010-08-06
i think that you should try changing your dns servers.
i use google dns servers (8.8.8.8, 8.8.4.4) and they work much better than my isp servers.
also i think you should change your router connection settings (WAN settings) from bridging mode to pppoe mode so that your router connects automatically without requiring any bridge to Ubuntu so in most cases you will be able to connect even if there is a problem in ubuntu.

please post your results

---

### Post by k3lt01 on 2010-08-06
> **cjack007 said:**
> i think that you should try changing your dns servers.
i use google dns servers (8.8.8.8, 8.8.4.4) and they work much better than my isp servers.He has already tried that and it didn't work.

---

### Post by dineshs on 2010-08-07
Please follow this link(Avoid using pppoeconf in ubuntu versions having Network manager active)
First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
```
gksudo gedit /etc/network/interfaces
```
Edit the file so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
save the file and close
Now continue using the DSL connection
Also pl post the output of the following commands [COLOR="Magenta"]in windows[/COLOR]
```
ipconfig /all
```and ```
route print
```

---

### Post by kumar01Aug on 2010-08-09
Dear Dinesh,

I have made the correction for Network Manager. I configured DSL in network manager. When i connect, it establishes the connection. I can see the IP, netmask, DNS in the Connection Information in Network Manager.

But i cannot surf the net in forefox mozilla. I can not able to ping the the DNS or website.

Kindly suggest the steps to rectify this problem in ubuntu 10.04. 

regards.

---

### Post by kumar01Aug on 2010-08-09
[QUOTE=kumar01Aug;9698037]Dear Dinesh,

I have made the correction for Network Manager. I configured DSL in network manager. When i connect, it establishes the connection. I can see the IP, netmask, DNS in the Connection Information in Network Manager.

But i cannot surf the net in forefox mozilla. Kindly suggest how to configure ubuntu or firefox so i can surf net.

regards,

---

### Post by dineshs on 2010-08-11
Open firefox
edit-preferences-advanced-network-settings
Can you tick use system proxy settings and see

---

### Post by theboxseat on 2010-08-11
I had the same problem...

How about trying something really simple first...

Your NIC and router may be operating at different settings

Try this

#sudo ethtool -s eth0 speed 10 duplex full autoneg off

Right click network connection 
Uncheck 'Enable Networking"
Recheck 'Enable Networking"

Try browsing to speedtest.net

If above does not work, then try again, but change duplex to half.

---

