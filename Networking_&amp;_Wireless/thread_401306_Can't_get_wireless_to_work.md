---
title: "Can't get wireless to work"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by trevoore on 2007-04-04
Hi!

I'm basically a beginner, but I thought I'd post this here anyway. 
I can't get my wireless to work. I'm using Xubuntu 7.04
Wifi-Radar can find my network and connect to it. It can't acquire an IP address with DHCP. If I give it a static IP adress, Wifi-Radar claims to be connected, but my PCMCIA Wifi-Card (no-name card apparently with an Atheros chipset) still blinks the way it blinks when its disconnected in Windows and I can't connect to the Internet with Firefox.

Here's what I've found in the Forum and tried:
I can ping myself but not the router
I've tried taking out the WPE Key, it doesn't make a difference
I can't access google with 64.233.167.99
I've turned off Ipv6 in Firefox

Heres the output from iwconfig and ifconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"FRITZ!Box SL WLAN"  Nickname:"FRITZ!Box SL WLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:32167  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:03:7F:1E:F4:38  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::203:7fff:fe1e:f438/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:03:0D:09:AD:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27806 (27.1 KiB)  TX bytes:27806 (27.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-03-7F-1E-F4-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41979 errors:0 dropped:0 overruns:0 frame:38595
          TX packets:7285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4339855 (4.1 MiB)  TX bytes:380347 (371.4 KiB)
          Interrupt:16 

I'd be happy if you had any suggestions!

t

---

### Post by Tilex on 2007-04-04
Try doing:

```

sudo iwconfig ath0 essid YOUR_NETWORK_NAME key YOUR_KEY mode managed
sudo dhcpcd ath0

```

Tell me if it works.  You may need to install the command "dhcpcd" prior to doing the last step.  You can find it in the Synaptic Package Manager

---

### Post by trevoore on 2007-04-04
Hi!

Thanks alot for your help!

Here's the output for the first command:

sudo iwconfig essid FRITZ!Box SL WLAN key 0525329647431 mode managed
bash: !Box: event not found

My dear, now I'm posting the entrance data to my wireless network on the internet. Oh no, horrible. ;-)
Is the error because of the exclamation mark? Is there something I have to change for exclamation marks and spaces?

After installing dhcpcd and trying the second command without the first one working nothing happens. I have to close the terminal and start a new one to be able to use it again. 

Again: Your help is very appreciated.

Cheers,
t

---

