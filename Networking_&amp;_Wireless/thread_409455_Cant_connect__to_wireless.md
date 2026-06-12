---
title: "Cant connect  to wireless"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by rickjs on 2007-04-14
I put the wireless setup in DHCP, put in my SSID, and all the other information on th connections tab......

What do I do now? I cannot connect to my router.

---

### Post by king_arthur on 2007-04-14
There could be countless reasons.

First of all, did your WiFi card get detected?


What is the output of iwconfig?

/P

---

### Post by rickjs on 2007-04-14
My wifi card did get detected, but I have no idea what iwconfig is. help

---

### Post by king_arthur on 2007-04-14
iwconfig is a command you should give from your shell.

It should return you an output like this:
```
wlan0     802.11b linked  ESSID:"home-net"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:24:04:88:F3   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-51 dBm  Noise level=-253 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```The above allows you to check the status of your card

/P

---

### Post by djknorr75 on 2007-04-14
I'm having the same problem in that my wireless card (D-Link DWL-G630) is detected, and I even seem to receive a weak signal, but am not able to connect to the network unless I use a wire.

Here is what I see when I run iwconfig:
```
wlan0     IEEE 802.11b+/g+  ESSID:"bigredmachine"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=49/100  Signal level=28/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The only differences I see between mine and yours is mine has a Nickname (I didn't create one?), and my Access Point does not appear to be defined.  

Any ideas what I might be doing wrong?:confused:

---

### Post by djknorr75 on 2007-04-14
Oh yeah, btw...don't know if matters or not (I suspect it does), but I am using Feisty.

---

### Post by funzero on 2007-04-15
My wireless had worked fine until the last update a couple of days ago.  Wireless show up and shows connected but I cannot connect to the Internet. I messed around and was finally able to ping the router and then it worked until I rebooted then ot broke again.  Problem is I don't know what I did to get ti to work  the first time.

---

### Post by king_arthur on 2007-04-15
What does **ifconfig** show you?

And what about /etc/resolv.conf ?

/P

---

### Post by djknorr75 on 2007-04-15
Here is what I get when I run ifconfig, but I really don't know what it is telling me for sure:

```
eth0      Link encap:Ethernet  HWaddr 00:0D:56:B0:2D:BC  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb0:2dbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:505051 (493.2 KiB)  TX bytes:43860 (42.8 KiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11722 (11.4 KiB)  TX bytes:11722 (11.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:4D:7E:7C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

wlan0:ava Link encap:Ethernet  HWaddr 00:0F:3D:4D:7E:7C  
          inet addr:169.254.5.213  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

```

When I tried to run /etc/resolv.conf, I received a message stating 'command not found'.  I should note that I had to use 'sudo' in front of the command, or else it told me that permission was denied.  Any thoughts?

---

### Post by StandardBlueCaboose on 2007-04-15
resolv.conf is a configuration file. Essentially it's a text file. You're going to want to view the contents using the following command:

```
sudo gedit /etc/resolv.conf
```

or, if you're running Kubuntu (or prefer Kate)

```
sudo kate /etc/resolv.conf
```

---

### Post by djknorr75 on 2007-04-15
Aha!  Must be a noob mistake....

When I run the command, there are only 2 lines in the text file:

```
# generated by NetworkManager, do not edit!

nameserver 192.168.0.1
```

I was wired into the network the first time, so I unplugged, but still had the same info in the file when I checked it again.....I'm not sure what to do at this point.  It seems like the latest update for Feisty helped a little, because I at least always see my card is connected now at about 47-50%, but it is never enough to actually use the internet.  I've got my fingers crossed that when they come out with the final release, this will be resolved.

---

### Post by Jongi on 2007-04-20
Same issue using feisty. It seems I am connected to the network but no internet access. Yet no internet access is possible. Netgear WG311v3. Used [this guide to install the wirelss](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W:B1_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29) and [this guide to setup WPA-PSK authentication](http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+wpa+psk). Except used the latest ndiswrapper. I've left the wireless IP as my  my soon to be ex iBurst provider does not give that IP range. The wlan0:ava is a first for me as well.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr yy:yy:yy:yy:yy:yy
          inet6 addr: fe80::20d:61ff:fe30:e190/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:107264602 (102.2 MiB)  TX bytes:14855620 (14.1 MiB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5846 (5.7 KiB)  TX bytes:5846 (5.7 KiB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet6 addr: fe80::214:6cff:fe31:6982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:170 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25312 (24.7 KiB)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:e6000000-e6010000

wlan0:ava Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:169.254.5.174  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:e6000000-e6010000

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_SSID"
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm
          RTS thr=2346 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto ppp0
iface ppp0 inet ppp
provider international

auto ppp1
iface ppp1 inet ppp
provider local

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
```

```

$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 192.168.1.1

```

```

$ cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="My_SSID"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
```

---

### Post by Jongi on 2007-04-21
I changed the wlan0 section of /etc/network/interfaces to look like:

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid YOUR_SSID
wpa-ap-scan 2
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Strange that it works although I didn't change YOUR_SSID to my actual SSID.

My /etc/wpa_supplicant.conf file now looks like this (pairwise and group commented out)::

```

$ cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="My_SSID"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       #pairwise=CCMP TKIP
       #group=CCMP TKIP
       psk=zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
```

---

