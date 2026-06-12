---
title: "Wired connection problem for ubuntu 12.04"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by purestr666 on 2013-11-02
So i've been using 10.04 for a long time and yesterday i decide to upgrade to 12.04 but now the internet seems to be disconnected and i've tried everything to make it work. it says that it is 'disconnected' or 'device not ready'. im not used to ubuntu so any solutions may have to be in depth as im not familar with the commands. usually my brother could fix it as he is the one that installed ubuntu onto our desktop but he is at university at the moment and will not be back fro 1 month so i wanted to try and fix this problem withing that time. im currently on a windws 7 laptop so im going to give the ifconfig by just typign it out so sorry if i miss anything out.

eth0   link encap: ethernet   HWaddr  00:18:96:46:53
         inet6 addr:  fe80::218:f3ff:fe96:4653/64 scope:link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:3270 errors:0 dropped:0 overruns:0 frame:0
         TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:337912 (337.9 KB)   TX bytes:13443 (13.4 KB)
         Interrupt:18 Base address: 0xc880

eth1   Link encap: ethernet   HWaddr  00:12:3f:99:f6:22
         UP BROADCAST MULTICAST MTU:1500 metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes: 0 (0.0 B)   TX bytes:0 (0.0 B)

lo      link encap: local loopback
        inet addr: 127.0.0.1  mask: 255.0.0.0
        inet6 addr:   : : 1/128 scope:hos
        UP LOOPBACK RUNNING MTU: 16436  Metric:1
        RX bytes:112018 (112.0 KB)   TX bytes: 112018 (112.0 KB)

---

### Post by grahammechanical on 2013-11-02
Ok and welcome to the forums. Look again at those printouts for eth0 and eth1. They tell me that Ubuntu has recognised your ethernet adapters and has installed driver modules for both of them. But only one of them is connected to the router/hub. Which one is it? I am connected by ethernet and this is what I see when I run ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:1a:92:82:db:59  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe82:db59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2252974 (2.2 MB)  TX bytes:624028 (624.0 KB)
          Interrupt:17 


I also have an eth1 port that is not connected and the printout is similar to your eth1. So, I have not included it. The important bit is UP BROADCAST RUNNING MULTICAST. 

If I run this command

```
nm-tool
```

I see this for eth0

>  Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:1A:92:82:DB:59


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


What do you see when you run the nm-tool command? Whereas for eth1 the State is unavailable and the Wired Properties has Carrier: off.

There is one little thing you can check. Do you switch off the router when you shutdown Ubuntu? I do. So, I have to allow time for the router to initialise and connect to the ISP before I load Ubuntu as I will get a disconnected message. But from what I can see you are connected to the router. So, is the router connected to the ISP?

Regards.

---

### Post by purestr666 on 2013-11-02
hi i thinm it is the eth1 that is connected to the router/hub. i did the command and this is what i got:

State:   disconnected

- Device: eth1-----------------------------------------
  type:      wired
  driver: e100
  state: unvailable
  default: no
  hw address: 00:12:3f:99:f6:22

  capabilities:
      carrier detect : yes

wired properties
carrier: off

-device: eth0------------------------------------------
  type:  wired
   driver: sundance
    state: unvailable
   default: no
   hw address:   00:18:f3:96:46:53
   
capabilities:

wired properties
carrier: off

also im not too sure if the router is connected to the isp

---

