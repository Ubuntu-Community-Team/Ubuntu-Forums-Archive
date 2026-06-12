---
title: "Wifi Connected cannot access internet Ubuntu 16.04"
date: 2017-03-27
forum: Networking &amp; Wireless
---

### Post by vaibhav05 on 2017-03-27
Hi All,

I had installed ubuntu 16.04 & had some driver problems , so had re-installed the drivers & have been using following commands
sudo modprobe -rv rtl8723be

sudo modprobe -rv rtl8723be

it was working fine for few months & was repeatedly runnin this command when the wifi dropped , but today i found another peculair problem,

now the wifi is connecting but i cannot access internet using wifi , i can use the internet from the ethernet port & use wifi from my windows 
partition, but cannot use it in my ubuntu partition :( it is saying server not found or when i ping it is saying unkown host

i ran 

lshw -c net 

```
following is the output

[sudo] password for vaibhav: 
  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: 70:5a:0f:63:5e:04
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=10.246.27.16 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:c5000000-c5000fff memory:c5100000-c5103fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlp13s0
       version: 00
       serial: 44:1c:a8:03:a3:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-66-generic firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:c3000000-c3003f
```ff

any suggestions for the problem is appreciated 

Thanks 

Vaibhav

---

### Post by chili555 on 2017-03-28
Have you looked into antenna selection?  [http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work/635629#635629](http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work/635629#635629)

[http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660](http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660)

---

### Post by karthick87 on 2017-03-28
I guess this might be a DNS issue. Did you confirmed whether nameserver entry's are present in this file '/etc/resolv.conf'?

---

### Post by vaibhav05 on 2017-03-28
> **chili555 said:**
> Have you looked into antenna selection? [http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work/635629#635629](http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work/635629#635629)

[http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660](http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660)

Hey thanks for the reply , i feel the there is some persistent issues with the driver but this non-connectivity is not related to it.

I researched a little & i will like to know your opinion for the same   

have two wifi(WLAN1 & WLAN2) connections in my building which i can use & one ethernet cable of the ISP which is connected to the WLAN1.

I am using ubuntu 16.04 with following network configurations

```

docker0   Link encap:Ethernet  HWaddr 02:42:e2:a2:d4:54  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp7s0    Link encap:Ethernet  HWaddr 70:5a:0f:63:5e:04  
          inet addr:10.246.181.136  Bcast:10.246.255.255  Mask:255.255.0.0
          inet6 addr: fe80::6a33:cf39:44cd:f72e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16189 errors:0 dropped:475 overruns:0 frame:0
          TX packets:10387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17733073 (17.7 MB)  TX bytes:1053700 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1657305 (1.6 MB)  TX bytes:1657305 (1.6 MB)

wlp13s0   Link encap:Ethernet  HWaddr 44:1c:a8:03:a3:2f  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b024:b8b0:9664:964a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1261783 (1.2 MB)  TX bytes:194289 (194.2 KB) 

```

From last two days i am not able to use the internet using the wifi , 
but when i plug the cable provided by my isp from WLAN1 directly into my ethernet 
port , internet is working, but not through wifi.

Hence I researched more & i tried to Ping 8.8.8.8  & Ping google.com following are the results in both the WIFI's i am having
WLAN1
```


ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Net Unreachable
From 192.168.0.1 icmp_seq=2 Destination Net Unreachable
From 192.168.0.1 icmp_seq=3 Destination Net Unreachable
From 192.168.0.1 icmp_seq=4 Destination Net Unreachable
From 192.168.0.1 icmp_seq=5 Destination Net Unreachable
From 192.168.0.1 icmp_seq=6 Destination Net Unreachable
From 192.168.0.1 icmp_seq=7 Destination Net Unreachable
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 0 received, +7 errors, 100% packet loss, time 6010ms


________________________________________________________________________________

When i pinged google.com following was the result 

vaibhav@vaibhav-HP-Notebook:~$ ping google.com
ping: unknown host google.com


```

Similarly i tested the same commands  in the Second Wifi at my home

WLAN2
```


vaibhav@vaibhav-HP-Notebook:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=51.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=47 time=42.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=47 time=45.6 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=47 time=43.4 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=47 time=42.4 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=47 time=43.0 ms
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 6 received, 25% packet loss, time 7009ms
rtt min/avg/max/mdev = 42.495/44.820/51.628/3.220 ms

____________________________________________________________
When i pinged google.com following was the result

vaibhav@vaibhav-HP-Notebook:~$ ping google.com
ping: unknown host google.com


```

> As you can see both the wifi's WLAN1 & WLAN2 is behaving differently 

i.e ping 8.8.8.8 & ping google.com is not working in WLAN1 

    ping 8.8.8.8 is working WLAN2 but ping google.com is not working in WLAN2



But the internet is working fine when i connect the ISP's cable from WLAN1 directly to my ehthnet port 

I am frustrated trying everything i researched in these forums from last two day but nothing is working ,


Following are the some more info on the commands i executed in WLAN1 which is my primary wifi

```

vaibhav@vaibhav-HP-Notebook:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    600    0        0 wlp13s0
link-local      *               255.255.0.0     U     1000   0        0 wlp13s0
172.17.0.0      *               255.255.0.0     U     0      0        0 docker0
192.168.0.0     *               255.255.255.0   U     600    0        0 wlp13s0



```

kindly suggest on how to overcome this problem 



Thanks & Regards

Vaibhav

---

### Post by vaibhav05 on 2017-03-28
> **karthick87 said:**
> I guess this might be a DNS issue. Did you confirmed whether nameserver entry's are present in this file '/etc/resolv.conf'?

Hi Karthick , i feel the same but done know how to troubleshoot it, please look into my previous reply i have outlined few of my observations,

Following is the contents of the  file '/etc/resolv.conf'
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


``` 

I even pinged this name server it is working or its a loop back address

Kindly Suggest

Thanks 

Vaibhav

---

