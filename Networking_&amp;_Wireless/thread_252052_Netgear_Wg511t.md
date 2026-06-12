---
title: "Netgear Wg511t"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by carlo bolzonello on 2006-09-06
Hi Guys,

I have a Netgear WG511T Pcmcia card in my notebook. It is seen by Ubuntu, however i cannot get it to connect to my wifi network?

I have attached a screen shot of the device detected

---

### Post by wieman01 on 2006-09-06
Please do the following steps:

1. Run "ifconfig" in a terminal and post the output (simply highlight it with your mouse pointer and press the mouse-wheel to paste).

2. Post the content of "/etc/network/interfaces":
> gedit /etc/network/interfaces
3. Please also tell us what your network's SSID is and whether you are using encryption such as WEP.

---

### Post by carlo bolzonello on 2006-09-06
carlob@Ubuntu-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:AF:2E:7D
          inet6 addr: fe80::20f:b5ff:feaf:2e7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1332 dropped:0 overruns:0 frame:1332
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:f8ba0000-f8bb0000

eth0      Link encap:Ethernet  HWaddr 00:0F:20:CA:8E:B5
          inet addr:10.12.1.89  Bcast:10.12.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:feca:8eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19553 errors:1 dropped:0 overruns:1 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:1475399 (1.4 MiB)  TX bytes:25044871 (23.8 MiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1164 (1.1 KiB)  TX bytes:1164 (1.1 KiB)



auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid NNB_CAPETOWN
wireless-key s:
auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 10.12.1.89
netmask 255.255.255.0
gateway 10.12.1.1





auto eth0

auto ath0

---

### Post by carlo bolzonello on 2006-09-06
[/quote]
3. Please also tell us what your network's SSID is and whether you are using encryption such as WEP.[/QUOTE]

we are using wep encryption:)

---

### Post by wieman01 on 2006-09-06
Ok, it seems that your interfaces file is the problem... Open it using this command:
> sudo gedit /etc/network/interfaces
Then change the file according to this:
> 
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid **your_essid**
wireless-key **your_hex_wep_key**

auto eth0
iface eth0 inet static
address 10.12.1.89
netmask 255.255.255.0
gateway 10.12.1.1

The second interfaces (eth0) is your ethernet adapter. We will ignore this one for now. Then simply add your SSID ("your_essid") and your network's WEP key ("your_hex_wep_key") in a hexidecimal format (NOT plain text).

Then save the file, restart the system, and see if you can connect to the Internet. 

BTW: I assume you are using DHCP? I am asking because your ethernet adapter expects a Static IP... Use DHCP in the first place, that's easier to start with.

---

### Post by carlo bolzonello on 2006-09-07
thried all you said, still no luck, we are using dhcp.... anything ilse i can try, i see the wireless manager sees the network, just doesnt like the key for some reason??

---

### Post by wieman01 on 2006-09-07
Can you post your interfaces file please? Please also include the key so that I can validate it. You can change it later on.

---

### Post by wieman01 on 2006-09-08
Please provide as much information as possible concerning your network. E.g. WPA1, WPA2, static IP or DHCP, ssid, network adapter you're using, etc. 

Turned out that this is a WPA network, not WEP.

---

### Post by bluevoodoo1 on 2006-09-09
I have the same notebooki card and I used ndiswrapper for the driver and it works...

though I do have another problem with it... [http://ubuntuforums.org/showthread.php?t=204875](http://ubuntuforums.org/showthread.php?t=204875)

---

