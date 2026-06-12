---
title: "Internet connection sharing via wifi"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by BlaaaZ on 2009-03-19
I start with this "im new in ubuntu" so u need to answer me this way that i understand you.

My problem is internet connection sharing. I have PC what is connected to internet via cable and what is always on, no modems, no routers. Now my PC has WIFI card and i want to share my internet connection with wifi to other computer what is running on windows XP.

When both were running windows, it was quite easy. I set PC ips like this:

Ip address: 192.168.0.1
Subnet mask: 255.255.255.0

And Laptop used IPs

Ip address: 192.168.0.2
Subnet mask: 255.255.255.0
Default gateway 192.168.0.1

Preferred DNS server: 194.126.115.18

Then on PC i selected local ON LOCAL AREA CONNECTION....Share my internet connetion.

Then it was all working fine and i was connected with my laptop.

Any help? :popcorn:

PC: ubuntu 8.10
Laptop: windows XP

---

### Post by roblubbers on 2009-03-19
take a look at this how to: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by BlaaaZ on 2009-03-19
First command already gives me:

 keit@Keit:~$ ifconfig ethX ip 
ip: Unknown host
ifconfig: `--help' gives usage information.
keit@Keit:~$

---

### Post by blastus on 2009-03-19
It's complicated but looks like it's possible...
[Creating a wireless home network to share internet without router](http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html)

Also, the HowTo says...
> 1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

You don't actually enter "ifconfig ethX ip" You need to put in the name of your network interface (i.e. eth0, eth1, wlan0 etc...) and an ip address in place of "ip"

---

### Post by BlaaaZ on 2009-03-20
How do i know is it...i.e. eth0, eth1 or wlan0...or even something else, where do i look?

E: OK! i found it and im still stuck...

keit@Keit:~$ sudo iwconfig wlan0 essid "xxxx" mode Ad-Hoc key s:myweppasshere


And my network is named xxxx...

Still cant connect my windows XP machine to network, it finds it but doesnt connect.

---

### Post by blastus on 2009-03-20
"sudo ifconfig" will list all your network interfaces. "sudo iwconfig" is like ifconfig but is specifically for wireless interfaces.

The wireless interface will typically be wlan0 (or something like that.) On some systems it might actually be eth1 (like on a DD-WRT router.) Mine is rausb0 because I installed a customized wireless driver. You want to configure the wireless interface. 

If you list the output of "sudo ifconfig" and "sudo iwconfig" I can tell you what your wireless interface is.

---

### Post by BlaaaZ on 2009-03-22
keit@Keit:~$ sudo ifconfig
[sudo] password for keit: 
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:c0:df:82  
          inet addr:90.191.30.230  Bcast:90.191.31.255  Mask:255.255.254.0
          inet6 addr: fe80::20b:6aff:fec0:df82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:318320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:372080798 (372.0 MB)  TX bytes:17357455 (17.3 MB)
          Interrupt:23 Base address:0x6d00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2408 (2.4 KB)  TX bytes:2408 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:73:6b:13  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe73:6b13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2888 (2.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-73-6B-13-62-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

keit@Keit:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"internet"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: DE:59:1E:5E:A0:77   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

keit@Keit:~$

---

### Post by blastus on 2009-03-23
Your wireless interface is wlan0. You can run "sudo ifconfig" anytime to find out what the IP address of that interface is.

---

### Post by binbash on 2009-03-23
> **BlaaaZ said:**
> I start with this "im new in ubuntu" so u need to answer me this way that i understand you.

My problem is internet connection sharing. I have PC what is connected to internet via cable and what is always on, no modems, no routers. Now my PC has WIFI card and i want to share my internet connection with wifi to other computer what is running on windows XP.

When both were running windows, it was quite easy. I set PC ips like this:

Ip address: 192.168.0.1
Subnet mask: 255.255.255.0

And Laptop used IPs

Ip address: 192.168.0.2
Subnet mask: 255.255.255.0
Default gateway 192.168.0.1

Preferred DNS server: 194.126.115.18

Then on PC i selected local ON LOCAL AREA CONNECTION....Share my internet connetion.

Then it was all working fine and i was connected with my laptop.

Any help? :popcorn:

PC: ubuntu 8.10
Laptop: windows XP


at ubuntu create a new wireless connection, make it wep , put password.Then edit that connection and at ipv4 setting , select method automatic DHCP addresses only.That is all

---

### Post by BlaaaZ on 2009-03-24
Still, XP machine cant connect me :(

---

