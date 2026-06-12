---
title: "Cannot connect to wireless access point."
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by Hudson180 on 2014-03-15
Hello, I am trying to set up a dual boot setup with both Ubuntu and Windows 7. I am having an issue establishing a connection with my wireless access point. This is on my desktop computer, and since it does not have a wireless adapter, nor am I no where near the router, I am using an Ethernet cable to bridge the connection between the AP and desktop in order to get a wireless signal.  This does work on my installation on Windows, but not on Ubuntu. Can you please help me resolve this issue. Thank you so much. It does not work on neither the live CD, or the local installation of Ubuntu.

---

### Post by varunendra on 2014-03-16
Welcome to the forums Hudson!

Please explain this more clearly -
> **Hudson180 said:**
> This is on my desktop computer, and **since it does not have a wireless adapter**, nor am I no where near the router, I am using an Ethernet cable to bridge the connection between the AP and desktop in order to get a wireless signal.

If you don't have a wireless adapter, what are you trying to receive the signal? It's like tuning to a radio station without having a radio set.

If you are using a USB wireless adapter, it is also a wireless adapter, just USB.

Please confirm/clarify.

---

### Post by Hudson180 on 2014-03-16
I am connecting an ethernet cable from my computer's NIC to a wireless access point. The access point is picking up the Wi-Fi and is feeding the signal into the cable, going back to my PC and establishing and internet connection.

---

### Post by varunendra on 2014-03-16
If so, the title is a bit misleading. If the access-point (a wireless receiver in this case) is able to receive wifi signal but can't forward it to Ethernet port, it is a configuration problem in itself, nothing to do with Ubuntu. You'll have to refer to its user manual to fix it.

If however, everything is okay at the wireless receiver, only Ubuntu can't 'Use' the forwarded connection over Ethernet, it is an Ethernet problem (hardware/driver or configuration), not wireless.

Please open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
uname -mr
lsb_release -d
sudo lshw -numeric -C network -sanitize
ifconfig -a
nm-tool
cat /etc/network/interfaces
route -n
```
Copy-paste the outputs from the terminal (using your mouse cursor) to your next post here (you can copy them to a text file > move to a computer with internet connection > paste here. Make sure to save the "Line ending" as "Windows" if you are going to open the file on windows, else the lines will be mixed up).

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Hudson180 on 2014-03-16
I just want to say thank you for welcoming me on the forums, and for helping me! I have done your instructions and here is the output:

```

ubuntu@ubuntu:~$ uname -mr
3.11.0-12-generic x86_64
ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 13.10
ubuntu@ubuntu:~$ sudo lshw -numeric -C network -sanitize
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller [11AB:436B]
       vendor: Marvell Technology Group Ltd. [11AB]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff
ubuntu@ubuntu:~$ ifconfig -a
bridge0   Link encap:Ethernet  HWaddr 6e:e1:13:c6:ba:be  
          inet6 addr: fe80::6ce1:13ff:fec6:babe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr 90:fb:a6:4a:43:d0  
          inet addr:169.254.9.66  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::92fb:a6ff:fe4a:43d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61177 (61.1 KB)  TX bytes:61883 (61.8 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24448 (24.4 KB)  TX bytes:24448 (24.4 KB)


ubuntu@ubuntu:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: bridge0 --------------------------------------------------------------
  Driver:            bridge
  State:             disconnected
  Default:           no


  Capabilities:
    Carrier Detect:  yes




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           no
  HW Address:        90:FB:A6:4A:43:D0


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         169.254.9.66
    Prefix:          16 (255.255.0.0)
    Gateway:         0.0.0.0






ubuntu@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth0



```

Note: The bridge connection was just my own attempt at trying to get the connection working. You can disregard it.

---

### Post by varunendra on 2014-03-17
> **Hudson180 said:**
> ```

  IPv4 Settings:
    Address:         169.254.9.66
    Prefix:          16 (255.255.0.0)
   ** Gateway:         [COLOR="#FF0000"]0.0.0.0[/COLOR]**

```

Connection looks good as per nm-tool and lshw, however, Gateway is not defined. Also, the IP looks like the one directly assigned by your ISP?

The gateway is either automatically assigned by DHCP (the router/access-point or ISP), or has to be assigned manually with IP and Subnet (if the IP is static).

How have you got that IP address above (168.254.9.66)? Manually configured in Network Manager or automatically by DHCP?

Please post the IP configuration of your Wireless Access-Point if you are unsure (its own IP address, and the IP of the access-point/router to which it connects).

I have never configured a Wireless Access-Point in this way (and don't have any around to experiment), so **_unless someone with practical experience with this kind of setup sees this and joins us_**, I may need you to provide complete details of its setup configuration as well as how is it connecting to what on the other side (where it is _getting_ the connection from).

A link to the access-point's user manual and the guide (if any) that you followed to configure it this way may also help me.

Fundamentally, a wireless-receiver should get the whole IP configuration (IP, Subnet, Gateway, DNS) from the access-point which it is connecting to, then forward it all as it is to the Ethernet, thus acting like a transparent bridge between the Ethernet device and the access-point.

---

### Post by Hudson180 on 2014-03-17
I did some research, and I came to the conclusion that it is not the wireless receiver that is causing the problem. I believe it is the network drivers. After some googling, I have found that people with the same brand of network cards are having similar trouble with Ubuntu's build in drivers. So I tried to blacklist the driver 'sky2' and install the manufacturer's drivers, however it still seems like the system still sees sky2 as the network driver in use. Is there guranteed way to replace the sky2 driver with my own?

If you still want the manual for the wireless receiver, here it is:  [http://www.downloads.netgear.com/files/GDC/WN604/WN604_UM_14Oct11.pdf](http://www.downloads.netgear.com/files/GDC/WN604/WN604_UM_14Oct11.pdf)

---

### Post by varunendra on 2014-03-18
Please also post the answers to the rest of my questions/details asked.

The driver "sky2" is okay and the problems you saw might be different. For now I'd recommend to revert the blacklist and any other changes you made and just try manual IP assignment if it is static.

I'll take a look at the manual and see if I can suggest anything else. But please post the other details I asked about in my previous post, as much as you can.

---

### Post by Hadaka on 2014-03-18
is this the configuration you are doing??

{internet/wireless signal}  ))))>    <((((((([access point/router]-----cable-------[computer/wifi]

---

