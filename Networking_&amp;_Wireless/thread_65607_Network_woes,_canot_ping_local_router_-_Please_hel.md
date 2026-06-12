---
title: "Network woes, canot ping local router - Please help a newb"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by reddwarfusa on 2005-09-14
Hi All

I'm hoping you can help, I am finally trying (and I mean trying) to take the leap to linux.  BUT>>I have installed a lovely version of UBUNTU but cannot get connectivity to the internet.  I have a US robotics wireless card installed (USR5410) and have assigned static ip address and CAN ping that address fine as well as loopback address.  BUT I cannot pint my local router (192.168.1.1) or and website.  I have attached hopefully some of the info which may help to track it down.  I've also tried using lan cable with the same issue, PLEASE HELP!!!!

ctwiner@Linuxlaptop:/var/lib$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:317828 (310.3 KiB)  TX bytes:317828 (310.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:49:D7:08:17
          inet addr:192.168.1.161  Bcast:192.168.1.255  Mask:255.255.0.0
          inet6 addr: fe80::2c0:49ff:fed7:817/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1764 (1.7 KiB)
          Interrupt:10

ctwiner@Linuxlaptop:/var/lib$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

ctwiner@Linuxlaptop:/var/lib$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.071 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.053 ms

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.053/0.062/0.071/0.009 ms
ctwiner@Linuxlaptop:/var/lib$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 wlan0
default         reddwarfusa     0.0.0.0         UG    0      0        0 wlan0
ctwiner@Linuxlaptop:/var/lib$

---

### Post by mlomker on 2005-09-15
What is the output of **iwconfig**?

---

### Post by reddwarfusa on 2005-09-15
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"reddwarfusa"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:B1:30:10
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:7265-6464-7761-7266-7573-6100-00   Security mode:open
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Hope that helps

---

### Post by mlomker on 2005-09-15
I recommend disabling encryption on your router until you're sure that everything works.

The link quality is also *really* bad.  Move closer to your access point, if possible, while testing stuff out.

---

### Post by reddwarfusa on 2005-09-15
I have done that but i also get the same problem if I plug into ethernet, I will disable connection and resend logs

---

### Post by reddwarfusa on 2005-09-15
ctwiner@Linuxlaptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:357886 (349.4 KiB)  TX bytes:357886 (349.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:49:D7:08:17
          inet addr:192.168.1.161  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fed7:817/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2203 (2.1 KiB)  TX bytes:7456 (7.2 KiB)
          Interrupt:10

ctwiner@Linuxlaptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

ctwiner@Linuxlaptop:~$ ping 192.168.1.161
PING 192.168.1.161 (192.168.1.161) 56(84) bytes of data.
64 bytes from 192.168.1.161: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 192.168.1.161: icmp_seq=2 ttl=64 time=1.50 ms

--- 192.168.1.161 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.058/0.783/1.508/0.725 ms
ctwiner@Linuxlaptop:~$

Here are the iwconfig and ifconfig after I turned up the power and removed encryption from my router, incidentally this works perfectly in windows with no issue. 

Thanks for the help so far

Chris

---

### Post by reddwarfusa on 2005-09-15
ctwiner@Linuxlaptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"reddwarfusa"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:B1:30:10
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:7265-6464-7761-7266-7573-6100-00   Security mode:open
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ctwiner@Linuxlaptop:~$

resending due to forgotten iwconfig

---

### Post by reddwarfusa on 2005-09-15
Here are the files

---

### Post by mlomker on 2005-09-15
# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface wlan0 inet dhcp
iface eth0 inet dhcp

---

