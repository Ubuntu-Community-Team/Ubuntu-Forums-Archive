---
title: "Ubuntu Studio Strange wifi problem, not the routine &quot;no wifi&quot;"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by studiodude on 2009-07-04
I have been waiting for an oportunity to install ubuntu studio on my studio laptop (dual core Acer Aspire 9420) and finally got round to it last night.  I have searched for a solution here and been through a few threads regarding the "no wifi" thing, but all the commands others without wifi are being asked to report like ifconfig are returning positive results for me, but i still have no wifi connection.  To compound the issue I also have no network manager icon in the top right as I do in regular ubuntu, so its not that easy to see without the command line tools that my wifi is up.  Also, in "network tools" i tried to configure my wlan0 but it says it doesnt exist - i thought this was the cause of my problem initially, but i accidently tried to configure my ethernet connection and it also says that doent exist, which it clearly does as I am on line now and can ping both google and my router. 

ifconfig returns:
```
marc@studio-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:4b:8e:09  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe4b:8e09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3157082 (3.1 MB)  TX bytes:338726 (338.7 KB)
          Interrupt:250 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:72:57:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:de:72:57:0f  
          inet addr:169.254.4.210  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-72-57-0F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and cat /etc/network/interfaces returns

```
marc@studio-laptop:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-key s:"my password appears here correctly"
wireless-essid "my esid correctly appears here"

auto wlan0

auto eth0

```

i do know that 
```
wlan0:avahi Link encap:Ethernet  HWaddr 00:18:de:72:57:0f  
          inet addr:169.254.4.210  Bcast:169.254.255.255  Mask:255.255.0.0
```
is NOT correct but i cant find a way to change it to the same domain as the ethernet because as I said, the configure button in "Network Tools" throws up this "Does Not Exist" error for both ethernet and wlan - not true, I am typing this on line right now via ethernet!!

I have done a few things like adding a line to get the wifi drivers to load on start up to /etc/modules

my other Acer laptop on ubuntu and my wifes dell laptop, also on ubuntu are both sat connected to wifi right now, and before i tried out ubuntu studio, this one was too, also on ubuntu 9.04 like the other two.


I just dont know what to do now, I am at the limit of my knowledge and so any help would be gratefully received.  As always I thank every one in advance for any help or starting point to move me forwards.

---

### Post by studiodude on 2009-08-04
again, after a second thread with no replies or help, i figured it out for myself by installing regular ubuntu first then adding the stuff needed for ubuntu studio from here.   [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") I installed the real time kernal and all packages needed plus removed a lot of un needed stuff.  The regular ubuntu instal got the wifi working and this stayed working thru the RT install etc...

---

