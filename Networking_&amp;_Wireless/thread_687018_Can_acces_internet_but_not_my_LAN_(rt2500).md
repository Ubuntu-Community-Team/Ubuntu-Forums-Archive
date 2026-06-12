---
title: "Can acces internet but not my LAN (rt2500)"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by letex on 2008-02-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello!!
  
  I have and pci rt2500 based wireless card on Gusty. Fist at all, i didn't work, but I could do it to work by using the serialmonkey driver.
 
   Then I find out [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027"), where a new linux-ubuntu-modules is given to install and it works!!
  
    The new modules works exactly as the serialmonkey dirver....but I have a problem.

    Now I can acces Internet (i'm writing through it) but I can't access my LAN. My config files are:

/etc/network/interfaces
[INDENT]# iface wlan0

iface wlan0 inet static
address 192.168.1.89
gateway 192.168.1.2
netmask 255.255.255.0

#pre-up ifconfig wlan0 up
#pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid Casa
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=************
pre-up ifconfig wlan0 up

auto wlan0[/INDENT]

sudo /etc/resolv.conf
[INDENT]nameserver 80.58.61.250
nameserver 80.58.61.254[/INDENT]

  If I try to do "ping" to google (ping [www.google.com](www.google.com)) its works, but if I try to do ping my router (192.168.1.2) has no response.....

  ifconfig wlan0
[INDENT]wlan0     Link encap:Ethernet  HWaddr 00:08:A1:83:4E:02  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe83:4e02/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:2264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2326 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:19 txqueuelen:1000 
          RX bytes:1322840 (1.2 MB)  TX bytes:412431 (402.7 KB)
          Interrupt:17 Base address:0x8000 [/INDENT]

 Can anyone help me??  If you need more information, only ask!!

  thank you in advance and sorry for my poor english...... :)

---

### Post by croto on 2008-02-03
Hi! If it works when you ping google.com (I assume you are getting responses from google, aren't you?), then it means you are already talking to your router. I suppose your router is configured to not answer pings... did you try to ping the router from some other computer in the LAN?

---

### Post by letex on 2008-02-03
Yes, my router responses me doing ping to [www.google.es](www.google.es), but not responses when I "ping" it.
 
   I'm windows on the same computer (for an emergency) and I can do ping with the same IP.......then, the routers can responses my pings form my ip.

   In addition, I have another computer (portable) with Ubuntu 7.10 too, driver serialmonkey (the as the provided with the new modules package) and its work!!!
  
    I can't understanding it!! You can thing that is not important access router, is yet configured, but i can't access to LAN resources through Samba, Firefox (Lan amule webserver) and neither ssh form outside (previous port redirecting)

    It trying now doing ping to router or another computer and this appears:

ping 192.168.1.2
[INDENT]PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.88 icmp_seq=2 Destination Host Unreachable
From 192.168.1.88 icmp_seq=3 Destination Host Unreachable
From 192.168.1.88 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.2 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3[/INDENT]

  WHAT??? My IP is 192.168.1.89, not .88 (see ifconfig??? and:

cat /etc/hosts
[INDENT]
# The following lines are desirable for IPv6 capable hosts
192.168.1.89 ordenata-ubuntu localhost[/INDENT]

 But ping loclahost
[INDENT]
ping localhost
PING ordenata-ubuntu (192.168.1.89) 56(84) bytes of data.
64 bytes from ordenata-ubuntu (192.168.1.89): icmp_seq=1 ttl=64 time=0.021 ms
64 bytes from ordenata-ubuntu (192.168.1.89): icmp_seq=2 ttl=64 time=0.013 ms
64 bytes from ordenata-ubuntu (192.168.1.89): icmp_seq=3 ttl=64 time=0.025 ms
64 bytes from ordenata-ubuntu (192.168.1.89): icmp_seq=4 ttl=64 time=0.021 ms

--- ordenata-ubuntu ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.013/0.020/0.025/0.004 ms[/INDENT]

  I can't understand it. In feisty there were no problems, but after updating Gusty, the problems began....I finally could to up the wireless card with serialmonkeys drviers, but, _in gusty from this computer_, I couldn't access the LAN may.

   Thank you very much!!

---

### Post by croto on 2008-02-04
yep, it looks weird... could you please post the output of "route -n"?

---

### Post by letex on 2008-02-04
It's solved!!

[INDENT]route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    100    0        0 wlan0
0.0.0.0         192.168.1.2     0.0.0.0         UG    100    0        0 eth0[/INDENT]

  When the ping uses 192.168.1.88 I realized that this IP is the Ip of the wired interface. 

[INDENT]iface eth0 inet static
address 192.168.1.88
netmask 255.255.255.0
gateway 192.168.1.2
auto eth0[/INDENT]

 Just doing:

sudo ifdown eth0
  
  It's solved:
[INDENT]ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=254 time=1.60 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=254 time=1.55 ms

--- 192.168.1.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 1.557/1.578/1.600/0.045 ms[/INDENT]

  But I can't understand the reason, because the cable is not connected. I think that my computer was using the ip of the wired interface, but I don't know why....
 
  After "sudo ifup eth0" the ping was successful to router.....Now is actually solved!! 

  Thank you very much

---

### Post by croto on 2008-02-04
Hey I'm glad it worked! Good luck!

---

