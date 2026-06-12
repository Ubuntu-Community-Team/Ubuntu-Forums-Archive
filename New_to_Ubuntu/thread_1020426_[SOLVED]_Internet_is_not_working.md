---
title: "[SOLVED] Internet is not working"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by halovivek on 2008-12-24
hi
my internet connection is not working. i always give the manual ip address to work . after installation i have given the ip address and it worked fine. it downloaded all files and it was working fine. after the updated now i could not connect to internet. i tried to connect wireless also. it is not working. i dont know what to do. i have checked the same with vista it is working fine. i dont know how to solve this. :(

---

### Post by superprash2003 on 2008-12-24
have you tried giving the manual ip again?? go to the terminal and type ifconfig and post output..


merry christmas..

---

### Post by halovivek on 2008-12-24
i will do it and get back to you

---

### Post by halovivek on 2008-12-24
> **superprash2003 said:**
> have you tried giving the manual ip again?? go to the terminal and type ifconfig and post output..


merry christmas..

***When I select the wired config in network tools I will get this.***
halovivek@halovivek-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7
          inet addr:82.182.221.135  Bcast:82.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:201050 (201.0 KB)  TX bytes:1384 (1.3 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26368 (26.3 KB)  TX bytes:26368 (26.3 KB)

**_when I select the auto I get this._**
halovivek@halovivek-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7
          inet6 addr: fe80::21e:ecff:fe4b:e0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:235204 (235.2 KB)  TX bytes:3606 (3.6 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26368 (26.3 KB)  TX bytes:26368 (26.3 KB)

---

### Post by northern lights on 2008-12-24
How do you connect to the internet?
Is there a router in between your machine and the ISP's house access?

Can you post the output of```
sudo lshw -C network
```also, in order to check whether your hardware is configured correctly in the first place, please?

Thank you.

---

### Post by akelsall on 2008-12-24
Please post the output of the following files:

/etc/resolv.conf  (displays your DNS IPs)

/etc/network/interfaces (shows DHCP or manually configured IPs)

---

### Post by halovivek on 2008-12-24
> **northern lights said:**
> How do you connect to the internet?
Is there a router in between your machine and the ISP's house access?

Can you post the output of```
sudo lshw -C network
```also, in order to check whether your hardware is configured correctly in the first place, please?

Thank you.

sudo lshw -C network
[sudo] password for halovivek:                    
  *-network                                       
       description: Wireless interface            
       product: BCM4312 802.11b/g                 
       vendor: Broadcom Corporation               
       physical id: 0                             
       bus info: pci@0000:05:00.0                 
       logical name: eth1
       version: 01
       serial: 00:1f:e2:ae:88:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.110 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:4b:e0:f7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=82.182.221.135 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:27:1f:2a:3c:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
halovivek@halovivek-laptop:~$

---

### Post by uarale on 2008-12-24
it seems that there's something wrong with NetworkManager on Ubuntu. i encountered some problems before, but the network's just fine after i installed wicd to replace the build-in NetworkManager.
maybe you should give it a try: [http://www.wicd.net/download.php](http://www.wicd.net/download.php)

---

### Post by Gulyan on 2008-12-24
First try to check the physical connection. Type this in a terminal:
```
ethtool eth0
```
If it shows "Link detected: yes" then the physical connection is fine.
The nest step is to verify the existence of a gateway. You can do this by typing:
```
route
```
If no gateway is present you must add one:
```
sudo route add default gateway <IP>
```
Another problem may be the DNS. Type this 2 commands:
```
ping -c 4 www.google.com
ping -c 4 74.125.43.104
```
If the first one fails but the second one works, you must add a DNS server to the /etc/resolv.conf file
The final step si to try:
```
traceroute www.google.com
```
And to see where the connection breaks.

I hope this helps you. :)

---

### Post by akelsall on 2008-12-24
Actually, if you find that DNS is your problem, enter the following command to modify the file that makes your DNS entries permanent:

**[COLOR="Blue"] sudo vi /etc/dhcp3/dhclient.con[/COLOR]**f 

Add the following two lines to the end of the file (make sure you inclue the semicolon at the end. OpenDNS is a company millions of people use for DNS service. Visit [www.opendns.com](www.opendns.com) for more info):

prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;

Once you've made you're changes, you may need to restart networking by using the following command:

 [COLOR="Blue"]**    sudo /etc/init.d/networking restart**[/COLOR]

Andy

---

### Post by halovivek on 2008-12-25
> **Gulyan said:**
> First try to check the physical connection. Type this in a terminal:
```
ethtool eth0
```
If it shows "Link detected: yes" then the physical connection is fine.
The nest step is to verify the existence of a gateway. You can do this by typing:
```
route
```
If no gateway is present you must add one:
```
sudo route add default gateway <IP>
```
Another problem may be the DNS. Type this 2 commands:
```
ping -c 4 www.google.com
ping -c 4 74.125.43.104
```
If the first one fails but the second one works, you must add a DNS server to the /etc/resolv.conf file
The final step si to try:
```
traceroute www.google.com
```
And to see where the connection breaks.

I hope this helps you. :)

halovivek@halovivek-laptop:~$ ethtool eth0
The program 'ethtool' is currently not installed.  You can install it by typing:
sudo apt-get install ethtool
bash: ethtool: command not found
halovivek@halovivek-laptop:~$ ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
halovivek@halovivek-laptop:~$ ping -c 4 74.125.43.104
PING 74.125.43.104 (74.125.43.104) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 74.125.43.104 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3013ms

halovivek@halovivek-laptop:~$ traceroute [www.google.com](www.google.com)
[www.google.com:](www.google.com:) Name or service not known
Cannot handle "host" cmdline arg `[www.google.com](www.google.com)' on position 1 (argc 1)
halovivek@halovivek-laptop:~$
:(

---

### Post by halovivek on 2008-12-25
> **akelsall said:**
> Actually, if you find that DNS is your problem, enter the following command to modify the file that makes your DNS entries permanent:

**[COLOR="Blue"] sudo vi /etc/dhcp3/dhclient.con[/COLOR]**f 

Add the following two lines to the end of the file (make sure you inclue the semicolon at the end. OpenDNS is a company millions of people use for DNS service. Visit [www.opendns.com](www.opendns.com) for more info):

prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;

Once you've made you're changes, you may need to restart networking by using the following command:

 [COLOR="Blue"]**    sudo /etc/init.d/networking restart**[/COLOR]

Andy

halovivek@halovivek-laptop:~$ sudo lshw -C network                              
  *-network                                                                     
       description: Wireless interface                                          
       product: BCM4312 802.11b/g                                               
       vendor: Broadcom Corporation                                             
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:ae:88:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.179 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:4b:e0:f7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:48:a7:b3:9b:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
halovivek@halovivek-laptop:~$


halovivek@halovivek-laptop:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
halovivek@halovivek-laptop:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
halovivek@halovivek-laptop:~$

halovivek@halovivek-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:1f:e2:ae:88:cc
          inet addr:192.168.0.179  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:feae:88cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:105
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3955 (3.9 KB)  TX bytes:1216 (1.2 KB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26368 (26.3 KB)  TX bytes:26368 (26.3 KB)

---

### Post by dineshs on 2008-12-25
If you have installed firestarter please stop it and try

---

### Post by northern lights on 2008-12-25
> **halovivek said:**
> halovivek@halovivek-laptop:~$ sudo lshw -C network                              
  *-network                                                                     
       description: Wireless interface                                          
       product: BCM4312 802.11b/g                                               
       vendor: Broadcom Corporation                                             
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:ae:88:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.179 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:4b:e0:f7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:48:a7:b3:9b:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
Your network hardware appears to be set up correctly from the driver side of things. Hence this must be a software issue.

> **halovivek said:**
> halovivek@halovivek-laptop:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
halovivek@halovivek-laptop:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
/etc/resolv.conf and /etc/network/interfaces are files you can view, not run. Therefore please post the output of ```
cat /etc/resolv.conf
```
and```
cat /etc/network/interfaces
```
You could alternatively open them in a GUI based editor and copy/paste.

> **halovivek said:**
> halovivek@halovivek-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:1f:e2:ae:88:cc
          inet addr:192.168.0.179  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:feae:88cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:105
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3955 (3.9 KB)  TX bytes:1216 (1.2 KB)
          Interrupt:18
eth0 denotes your ethernet interface and eth1 the wireless one. The wireless is currently assigned an IP, the ethernet is not.
Do you connect to the net directly via a cable modem or the like, or do you have a router with DHCP in between?
If the second is the case, set your interfaces to be assigned IPs automatically. If you connect with a static IP, assign one to your ethernet connection.
What settings do you use on other machines / Windows machines to connect?
If all that sounds like gibberish, what is your ISP?

---

### Post by halovivek on 2008-12-25
cat /etc/resolv.conf
cat /etc/network/interfaces

***halovivek@halovivek-laptop:~$ cat /etc/resolv.conf***
# Generated by NetworkManager
domain .
search .
nameserver 208.67.220.220
nameserver 208.67.222.222
nameserver 89.160.20.18
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 192.168.0.1
***halovivek@halovivek-laptop:~$ cat /etc/network/interfaces***
auto lo
iface lo inet loopback
.
now i am friend room, he is using wifi router. i can connect it also but i could not work in internet. it is working fine in windows.

---

### Post by Krisando on 2008-12-25
Same problem.

---

### Post by desy83 on 2008-12-25
> **Krisando said:**
> Same problem.

I had the same problem but it wasn't my router it was my external wireless adpater.Even though the router and the wireless connections were both Belkin. The Belkin wireless G USB Adapter did not work so I changed it to wireless lan cardbus card for my laptop and I had no further problems.

---

### Post by northern lights on 2008-12-26
> **northern lights said:**
> Do you connect to the net directly via a cable modem or the like, or do you have a router with DHCP in between?
If the second is the case, set your interfaces to be assigned IPs automatically. If you connect with a static IP, assign one to your ethernet connection.
What settings do you use on other machines / Windows machines to connect?
If all that sounds like gibberish, what is your ISP?
Could you please provide the requested answers?
It is much harder to diagnose your problem without adequate information.

The *ifconfig* output in your last post suggests that your friends wireless router did assign an IP to your wireless interface via DHCP.

Could you maybe also provide ```
route -n
```

It would further be helpful if you were always working from the same environment when posting information.

---

### Post by halovivek on 2008-12-26
[COLOR="Red"]Do you connect to the net directly via a cable modem or the like, or do you have a router with DHCP in between?[/COLOR]
i will connect to the router for which ip address is permenent for me.
[COLOR="Red"]If the second is the case, set your interfaces to be assigned IPs automatically. If you connect with a static IP, assign one to your ethernet connection.[/COLOR]
i tried to get auto ip but it is not working.
[COLOR="Red"]What settings do you use on other machines / Windows machines to connect?[/COLOR]
i will just go to the lan settings and i will give manual ip
[COLOR="Red"]If all that sounds like gibberish, what is your ISP?[/COLOR]
i dont know, my house owner given the ip address and he told we had the agreement with the company. so this is permenent ip address to the router.


[COLOR="Red"]Could you maybe also provide 
Code:
route -n
It would further be helpful if you were always working from the same environment when posting information.
[/COLOR]
i am in friend home. this is output.
halovivek@halovivek-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
halovivek@halovivek-laptop:~$

---

### Post by northern lights on 2008-12-26
> **halovivek said:**
> [COLOR="Red"]i will connect to the router for which ip address is permenent for me.
i will just go to the lan settings and i will give manual ip
Okay. If I understand you correctly, you do not connect directly to the ISP, but via a router that is used by several parties in the house. However it does have DHCP enabled and you can connect via one specific IP only.

> **halovivek said:**
> i am in friend home. this is output.
halovivek@halovivek-laptop:~$ route -n
Kernel IP routing table
Destination.....Gateway.........Genmask.........Flags.Metric.Ref    Use Iface
192.168.0.0.....0.0.0.0.........255.255.255.0.U.....2......0........0.[COLOR="DarkRed"]eth1[/COLOR]
169.254.0.0.....0.0.0.0.........255.255.0.0.....U ....1000...0........0.[COLOR="DarkRed"]eth1[/COLOR]
0.0.0.0............[COLOR="SeaGreen"]192.168.0.1[/COLOR]...0.0.0.0..........UG....0......0.......0.[COLOR="DarkRed"]eth1[/COLOR]

The green IP is the current routers IP. The dark red marked eth1 is telling us that you're currently connected via the wireless. So for now, let's try to get you web access in this friend's wireless environment.

Check the networking icon in the upper panel to see whether you've been automatically connected - you should be, as *route -n* shows what is most likely your friend's wireless router. Ask him, whether the router's IP is 192.168.0.1.
If you're not connected, open "System > Preferences > Network Configuration" (you've mentioned "Network Tools" earlier - you don't need those right now), switch to the wireless tab and click on "Add". "SSID" is the name of the wireless network. "Infrastructure" is fine. Under the "Wireless Security" tab, pick the correct encryption and enter the passphrase. Under "IPv4 Settings" the defaults should be fine, i.e. "Automatic (DHCP)" for "Method".

When you open a browser and connecting to a website fails, what exact error message do you get?
I know you've been asked this before, but when connected to your friend's wireless (whether automatically, or manually) can you ping google.com again?```
ping google.com
```If this doesn't work, but pinging 74.125.45.100 does, the problem somehow lies in resolving URLs.

Let's narrow this down.

---

### Post by linux_tech on 2008-12-26
I don't see any gateway listed, without a gateway you can't get on internet
what is output of:
```
netstat -nr
```
If there is no ip addr for the gateway then you will need to add one.

Based on your current ip addr, you can type something like this-
```
sudo ip route add default via 192.168.0.254  
sudo route add default gw 192.168.0.254
```


Next open /etc/network/interfaces file

```
 sudo vi /etc/network/interfaces
```
Find eth0 or desired network interface and add following-
```
gateway 192.168.0.254
```

more details here-http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html

HOWTO - Basic Network Troubleshooting 
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by halovivek on 2008-12-26
> **northern lights said:**
> Okay. If I understand you correctly, you do not connect directly to the ISP, but via a router that is used by several parties in the house. However it does have DHCP enabled and you can connect via one specific IP only.


The green IP is the current routers IP. The dark red marked eth1 is telling us that you're currently connected via the wireless. So for now, let's try to get you web access in this friend's wireless environment.

Check the networking icon in the upper panel to see whether you've been automatically connected - you should be, as *route -n* shows what is most likely your friend's wireless router. Ask him, whether the router's IP is 192.168.0.1.
If you're not connected, open "System > Preferences > Network Configuration" (you've mentioned "Network Tools" earlier - you don't need those right now), switch to the wireless tab and click on "Add". "SSID" is the name of the wireless network. "Infrastructure" is fine. Under the "Wireless Security" tab, pick the correct encryption and enter the passphrase. Under "IPv4 Settings" the defaults should be fine, i.e. "Automatic (DHCP)" for "Method".

When you open a browser and connecting to a website fails, what exact error message do you get?
I know you've been asked this before, but when connected to your friend's wireless (whether automatically, or manually) can you ping google.com again?```
ping google.com
```If this doesn't work, but pinging 74.125.45.100 does, the problem somehow lies in resolving URLs.

Let's narrow this down.
[COLOR="Blue"][B][I]
hi 
sorry to say. since i am very much towards linux and to get rid of windows. i have reinstalled the whole ubuntu again and configured again. so now it is working fine. i tried to remove some pakagees like that and i tried all option but i could not continue. so i lost the hope and reinstalled ubuntu 64 bit again and now i am doing good with the system. i am planning to buy ubuntu book and i will go through full on this to make myself one geek. thanks all for your support. now i am giving reply from the ubuntu new system only. thank you so much[/I][/B][/COLOR]:guitar::lolflag::popcorn:

---

### Post by northern lights on 2008-12-26
> **halovivek said:**
> hi 
sorry to say. since i am very much towards linux and to get rid of windows. i have reinstalled the whole ubuntu again and configured again.
I generally dislike giving a reinstall as advice, cause that's just cheap advice to give (as in, you need not ask a question in a support forum to be told to go reinstall your system, the requester can figure that on his/her own), but sometimes it's just the quickest solution.

Good to hear it works.

---

### Post by halovivek on 2008-12-27
> **northern lights said:**
> I generally dislike giving a reinstall as advice, cause that's just cheap advice to give (as in, you need not ask a question in a support forum to be told to go reinstall your system, the requester can figure that on his/her own), but sometimes it's just the quickest solution.

Good to hear it works.

i tried in lot of ways. but the main thing is if i do the problem again and again. my innner mind will get frustrated and will tend to leave. since i am practicing full towards linux so i have reinstalled again. thank you so much to all.

---

