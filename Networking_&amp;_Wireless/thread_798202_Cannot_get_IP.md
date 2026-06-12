---
title: "Cannot get IP"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by logrusmage on 2008-05-18
My wireless can't get an IP from any network. I can see plenty og networks, but when I try to connect, i get the following error.

> beowolf@beowolf-laptop:~$ sudo dhclient wlan0
[sudo] password for beowolf: 
There is already a pid file /var/run/dhclient.pid with pid 10717
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:3a:8e:f4:d2
Sending on   LPF/wlan0/00:1f:3a:8e:f4:d2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Help?

---

### Post by empthollow on 2008-05-18
could you post the output of 
```
ifconfig -a
```

---

### Post by logrusmage on 2008-05-20
> beowolf@beowolf-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:06:24:86  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe06:2486/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1337315 (1.2 MB)  TX bytes:242213 (236.5 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14500 (14.1 KB)  TX bytes:14500 (14.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:8e:f4:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f8200000-f8210000 



There you go.

---

### Post by mapes12 on 2008-05-20
> eth0 Link encap:Ethernet HWaddr 00:1e:ec:06:24:86
inet addr:192.168.1.106 Bcast:192.168.1.255 Mask:255.255.255.0

My guess is that you have an ethernet cable hard wired into your box. If so then take it out.

Wireless may reconfigure when it's out.

---

### Post by chili555 on 2008-05-20
Network Manager is not going to allow a wireless connection if a working wired is available, which it is:> ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:1e:ec:06:24:86
inet addr:192.168.1.106 Bcast:192.168.1.255 Mask:255.255.255.0Detach the wire and try it again, please.

---

### Post by mapes12 on 2008-05-20
?

---

### Post by mapes12 on 2008-05-20
> Detach the wire and try it again, please.


Isn't that what I just suggested????

---

### Post by logrusmage on 2008-05-20
I've disconnected the ethernet cable, and put eth0 down, and got the same result.

I'm using WICD if that matters. It, at least, shows the networks available. Network-Manager didn't even give me that. (I've made sure I've removed N-M).

Could it be something in network settings? I do have my wireless 'checked' and set to my network. As well, it won't give me a securityless option, so I just left the password space blank. Regardless, it wasn't working back when nothing was checked off as well.

---

### Post by chili555 on 2008-05-20
> **mapes12 said:**
> Isn't that what I just suggested????Yep, near as I can tell, we posted at about the same moment. Sorry I missed your and sorry you missed mine.

---

### Post by logrusmage on 2008-05-20
Bump. Seriously, this is aggravating. I've tried everything I can think of. Worst part: a week ago it randomly connected and was working perfectly, but I have no idea how I did it, and which combo of settings did the trick.

---

### Post by logrusmage on 2008-05-21
Bump

---

### Post by mapes12 on 2008-05-21
wicd is a good choice.

After removing the ethernet cable restart your machine and see if wireless configures to a usable state. 

If not please post the out put to:

```
iwconfig
```
```
ifconfig
```
```
cat /etc resolv.conf
```

BTW chili555 is an experienced poster on these issues and may also have a take on how to dig into this. Check back here from time to time for a response.

---

### Post by logrusmage on 2008-05-21
> **mapes12 said:**
> wicd is a good choice.

After removing the ethernet cable restart your machine and see if wireless configures to a usable state. 

If not please post the out put to:

```
iwconfig
```
```
ifconfig
```
```
cat /etc resolv.conf
```

BTW chili555 is an experienced poster on these issues and may also have a take on how to dig into this. Check back here from time to time for a response.

```
beowolf@beowolf-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:06:24:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15904 (15.5 KB)  TX bytes:15904 (15.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:8e:f4:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f8200000-f8210000 

beowolf@beowolf-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

beowolf@beowolf-laptop:~$ cat /etc resolv.conf
cat: /etc: Is a directory
cat: resolv.conf: No such file or directory


```

Obviously, removing the ethernet + restart did nothing :P
Pan0 just appeared under ifconfig... randomly.

What the hell...

---

### Post by chili555 on 2008-05-21
Thanks for the kind comments, mapes12. I appreciate it. The command he was looking for was:```
cat /etc/resolv.conf
```With the wire detached, doesn't Wicd give you the encryption options, WEP, WPA, etc. when you drop down the arrows?

Your *iwconfig* looks healthy, like it's waiting for a request to connect.

What is your encryption method? WEP? WPA?

---

### Post by logrusmage on 2008-05-21
> **chili555 said:**
> Thanks for the kind comments, mapes12. I appreciate it. The command he was looking for was:```
cat /etc/resolv.conf
```With the wire detached, doesn't Wicd give you the encryption options, WEP, WPA, etc. when you drop down the arrows?

Your *iwconfig* looks healthy, like it's waiting for a request to connect.

What is your encryption method? WEP? WPA?

It always gives such options, however I use an open connection (my father is one of those people who refuses to let me mess with the router. I use WEp at my mums, but this computer is currently not there).

```
beowolf@beowolf-laptop:~$ cat /etc/resolv.conf
nameserver 167.206.254.1
nameserver 167.206.254.2

```

Theres the final output. And I just realized my laptop came with *optional* bluetooth -_- so i have to go buy a usb dongle. Lovely.

Anyway thanks for the help thus far. Any other ideas?

---

### Post by chili555 on 2008-05-21
> Any other ideas?A few. Let's try to compress a few things into one post, if we can. First, what does Wicd do when you click connect? Just not connect?

Second, when you uninstalled N-M, did you also remove dhcdbd? Would you please?

Third, when you did you dhclient command, did you precede it with:```
sudo iwconfig wlan0 essid <dads_essid>
```Next, may I please see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by logrusmage on 2008-05-25
> **chili555 said:**
> A few. Let's try to compress a few things into one post, if we can. First, what does Wicd do when you click connect? Just not connect?

Second, when you uninstalled N-M, did you also remove dhcdbd? Would you please?

Third, when you did you dhclient command, did you precede it with:```
sudo iwconfig wlan0 essid <dads_essid>
```Next, may I please see:```
cat /etc/network/interfaces
```Thanks.

It just says "Getting IP from Network" and doesn't move past that. I've left it own for 20min+ and it still stalls at that stage.

I've now uninstalled dhcdbd. 

I did precede it with such. Removing dhcdbd has seemed to do nothing thus far, btw.

```
beowolf@beowolf-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid linksys_SES_39177



auto wlan0

```

---

### Post by logrusmage on 2008-05-27
Bump

---

### Post by mapes12 on 2008-05-28
An open network at least removes WEP etc. from the issue. Can we now have a look at ```
sudo lshw -C network
``` and ```
sudo dhclient
``` please

---

### Post by logrusmage on 2008-06-10
```
beowolf@beowolf-laptop:~$ sudo lshw -C network
[sudo] password for beowolf: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:06:24:86
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.106 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:8e:f4:d2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
beowolf@beowolf-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6546
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:3a:8e:f4:d2
Sending on   LPF/wlan0/00:1f:3a:8e:f4:d2
Listening on LPF/eth0/00:1e:ec:06:24:86
Sending on   LPF/eth0/00:1e:ec:06:24:86
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.106 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 38313 seconds.

```

---

### Post by chili555 on 2008-06-11
> DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 38313 seconds.Congratulations! You are connected! Problem solved?

---

