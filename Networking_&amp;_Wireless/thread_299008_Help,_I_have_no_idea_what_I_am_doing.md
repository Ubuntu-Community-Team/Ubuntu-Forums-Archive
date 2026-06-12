---
title: "Help, I have no idea what I am doing"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2006-11-13
Hello, sorry if this sounds silly, but I have no idea what I am doing. I am trying to get my wifi access to work on my Laptop, I have tried so many tutorials that I am quite confused now.

I will give you as much information as I can, and if some experienced user could help me out here I would appreciate it very much.

I have a wifi network at home running off a Netgear router with wpa-psk.

I have installed Ubuntu 6.06 (Dapper) on my Asus A6K laptop. (Its a dual boot system, I also have Windows XP on the hard disk).

My laptop has a mini pci Asus wifi card with a BCM4306 chip.

I DO NOT currently have access to the internet in Dapper since wifi is my only access right now. (So I usually boot into win xp, download what i need, copy it to the ubuntu partition and then boot into ubuntu).

I have tried several tutorials:
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) 
[http://www.ubuntuforums.org/showthread.php?t=263136&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=263136&highlight=wpa)
ndiswrapper
bcm43xx-fwcutter

But nothing seems to work.

After trying the above mentioned wpa tutorial I get this:

for iwconfig:

```
amr@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"ALH"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:B5:63:93:A2
          Bit Rate=11 Mb/s   Tx-Power=13 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=185/100
          Rx invalid nwid:0  Rx invalid crypt:1299  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

this iwlist:



```
amr@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
```

Thank you in advance to anyone who has the patience to guide me through this mess.

---

### Post by pnael on 2006-11-13
You are connected, since we can see a mac address for your access Point 
eth1      IEEE 802.11b/g  ESSID:"ALH"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:B5:63:93:A2
          Bit Rate=11 Mb/s   Tx-Power=13 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=185/100
          Rx invalid nwid:0  Rx invalid crypt:1299  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now please provide the output of 
ifconfig
route
cat /etc/resolv.conf

---

### Post by PartisanEntity on 2006-11-13
ifconfig:

```
amr@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:1B:B1:84
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xec00

eth1      Link encap:Ethernet  HWaddr 00:13:D4:30:AF:3A
          inet6 addr: fe80::213:d4ff:fe30:af3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207 errors:0 dropped:66 overruns:0 frame:0
          TX packets:1019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23391 (22.8 KiB)  TX bytes:58962 (57.5 KiB)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11268 (11.0 KiB)  TX bytes:11268 (11.0 KiB)
```

route:

```
amr@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

cat /etc/resolv.conf:

nothing noticeable happened when i typed this into the termainal

---

### Post by pnael on 2006-11-14
Hello,

You don't have an IP address for eth1. You are connected to
the access point but then you don't get any IP address.
please try the following :
>sudo dhclient eth1

You should get an ip address. If you have an error, let me know.
Provide the content of /etc/network/interfaces.

Regards

---

### Post by PartisanEntity on 2006-11-14
Hello again,

(I renamed eth1 to wlan0 just to keep track of it because it was confusing me)

sudo dhclient wlan0:

```
amr@ubuntu:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:13:d4:30:af:3a
Sending on   LPF/wlan0/00:13:d4:30:af:3a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

/etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid ALH
wireless-key mykey
pre-up wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

---

### Post by pnael on 2006-11-14
You don't receive an IP address via DHCP.
The link seems to be up but it looks that you don't have a running DHCP server on your network. Usualy it is provided by the access point (netgear router in your case).

- If you connect via ethernet to your netgear box, do you have an IP address ? 
- Under Windows please could you check if you have an fixed ip address
or an address via DHCP. The command is ipconfig /all in a dos box.

- Please provide the output of : cat /etc/wpa_supplicant.conf
Regards

---

### Post by PartisanEntity on 2006-11-14
Here is the output of ipconfig /all in win xp:

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : notebook
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection 3:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : ASUS 802.11g Netzwerkadapter
        Physical Address. . . . . . . . . : 00-13-D4-30-AF-3A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Dienstag, 14. November 2006 22:44:11

        Lease Expires . . . . . . . . . . : Dienstag, 19. J?nner 2038 04:14:07
```

Perhaps it might help you to know that on my router I have reserved a specific IP number for each laptop in the home network  based on MAC address. So my notebook has the number 192.168.1.2 as the reserved IP number.

Concerning ethernet, I have never used it (not even in win xp). I dont have an ethernet cable in the house. Just a router and a number of laptops all working with wifi.

I will boot into Ubuntu and post the contents of wpa_supplicant.conf

Thanks for all the help so far! :)

---

### Post by PartisanEntity on 2006-11-14
etc/wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="ALH"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP       
       psk=wb32fa92e6daeace246fa569d7e2f0d6dd943f6cea2d951ff45ee61c1d98bc12

}
```

---

### Post by PartisanEntity on 2006-11-15
I got myself an ethernet cable, and now I plugged into my router. I still have no ip number. I will try to restart now, and if this still doesnt work then i will reinstall ubuntu, perhaps by trying out so many tutorials I have changed certain important settings...

---

### Post by PartisanEntity on 2006-11-15
**pnael** 

I just wanted to thank you for your help. I reinstalled Dapper, but this time I had the ethernet cable plugged in. An ip number was assigned this time and I was able to update Dapper and then I picked one tutorial and followed it.

I am now proudly posting through my wireless network with ndiswrapper and wpa_supplicant.

Thanks for your help, I appreciate it :)

---

