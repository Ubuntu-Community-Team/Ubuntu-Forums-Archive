---
title: "Trouble connecting to the internet"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by rahul_cse25 on 2010-06-28
I am very new to ubuntu, i installed ubuntu dual booting with windows vista. I use a wired internet connection to connect to the 
internet.I am not able to connect to the internet using ubuntu.
I have followed all the steps using the network manager,manually
editing the connection details,and at the end the network manager
shows that i am connected,but mozilla does not open my ISP home page,nor any other page. Windows vista works fine .I really want to make the transition to ubuntu but i have this problem,kindly help!

---

### Post by gdonwallace on 2010-06-28
There are a couple things you can do.

1.  Check the settings in Firefox.  If you are running through a router, you may want to check the option for No Proxy, or use system proxy settings.

2.  Check to make sure there are no issues with your wireless on the machine you are using.  Start a terminal (Applications --> Accessories --> Terminal) At the prompt type **ping <web address>** (I would suggest a web address outside like [www.microsoft.com](www.microsoft.com)) it will send out test packets to the address, if it works, it will report back no dropped packets, if not it will report back dropped packets.  If you get drops, then there may still be something with the wireless connection.  

If you are using security, make sure you have the correct pass phrase and security type selected.  Thats a start, hope it helps.

---

### Post by rahul_cse25 on 2010-06-29
I am not using a wireless connectio,i am using a wired connection,something like
cable modem. 
As i said that the same connection is working flawless with windows vista in my same 
laptop,thats why i dont think that there might be somehing wrong with my connection or my laptop.
But i will work on the steps suggested by you,and will get back to you.
thanks anyway!

---

### Post by Rubi1200 on 2010-06-29
Posting the output of 

```
ifconfig
```

might also help us figure things out.

---

### Post by dineshs on 2010-06-29
pl post the output of```
ifconfig -a
```
and
```
ping -c3 4.2.2.1
```

---

### Post by DrMelon on 2010-06-29
Note: you have to open a Terminal to type those in and get the output.
You'll find it in Applications -> Accessories (i think).

---

### Post by rahul_cse25 on 2010-06-30
I tried out the steps suggested . when i am typing ping -c3 4.2.2.1 ,it is giving the output as: connect: network is unreachable.
 
on typing ifconfig -a
lot of information is displayed which i am not able to writye all of them down here
the last line shows: interrupt=17
 
I am really puzzled,where does the problem lie?
kindly help me.

---

### Post by bance on 2010-06-30
try to copy and paste the output to show all info ):P

---

### Post by dineshs on 2010-06-30
> . I use a wired internet connection to connect to the
internet
You mean ethernet cable? And to what device the other end is connected to?modem?
please post the output of
```
route -n
```
or at least  the gateway IP address from the command output

---

### Post by rahul_cse25 on 2010-06-30
No it is not an ethernet cable,it is a cable provided to me by my isp,the other end does not have a modem,it is directly connected to my isp router i guess.

Also i am not able to post the output,as sometimes the output is very long and i connect to the internet through windows vista,not through ubuntu.

---

### Post by rahul_cse25 on 2010-06-30
I am trying to paste the output of the commands which i have tried in ubuntu as suggested by you.
please help me rectify the issue.
 
 
 
[FONT=Courier New][SIZE=3][SIZE=2]subhayan@subhayan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:f2:75:79  
          inet addr:172.60.12.207  Bcast:172.60.255.255  Mask:255.255.0.0
          inet6 addr: fec0::9:223:8bff:fef2:7579/64 Scope:Site
          inet6 addr: 2002:ac3c:4b9:9:223:8bff:fef2:7579/64 Scope:Global
          inet6 addr: fe80::223:8bff:fef2:7579/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29461 (29.4 KB)  TX bytes:7423 (7.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr be:81:76:10:00:7c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:3d:d0:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



subhayan@subhayan-laptop:~$ pwd
/home/subhayan
subhayan@subhayan-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.60.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

[/SIZE]
 [/SIZE][/FONT]

---

### Post by rahul_cse25 on 2010-07-01
i have already posted the output of the commands as asked by you all,
kindly suggest me a way out of the problem. what might be wrong,at the same time can any body tell me hoe to alter the settings of mozilla firefox browser,i mean which tab to go,and what to do.

---

### Post by dineshs on 2010-07-01
can you post the output of the following commands on [COLOR="Blue"]windows[/COLOR]
*ipconfig /all*
and
*route print*

---

### Post by rahul_cse25 on 2010-07-03
the outputs as asked for are as follows:

C:\Users\user>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : user-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : mshome
                                       net

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) WiFi Link 5100 AGN
   Physical Address. . . . . . . . . : 00-1E-65-3D-D0-0A
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : mshome
   Description . . . . . . . . . . . : Broadcom NetLink (TM) Gigabit Ethernet
   Physical Address. . . . . . . . . : 00-23-8B-F2-75-79
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:ac3c:4b9:9:a892:337f:f512:4f92(Prefe
rred)
   Site-local IPv6 Address . . . . . : fec0::9:a892:337f:f512:4f92%1(Preferred)

   Temporary IPv6 Address. . . . . . : 2002:ac3c:4b9:9:cd3e:47f0:8c88:f96(Prefer
red)
   Link-local IPv6 Address . . . . . : fe80::a892:337f:f512:4f92%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 172.60.12.207(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::40f6:4888:44fc:a34b%12
                                       172.60.12.1
   DHCPv6 IAID . . . . . . . . . . . : 268444555
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-29-06-F9-00-23-8B-F2-75-79

   DNS Servers . . . . . . . . . . . : 202.179.76.245
                                       202.71.136.67
   NetBIOS over Tcpip. . . . . . . . : Enabled
   Connection-specific DNS Suffix Search List :
                                       mshome
                                       net

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 00-25-56-F3-14-CB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . : mshome
   Description . . . . . . . . . . . : isatap.{5B1B404C-17FE-4BE5-A965-D46D351B2
7C4}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::200:5efe:172.60.12.207%14(Preferred
)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 202.179.76.245
                                       202.71.136.67
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{12C805C7-AF57-4CFF-BD5D-A7673F477
C6E}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 13:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{5010D04C-2493-4919-B1D5-AEDD069F9
499}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

and the output of route print is :

C:\Users\user>route print
===========================================================================
Interface List
 13 ...00 1e 65 3d d0 0a ...... Intel(R) WiFi Link 5100 AGN
 12 ...00 23 8b f2 75 79 ...... Broadcom NetLink (TM) Gigabit Ethernet
 11 ...00 25 56 f3 14 cb ...... Bluetooth Device (Personal Area Network)
  1 ........................... Software Loopback Interface 1
 14 ...00 00 00 00 00 00 00 e0  isatap.{5B1B404C-17FE-4BE5-A965-D46D351B27C4}
 16 ...00 00 00 00 00 00 00 e0  isatap.{12C805C7-AF57-4CFF-BD5D-A7673F477C6E}
 15 ...00 00 00 00 00 00 00 e0  isatap.{5010D04C-2493-4919-B1D5-AEDD069F9499}
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      172.60.12.1    172.60.12.207    276
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      172.60.12.0    255.255.255.0         On-link     172.60.12.207    276
    172.60.12.207  255.255.255.255         On-link     172.60.12.207    276
    172.60.12.255  255.255.255.255         On-link     172.60.12.207    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link     172.60.12.207    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link     172.60.12.207    276
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0      172.60.12.1  Default
===========================================================================

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 12    276 ::/0                     fe80::40f6:4888:44fc:a34b
  1    306 ::1/128                  On-link
 12   4116 2002::/16                fe80::40f6:4888:44fc:a34b
 12     28 2002:ac3c:4b9:9::/64     On-link
 12    276 2002:ac3c:4b9:9:a892:337f:f512:4f92/128
                                    On-link
 12    276 2002:ac3c:4b9:9:cd3e:47f0:8c88:f96/128
                                    On-link
 12    276 fe80::/64                On-link
 14    281 fe80::200:5efe:172.60.12.207/128
                                    On-link
 12    276 fe80::a892:337f:f512:4f92/128
                                    On-link
 12     28 fec0:0:0:9::/64          On-link
 12    276 fec0::9:a892:337f:f512:4f92/128
                                    On-link
  1    306 ff00::/8                 On-link
 12    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None


these are the outputs which you wanted,kindly tell me what should i do to get rid of my problem and connect to the internet?

---

### Post by dineshs on 2010-07-04
Pl try to configure NM as follows
Right-click on the NM icon(two opposite arrows on top right if you are using 10.04) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection  and click edit
select ipv4 
method-manual 
click add 
address 172.60.12.207
mask 255.255.255.0
gateway 172.60.12.1 
[COLOR="Blue"]then hit enter [/COLOR]
DNS 4.2.2.1
then click [COLOR="Blue"]apply [/COLOR]
Now restrat your machine and try if pages are loading.If not post the output of
```
ping -c3 4.2.2.1
```
```
route -n
```
```
ping -c3 172.60.12.1
```

---

### Post by waseemf on 2010-07-06
> **dineshs said:**
> Pl try to configure NM as follows
Right-click on the NM icon(two opposite arrows on top right if you are using 10.04) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection  and click edit
select ipv4 
method-manual 
click add 
address 172.60.12.207
mask 255.255.255.0
gateway 172.60.12.1 
[COLOR="Blue"]then hit enter [/COLOR]
DNS 4.2.2.1
then click [COLOR="Blue"]apply [/COLOR]
Now restrat your machine and try if pages are loading.If not post the output of
```
ping -c3 4.2.2.1
```
```
route -n
```
```
ping -c3 172.60.12.1
```



Hi Dinesh, 

I am also having a similiat problem connecting to ethernet on 10.04. I have only Ubuntu on my system(No Windows).

The output of 'ifconfig -a' gives

Link encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RS packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)
=======================================


And here is the output of 'ipconfig' on Windows running on a different machine.

===================================
Windows IP Configuration


Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.2.128
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
===================================

Please help with this!

---

### Post by dineshs on 2010-07-06
waseemf,
please start a new thread with the output of
```
sudo lshw -C network
```
From the data you have given(ifconfig -a),I understand that your ethernet card is not detected.I am not an expert to tell why.Do you have an ethernet card ?Is it enabled in BIOS?

---

