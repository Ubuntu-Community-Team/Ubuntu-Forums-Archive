---
title: "Intel ipw3945 Says 'Connected' But Can't Surf."
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by raid517 on 2006-12-04
Hi, I have an Intel 3945ABG Wireless Chip on my laptop. This chip works perfectly in Debian Kanotix/Sid.

However I cannot get it to work properly in Ubuntu. I used wireless assistant to connect - and it says I am connected. 

Wireless assistant is fairly easy to set up.

To do so I do the following:

I enter a static IP address of 192.168.1.104

25) I then enter a network mask of 255.255.255.0

26) I enter the broadcast address as 192.168.1.255

27) I enter the default gateway as 192.168.1.1

28 ) I enter the nameserver as 192.168.1.1

In the final step I enter my ASCII 13 character WEP key.

I then click on connect and a few seconds later I get a message saying I  am connected. However when I try to surf the internet or browse my network nothing happens.

Previously in Debian Sid/Kanotix my /etc/network/interfaces file was set up as follows:

```
# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)

# The loopback interface
# automatically added when upgrading
auto lo eth0 eth2
iface lo inet loopback

iface eth0 inet static
	address 192.168.2.104
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
#	gateway 192.168.1.1





iface eth2 inet static
	address 192.168.1.102
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
 wireless-mode Managed
 wireless_key s:MYWEPKEY

However in Kubuntu /etc/network/interfaces is configured  as follows:

[CODE]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
 wireless-essid MYNETWORK
```[/CODE]

Which is formatted really quite differently. I tried simply substituting my Kanotix /etc/network/interfaces file for the Kubuntu one - but that didn't work - and indeed even my wired network failed after a reboot. (Thankfully I had backed my original /etc/network/interfaces file up).

The output of ifconfig and iwconfig are as follows:


```
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:41:75:19
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe41:7519/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18719228 (17.8 MiB)  TX bytes:966007 (943.3 KiB)


eth1      Link encap:Ethernet  HWaddr 00:13:02:71:F2:A2
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63283 errors:1482 dropped:1488 overruns:0 frame:0
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:389469 (380.3 KiB)  TX bytes:17951 (17.5 KiB)
          Interrupt:185 Base address:0x2000 Memory:da000000-da000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14896 (14.5 KiB)  TX bytes:14896 (14.5 KiB)
```

```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Jebus97"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:C1:19:0F:0C
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-36 dBm  Noise level=-37 dBm
          Rx invalid nwid:0  Rx invalid crypt:1388  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0
```

So as you can see the network is associated, but it appears to be unable to obtain an IP address, or any routing/default gateway information etc.

The question is, how can I enter these details manually so that the system is able to correctly identify IP/routing/gateway information etc - and also so that I can ensure that this information is retained after each reboot?

---

### Post by raid517 on 2006-12-04
Anyone? Come on guys I thought the Ubuntu forums were supposed to be famously helpful?

All I am asking is is there a text file somewhere where these settings are usually stored?

---

