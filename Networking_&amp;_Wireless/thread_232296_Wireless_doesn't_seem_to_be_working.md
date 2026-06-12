---
title: "Wireless doesn't seem to be working"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by pcnomad on 2006-08-08
Ubuntu 6.06 on older celeron 433Mhz with a Linksys WMP54G PCI adapter and a ethernet adapter.
I'm using a Linksys WRT54GS router to my broadband.
The hard wire is working but the wireless doesn't seem to be working.
Here is the result of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:03:47:24:F6:62
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe24:f662/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:855397 (835.3 KiB)  TX bytes:107848 (105.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35927 (35.0 KiB)  TX bytes:35927 (35.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:16:B6:9A:DA:CF
          inet6 addr: fe80::216:b6ff:fe9a:dacf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:977 errors:9 dropped:9 overruns:0 carrier:0
          collisions:17 txqueuelen:1000
          RX bytes:3725293 (3.5 MiB)  TX bytes:60680 (59.2 KiB)
          Interrupt:9

Here is the result of iwconfig:

lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"molerwireless"
          Mode:Managed  Frequency:11 MHz  Access Point: 00:13:10:05:4A:96
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/70  Signal level:-39 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

I'm using 128 bit WEP and have entered the key into the network manager but no wireless.
Any help would be appreciated.
P.S. I'm somewhat new to Linux, so easy on the programming jargon please.

---

### Post by jeff_ on 2006-08-08
Well from your iwconfig output it looks like your wireless card has successfully connected with the wireless access point (since it shows its MAC address). However, from your ifconfig output you can see that your wireless card (ra0) doesn't have an ip address.

Are you using dhcp to automatically retrieve an ip or do you statically assign one? Either can be setup by going to System > Administration > Networking and then adjusting the properties of your Wireless connection.

---

### Post by pcnomad on 2006-08-10
I have it set to use DHCP in the wireless manager. I'm not real sure of what I would be doing to set it up with static IP. Any help would be just wonderful.

---

### Post by jeff_ on 2006-08-10
Well is your wireless router setup to use DHCP?

---

### Post by flub on 2006-08-12
Jeff, I am having the same problem.

I use static IP addressing and like the OP I have appear to have connected to the Router but I cannot ping/browse/email etc. (My iwconfig output is near identical)

My setup has been workign fine for nearly 2 years but since the last kernal update its not connected.

I know the card is ok as when I use it on another Windows XP pc is works fine.

Any hints/tips help would be greatly appreciated.

---

### Post by jeff_ on 2006-08-12
> **flub said:**
> Jeff, I am having the same problem.

I use static IP addressing and like the OP I have appear to have connected to the Router but I cannot ping/browse/email etc. (My iwconfig output is near identical)

My setup has been workign fine for nearly 2 years but since the last kernal update its not connected.

I know the card is ok as when I use it on another Windows XP pc is works fine.

Any hints/tips help would be greatly appreciated.

Honestly I'd make a new thread anyway just to get more attention. Also are you saying that you have a static IP set on your wireless interface, but in ifconfig it doesn't show up?

---

### Post by jeff_ on 2006-08-12
> **jeff_ said:**
> Well from your iwconfig output it looks like your wireless card has successfully connected with the wireless access point (since it shows its MAC address). However, from your ifconfig output you can see that your wireless card (ra0) doesn't have an ip address.

Are you using dhcp to automatically retrieve an ip or do you statically assign one? Either can be setup by going to System > Administration > Networking and then adjusting the properties of your Wireless connection.

Let me apologize since I misread your output. Your DHCP does seem to be working as you have received an IP address (192.168.1.103). Try pinging your wireless router or if you don't know its address ping 192.168.1.255 and see if you get a reply.

---

### Post by pcnomad on 2006-08-12
Alright, finally got around the boot hang-up, Thanks alot.
Now back to the original problem, no wireless. Once I got to the desktop I configured the wireless card (Linksys WMP54G) but still no wireless. I think its connecting but no internet.
I then: cat /etc/resolv.conf and my ISP's primary and secondary DNS servers are listed.
Now what? I have no clue what I'm doing! But I'm not going to give up!

Here is the output of ifconfig:

ra0 Link encap:Ethernet HWaddr 00:16:B6:9AA:CF
inet addr:192.168.1.116 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::216:b6ff:fe9a:dacf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:15274 errors:0 dropped:0 overruns:0 frame:0
TX packets:1704 errors:5 dropped:5 overruns:0 carrier:0
collisions:38 txqueuelen:1000
RX bytes:1305066 (1.2 MiB) TX bytes:93214 (91.0 KiB)
Interrupt:9

Here is the output of iwconfig:

ra0 RT61 Wireless ESSID:"startrek"
Mode:Managed Frequency:11 MHz Access Point: 00:13:10:05:4A:96
Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=100/70 Signal level:-31 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have the router set to no encryption. I don't know what else to look at.

---

### Post by jeff_ on 2006-08-12
Well you are connected to the wireless router so there doesn't seem to be a problem with your wireless card. Can you ping your router though? If you don't know its IP address try pinging 192.168.1.255

Do you have a dual boot with windows setup or a wired connection to the internet on linux? How are you connecting right now?

---

### Post by flub on 2006-08-15
Jeff, same problem for me as well. It says I'm connected but I cannot ping the Router.

This has been working for months until the latest Kernal Update. Is there anything I can do/check ?

---

### Post by jeff_ on 2006-08-15
> **flub said:**
> Jeff, same problem for me as well. It says I'm connected but I cannot ping the Router.

This has been working for months until the latest Kernal Update. Is there anything I can do/check ?

Are you getting an IP? Static/DHCP?

---

