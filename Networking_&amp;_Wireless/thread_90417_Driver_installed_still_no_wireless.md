---
title: "Driver installed still no wireless"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by majkmil on 2005-11-14
this is what I get with (lshw)

  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:0d:d5:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76c503 driverversion=v0.12beta23-fw_dwl firmware=1.101.4-84 wireless=IEEE 802.11-DS

And with (lsusb)

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin
Bus 001 Device 002: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 001 Device 001: ID 0000:0000

So my adapter is there and it seems to have a driver, any ideas why I can't get this to work?  

I still don't have connection. anyone know what to try?  Thanks

---

### Post by majkmil on 2005-11-14
Please help

---

### Post by Lambert on 2005-11-14
When you open networking does the wireless adapter show up in the list?

Are you using wep or wpa on your network?

post the output of iwconfig and ifconfig here.

Are you using dhcp or a static ip setting

---

### Post by majkmil on 2005-11-14
mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"okuwlan"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extension


mark@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:18:FF:0E:F7
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:feff:ef7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29384656 (28.0 MiB)  TX bytes:1548947 (1.4 MiB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6057459 (5.7 MiB)  TX bytes:6057459 (5.7 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:0D:D5:1A
          inet6 addr: fe80::20c:41ff:fe0d:d51a/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I am using DHCP

---

### Post by Lambert on 2005-11-15
Are you using encryption? If so wep or wpa?

post your /etc/network/interfaces file here.

---

### Post by majkmil on 2005-11-15
I put the ssid name of the network in preferences under WLAN0 and now I can ping my router and the other computers (wired) can ping me, I still cannot ping them. iwconfig now shows Accsess Point and signal level. Thanks for your help.
WEP is disabled




/etc/network/interfaces/

iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
wireless-essid Miller

---

### Post by majkmil on 2005-11-15
WOW, I diabled eth0 and I have internet! I still cannot ping the other computers but I see them on the network. Dont know about the ping issue but at least I can talk to you WIRELESSLY on my UBUNTU box. If you can think of wht I can't ping the other machines please post back. Otherwise thank You  Mark

---

