---
title: "Please help, can't ping LAN by default, but can get to internet"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by unco on 2006-10-05
I am at the very last stage of configuring my wireless network, but have one last problem to solve (this is a call for HELP).

If I ping a LAN IP address without the -I flag it fails, but works when I secify -Iwlan0 in the ping command.

Can someone please tell me how to get the wlan0 interface to work by default?

Example:
```
xxx@xxx:~$ ping -c4 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.254 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3021ms
, pipe 3

xxx@xxx:~$ ping -c4 -Iwlan0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.101 wlan0: 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=128 time=1.53 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=128 time=1.40 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=128 time=1.45 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=128 time=1.44 ms

--- 192.168.1.254 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3012ms
rtt min/avg/max/mdev = 1.404/1.459/1.534/0.060 ms
```
Network & Wireless Configuration:
```
xxx@xxx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:61:91:FA:57
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2928 (2.8 KiB)  TX bytes:2928 (2.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:76:70:D8:D3
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe70:d8d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1701188 (1.6 MiB)  TX bytes:377617 (368.7 KiB)
          Interrupt:217 Memory:ee000000-ee002000
```
eth0 will generally be unplugged, so want this to works so I can ssh to my server.
```
xxx@xxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MyEssid"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:04:ED:0A:09:B1
          Bit Rate:24 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-76 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
My /etc/network/interfaces contains:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.101
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254

auto wlan0
# iface wlan0 inet dhcp
iface wlan0 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254
pre-up modprobe ndiswrapper
pre-up iwconfig wlan0 essid MyEssid
pre-up iwconfig wlan0 mode Managed
pre-up ifconfig wlan0 up
pre-up wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw
post-down killall -q wpa_supplicant
```
My /etc/wpa_supplicant.conf contains:
```
# ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="MyEssid"
	proto=WPA
	key_mgmt=WPA-PSK
	psk="wouldntulike2no"
}
```

---

### Post by unco on 2006-10-05
More info:
```
xxx@xxx:~$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

help? anyone?

---

### Post by unco on 2006-10-05
I have found a manual workaround, but want to automate does anyone have ideas?

In /etc/network/interfaces switch the positions of the eth0 and wlan0 defintions, so wlan0 comes first.  Then do
```
sudo /etc/init.d/networking restart
```
Also after every restart have to do the above to resolve init ping behaviour.  Does anyone know how to get this to happen at startup?

---

### Post by spd106 on 2006-10-07
You a routing conflict, as you can see from the routing table you have two default routes. I'm not sure that I can give you the solution as I don't understand the way you are using the network cards. 

You can add a line in the interfaces file to remove the other route. ie when you plug in eth0 it removes wlan0 as the default route interface and adds eth0 instead. Something like **post-up ip route replace default via 192.168.1.254 dev eth0 ** and likewise for wlan0. Check out **man ip** for the details.

The easiest way would be to use network manager, which does this automatically, but it doesn't support static addresses at the moment.

---

### Post by unco on 2006-10-08
The way I use my NICs are:

1. All the time using wlan0, to access internet and lan.
2. But on rare occasions if I have a large downloaded file or multiple files to transfer from my download server to my desktop machine, I plug in the wired eth0 to speed up the process. (only rarely done as means having to run a cable thru the middle of the house).

Thanks for the info I will review later.

---

### Post by unco on 2007-02-27
Added to interface file following put wireless first for lan.

```
sudo gedit /etc/network/interfaces
```

```
post-up route del -net 192.168.1.0 netmask 255.255.255.0 dev eth1
post-up route add -net 192.168.1.0 netmask 255.255.255.0 dev eth1
```

---

