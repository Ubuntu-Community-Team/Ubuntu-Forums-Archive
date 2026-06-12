---
title: "Sierra Wireless 340U (AT&amp;T Beam) Ubuntu Desktop 13.10"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by guy6 on 2013-11-19
I have a AT&T Beam (Sierra 340U) that I can't get to work on my desktop. I have installed it on Mac and Windows and it is working there so assuming the hardware is healthy. The device is recognized by tghe system and I can get an IP address for it but can't ping. Perhaps I have a network configuration error but tcpdump shows an oddity in ethernet headers and am hoping someone can help me get this working correctly. On transmit the SA and DA are the same for the ping request. The ping reply has a SA of all zero and the DA looks correct. These might just be an artifact of the way the driver works. Still, at the end of the day I get no ping response and am not sure why. Any help appreciated.

Here are what I believe to be the pertinent facts:

    
```
~$ uname -pr
3.11.0-13-generic x86_64

```

```
guy@quijos:~$ dmesg

[430611.495719] usb 5-2: new high-speed USB device number 5 using xhci_hcd
[430611.513716] usb 5-2: config 1 has an invalid interface number: 9 but max is 0
[430611.513727] usb 5-2: config 1 has no interface number 0
[430611.514830] usb 5-2: config 2 has an invalid interface number: 12 but max is 1
[430611.514839] usb 5-2: config 2 has an invalid interface number: 13 but max is 1
[430611.514844] usb 5-2: config 2 has an invalid interface number: 13 but max is 1
[430611.514849] usb 5-2: config 2 has no interface number 0
[430611.514852] usb 5-2: config 2 has no interface number 1
[430611.516377] usb 5-2: New USB device found, idVendor=1199, idProduct=0fff
[430611.516387] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[430611.516392] usb 5-2: Product: AirCard 340U
[430611.516396] usb 5-2: Manufacturer: Sierra Wireless, Incorporated
[430611.516400] usb 5-2: SerialNumber: 013323000546953
[430611.519228] usb-storage 5-2:1.9: USB Mass Storage device detected
[430611.520635] usb-storage: probe of 5-2:1.9 failed with error -5

```

```

guy@quijos:~$ lsmod | grep cdc
cdc_mbim               13176  0 
cdc_ncm                20024  1 cdc_mbim
cdc_wdm                18919  1 cdc_mbim
usbnet                 39495  2 cdc_mbim,cdc_ncm

```

```

guy@quijos:~$ ifconfig wwan0
wwan0     Link encap:Ethernet  HWaddr 2e:ac:8b:f0:c0:8f  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

guy@quijos:~$ sudo mbim-network /dev/cdc-wdm0 start
Loading profile...
    APN: broadband
Loading previous state...
    Previous Transaction ID: 6
error: no actions specified
Clearing state...
Querying subscriber ready status 'mbimcli -d /dev/cdc-wdm0 --query-subscriber-ready-status --no-close'...
[/dev/cdc-wdm0] Subscriber ready status retrieved: Ready state: 'initialized' Subscriber ID: '310410629532284' SIM ICCID: '89014103276295322843' Ready info: 'unknown' Telephone numbers: (1) '16502728289' [/dev/cdc-wdm0] Session not closed: TRID: '3'
Saving state... (TRID: 3)
Querying registration state 'mbimcli -d /dev/cdc-wdm0 --query-registration-state --no-open=3 --no-close'...
[/dev/cdc-wdm0] Registration status: Network error: 'unknown' Register state: 'home' Register mode: 'automatic' Available data classes: 'lte' Current cellular class: 'gsm' Provider ID: '310410' Provider name: 'AT&T' Roaming text: 'unknown' Registration flags: 'manual-selection-not-available' [/dev/cdc-wdm0] Session not closed: TRID: '4'
Saving state... (TRID: 4)
Attaching to packet service with 'mbimcli -d /dev/cdc-wdm0 --attach-packet-service --no-open=4 --no-close'...
Saving state... (TRID: 5)
Starting network with 'mbimcli -d /dev/cdc-wdm0 --connect=broadband --no-open=5 --no-close'...
Network started successfully
Saving state... (TRID: 6)


```

```

guy@quijos:~$ sudo dhclient wwan0
dhclient-exit-hooks.d/hostname: Dynamic IP address = 10.187.216.20
hostname: the specified hostname is invalid
dhclient-exit-hooks.d/hostname: Dynamic Hostname = 3(NXDOMAIN)

guy@quijos:~$ ifconfig wwan0
wwan0     Link encap:Ethernet  HWaddr 2e:ac:8b:f0:c0:8f  
          inet addr:10.187.216.20  Bcast:10.187.216.23  Mask:255.255.255.252
          inet6 addr: fe80::2cac:8bff:fef0:c08f/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1430  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1419 (1.4 KB)  TX bytes:48248 (48.2 KB)



guy@quijos:~$ ping -I wwan0 8.8.8.8
PING 8.8.8.8 (8.8.8.8) from 10.187.216.20 wwan0: 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms

```

```

sudo tcpdump -e -i wwan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wwan0, link-type EN10MB (Ethernet), capture size 65535 bytes


11:39:07.028503 2e:ac:8b:f0:c0:8f (oui Unknown) > 2e:ac:8b:f0:c0:8f (oui Unknown), ethertype IPv4 (0x0800), length 98: 10.187.216.20 > google-public-dns-a.google.com: ICMP echo request, id 19244, seq 1, length 64
11:39:07.342582 00:00:00:00:00:00 (oui Ethernet) > 2e:ac:8b:f0:c0:8f (oui Unknown), ethertype IPv4 (0x0800), length 98: google-public-dns-a.google.com > 10.187.216.20: ICMP echo reply, id 19244, seq 1, length 64
11:39:08.027661 2e:ac:8b:f0:c0:8f (oui Unknown) > 2e:ac:8b:f0:c0:8f (oui Unknown), ethertype IPv4 (0x0800), length 98: 10.187.216.20 > google-public-dns-a.google.com: ICMP echo request, id 19244, seq 2, length 64
11:39:08.390364 00:00:00:00:00:00 (oui Ethernet) > 2e:ac:8b:f0:c0:8f (oui Unknown), ethertype IPv4 (0x0800), length 98: google-public-dns-a.google.com > 10.187.216.20: ICMP echo reply, id 19244, seq 2, length 64


```

---

### Post by guy6 on 2013-12-06
This is not a problem with the 340U, this is simply a problem with setting up a incoming route and a default gateway range for the new wireless interface.

[FONT=Menlo]IF2_DEV=wwan0[/FONT]
[FONT=Menlo]IF2_ADR=10.88.163.24[/FONT]
[FONT=Menlo]IF2_NET=10.88.163.0/24[/FONT]
[FONT=Menlo]IF2_DGW=10.88.163.25[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# make a new routing table #1 and call it admin. this only needs to be done once[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# echo "1 admin" >> /etc/iproute2/rt_tables[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# populate the new admin table with info about the wwan subnet and default gw[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]ip route add $IF2_NET dev $IF2_DEV src $IF2_ADR table admin[/FONT]
[FONT=Menlo]ip route add default via $IF2_DGW dev $IF2_DEV table admin[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# you can do an 'ip rule show here' to see current state[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]ip rule add from $IF2_NET table admin[/FONT]
[FONT=Menlo]ip rule add to $IF2_NET table admin[/FONT]
[FONT=Menlo]ip route flush cache[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# ip rule show[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]# all traffic to and from $IF2_NET now uses table 'admin'[/FONT]
[FONT=Menlo]#[/FONT]

---

### Post by davidpellerin-maison on 2014-02-20
Hello Guy6. I have the same problem with my Sierra 330U Rogers... Although I understand the mechanic behind your explanation, I was wondering if you could let me know which file you modified to make the problem go away?

Thanks in advance

---

