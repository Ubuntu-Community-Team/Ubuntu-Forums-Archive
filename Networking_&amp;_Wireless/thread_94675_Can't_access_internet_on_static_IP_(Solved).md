---
title: "Can't access internet on static IP (Solved)"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by LOMBAK on 2005-11-24
Hi,
I am a NewB
I can connect internet via my adsl using DHCP network settings but I can't connect to internet using static IP at office.(Windows NT LAN)

I can connect to internet using same IP/DNS config when using windows XP at the office. I need a speedy internet connection to install KDE on Ubuntu.

Can U help me pls?
:confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by darth_vector on 2005-11-24
have you set the default gateway? look in /etc/networking/interfaces for something like this:

auto eth0
iface eth0 inet static
        address 192.168.0.15
        netmask 255.255.255.0
        gateway 192.168.0.1

make sure that you have included the gateway line with the correct IP for the adsl router/modem.

---

### Post by mips on 2005-11-24
Give us some more details.
What is you default gateway ?
What is the netmask ?
Is there a firewall in use ?
 
Try disabling IPv6, search for posts with my username.

---

### Post by LOMBAK on 2005-11-24
mapping hotplug
            script grep
            map eth0

iface eth0 inet static
address 192.168.101.87
netmask 255.255.255.0
gateway 192.168.100.1

auto eth0

the auto eth0 line is in different position I guess

---

### Post by LOMBAK on 2005-11-24
I uninstalled F&#304;restarter after reading a post in another thread

---

### Post by darth_vector on 2005-11-24
the position of the "auto eth0" line doesnt matter. did un-installing firestarted fix your problem?

---

### Post by LOMBAK on 2005-11-24
Nope,
Uninstalling Firestarter does not help
By the way IPv6  disabling did not work either

---

### Post by darth_vector on 2005-11-24
hmm, can you ping the gateway? can you post the output of

ifconfig
route -n

---

### Post by LOMBAK on 2005-11-25
I am gratefull for your interest. 
here is the output:

ifconfig
eth0      
          inet addr:192.168.101.87  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe2b:a8ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59580 (58.1 KiB)  TX bytes:308 (308.0 b)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21791 (21.2 KiB)  TX bytes:21791 (21.2 KiB)

route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

There is a line ifconfig about my comps mac address but i forgot to copy it while switching btw OSes.

---

### Post by LOMBAK on 2005-11-25
By the way I tried to connect internet on Synaptics, FireFox and pinging on static IP none is working:???:

---

### Post by darth_vector on 2005-11-25
you will have to set a default route for 0.0.0.0. have a look at man route (default gateway).

---

### Post by LOMBAK on 2005-11-25
How can I edit the  defaolut route 0.0.0.0 gateway.
Editing the network connection settings does not solve the problem.

Should I use the terminal???:

---

### Post by mips on 2005-11-25
Your eth0 and gateway are in different subnets ?! How are the packets supposed to get from the one network to the other, do you have a router between the two subnets ?

Your PC and gateway have to be in the same network/subnet in order to work. 

Your PC is part of network 192.168.101.0
Your Gateway is part of network 192.168.100.0
These are two totally seperate networks and the only way to get packets from the one to the other is by having a router between the two.

You will have to move your PC to the 192.168.100.0 network if you want to achieve any type of connectivity.

You are trying to defy the rules of the TCP/IP architecture here ;)

---

### Post by LOMBAK on 2005-11-25
address 192.168.101.87
netmask 255.255.255.0
gateway 192.168.100.1

DNS 193.255.237.2
DNS 80.251.40.10

This is the config of WinXp network config.(Connecting)
Can U guide me a little bit more pls
I enter both DNS into DNS tab of network config but does not solve the problem

---

### Post by LOMBAK on 2005-11-25
I want to get rid of the WinXP but w/o internet connection I can't.
:(

---

### Post by teaker1s on 2005-11-25
it could be the router dns issue I had try- using the isp dns server ip manually in ubuntu and not trying to get it from router

---

### Post by mips on 2005-11-25
[QUOTE=LOMBAK]How can I edit the  defaolut route 0.0.0.0 gateway.
Editing the network connection settings does not solve the problem.

Should I use the terminal???:[/QUOTE]

To add a default route open a terminal and enter:

**sudo route add default gw 192.168.100.1**

---

### Post by LOMBAK on 2005-11-25
OK I will try to add the default gateway during office hours.
Thanks a lot.
 I will return with the result .

\\:D/ \\:D/ \\:D/ \\:D/

---

### Post by LOMBAK on 2005-11-27
sudo route add default gw 192.168.100.1

returns with network inaccessable reply

I connected internet via ADSL last night so ethernet card and network app working but needs manual tuning I think

---

### Post by LOMBAK on 2005-11-27
on the terminal screen I wrote network-admin to start the app

and returned with:

CRITICAL**:gst_xml_element_destroy:assertion `node !=NULL`failed 


:confused: :confused: :confused:

---

### Post by LOMBAK on 2005-11-27
:smile: :smile: :smile: :smile: 
SOLVED the problem by getting a new IP on the xxx.xxx.100.xxx
network.

UBUNTU cannot access networks divided into subnetworks 

I guess

---

### Post by LOMBAK on 2005-11-27
THANKS TO YOU ALL

THIS IS THE REASON WHY I LIKE OPEN SOURCE

[B][COLOR="Red"]IDEA OF UNITY
FEELING OF FREEDOM UNITES PEOPLE[/COLOR][/B]

[COLOR="red"]***[SIZE="6"]OPEN SOURCE FOR OPEN MINDED PEOPLE [/SIZE]***[/COLOR]


SHOULD I REPORT THIS ISSUE TO THE ADMINS (IS THIS A POINT TO BE WORKED ON OR A FAULT OF MY OFFICE NETWORK)

---

### Post by mips on 2005-11-27
Great! Dont say I did not tell you so ;)

No need to report this to the admins as your configuration was wrong/invalid. The behaviour was 100% correct.

---

