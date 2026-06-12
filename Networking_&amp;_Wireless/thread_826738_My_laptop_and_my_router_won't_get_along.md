---
title: "My laptop and my router won't get along"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by vinter on 2008-06-12
Hey,

I have a cheap-ish router, a **"DI-524UP"** from D-Link and an old Fujitsu Siemens **Lifebook E7110** laptop. When I had XP on the laptop, it could see the wireless networks of the neighbours and the school and restaurant across the street, but not my own! My other laptop could see it with full signal strength -- much stronger than the other networks.

So I did what was long overdue and put Ubuntu on the old one. It will connect to my cable modem directly, but not to the router: Not wirelessly, not wired! As I said, my new laptop has no trouble with that.

Here is what I do:

0) I **reset the router** to factory settings. It seems like it still keeps the updated firmware, though. I only change the ssid to **micro** and leave everything else.
1) In the Network Settings GUI, I set the DNS to the IPs of OPENDNS.
2) In there I notice that there are** two wireless interfaces** listed, "wifi0" and "wlan0". I would think, there is only one card in the machine!?
3) I then go onto the [HOWTO from this sub-forum]("http://ubuntuforums.org/showthread.php?t=684495"):
```
root@sionko:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:e0:00:ae:1a:51
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=88.212.85.94 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       **logical name: wifi0**
       version: 01
       serial: 00:e0:00:87:5c:4e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes **driver=hostap** firmware=1.4.1 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
```

But the [Wiki page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCisco") says that the driver should be called airo or airo_cs. **Is this a problem? And in that case, how do I change it?** And to what: airo or airo_cs?
4) **Unencrypted connection:**
```

root@sionko:~#  ifconfig wifi0 down
root@sionko:~# dhclient -r wifi0
There is already a pid file /var/run/dhclient.pid with pid 8457
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

[B]wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801[/B]
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
root@sionko:~# ifconfig wifi0 up
root@sionko:~# iwconfig wifi0 essid "micro"
root@sionko:~# iwconfig wifi0 mode Managed
root@sionko:~# dhclient  wifi0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@sionko:~# ping 64.233.161.44  # = google.com
PING 64.233.161.44 (64.233.161.44) 56(84) bytes of data.
From 88.212.85.94 icmp_seq=1 Destination Host Unreachable
From 88.212.85.94 icmp_seq=2 Destination Host Unreachable
From 88.212.85.94 icmp_seq=3 Destination Host Unreachable

--- 64.233.161.44 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5029ms
, pipe 3
root@sionko:~# 



```

But I wonder first of all if this is an Ubuntu problem or a router problem. Shall I go dish up the cash for a new and better router? Although it works fine with my newer laptop. 
Why can't those kids just get along?!

---

### Post by chili555 on 2008-06-12
I see a couple of issues here. First, Network Manager, which is installed by default, will not allow a wireless connection while a wired is available. [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

You have a working IP address with your wired connection:> ip=88.212.85.94 latency=64 link=yesSo, before you try to activate your wireless, please detach the wire and reboot.

Next, there is no evidence that your wireless card is a Cisco Aironet.> product: Prism 2.5 Wavelan chipset
       vendor: Intersil CorporationPerhaps some E7110's came with Aironet cards, but not this one.

With the wire detached and after a reboot, please do:```
**sudo** iwconfig wlan0 essid micro
sudo dhclient wlan0
```Did you connect?

---

### Post by vinter on 2008-06-12
Hey Chili555 and thanks for your fast answer,

> **chili555 said:**
> 
So, before you try to activate your wireless, please detach the wire and reboot.

Ahhhh. I just took it out without rebooting. I wanted it, so I could post all the output. But with that and

> **chili555 said:**
> ```
**sudo** iwconfig wlan0 essid micro
sudo dhclient wlan0
```

it works. Thnaks!
But why **"wlan0"** and not **"wifi0"**? 

Then on to ... you guessed it: **WPA**. Following the guide, I put the network cable in the other computer, changed the router to WPA-PSK with an easy password for a start. 
wpasupplicant was already installed for some reason. Not by me.

```
root@sionko:/# cat /etc/wpa_supplicant.conf
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="micro"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="1234" # I actually used something different. But...
        pairwise=TKIP
        group=TKIP
}

```

I notice that **/var/run/wpa_supplicant does not exist**. Is that a problem?

```
[B]root@sionko:/# ifconfig wifi0 down 
root@sionko:/# dhclient -r wifi0[/B]
There is already a pid file /var/run/dhclient.pid with pid 7088
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
**root@sionko:/# wpa_supplicant -w -D hostap -i wifi0 -c /etc/wpa_supplicant.conf -dd**
Initializing interface 'wifi0' conf '/etc/wpa_supplicant.conf' driver 'hostap' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     6d 69 63 72 6f                                    micro           
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='micro'
Initializing interface (2) 'wifi0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:e0:00:87:5c:4e
wpa_driver_hostap_set_wpa: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Driver does not support WPA.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface wifi0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wifi0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 176 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 176 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
No suitable AP found.
Setting scan request: 5 sec 0 usec
Ignore event for foreign ifindex 4
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 373 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Ignore event for foreign ifindex 4
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wifi0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
**root@sionko:/# ifconfig wifi0 up**
**root@sionko:/# iwconfig wifi0 mode Managed**
**root@sionko:/# dhclient  wifi0**
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
**root@sionko:/# ping 64.233.161.44**
PING 64.233.161.44 (64.233.161.44) 56(84) bytes of data.
From 192.168.0.101 icmp_seq=1 Destination Host Unreachable
From 192.168.0.101 icmp_seq=2 Destination Host Unreachable
From 192.168.0.101 icmp_seq=3 Destination Host Unreachable
From 192.168.0.101 icmp_seq=4 Destination Host Unreachable
From 192.168.0.101 icmp_seq=5 Destination Host Unreachable
From 192.168.0.101 icmp_seq=6 Destination Host Unreachable

--- 64.233.161.44 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6016ms
, pipe 3

```

"KBH Skolernes UNDERVISNING" is the wifi of the neighbour school.

Thanks again in advance for any suggestions -- and I know I should not be running as root, but it is just so much easier with history commands and that kind of thing.

---

### Post by chili555 on 2008-06-12
I don't know why some interfaces get assigned two logical names. Mine has eth1 and wmaster0. The reason I suggested wlan0 is this:> wifi0: unknown hardware address type 801and when you tried wlan0:> it works. Thnaks!Please try this again with the known working interface, wlan0:> wpa_supplicant -w -D hostap -i **wlan0** -c /etc/wpa_supplicant.conf -ddThen let's troubleshoot. Also, may I please see:```
lsmod | grep prism
```the prism2 drivers should not be loaded, however, I notice this:> ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Driver does not support WPA.I wonder why you proceeded with wifi0, since you know it doesn't work and wlan0 does.> root@sionko:/# ifconfig wifi0 up
root@sionko:/# iwconfig wifi0 mode Managed
root@sionko:/# dhclient  wifi0

---

### Post by vinter on 2008-06-12
Hey again,

With wlan0:

> [B]root@sionko:/# ifconfig wlan0 down
root@sionko:/# dhclient -r wlan0[/B]
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

**wifi0: unknown hardware address type 801**
**wifi0: unknown hardware address type 801**
Listening on LPF/wlan0/00:e0:00:87:5c:4e
Sending on   LPF/wlan0/00:e0:00:87:5c:4e
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
**root@sionko:/# wpa_supplicant -w -D hostap -i wlan0 -c /etc/wpa_supplicant.conf -dd**
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'hostap' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     6d 69 63 72 6f                                    micro           
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='micro'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Added alternative ifindex 3 (**wifi0**) for wireless events
WEXT: Operstate: linkmode=1, operstate=5
Added alternative ifindex 3 (**wifi0**) for wireless events
Own MAC address: 00:e0:00:87:5c:4e
wpa_driver_hostap_set_wpa: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Driver does not support WPA.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 502 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 859 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:19:e3:e3:7f:df ssid='Kristines lejlighed' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:e3:e3:7f:df ssid='Kristines lejlighed' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 859 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:19:e3:e3:7f:df ssid='Kristines lejlighed' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1c:0f:4f:a7:b0 ssid='KBH Skolernes UNDERVISNING' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:19:e3:e3:7f:df ssid='Kristines lejlighed' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 680 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 680 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
1: 00:19:5b:b3:c8:b9 ssid='PeterAnne' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1c:f0:9c:f2:1a ssid='default' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:1d:7e:4c:55:0b ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
**root@sionko:/# ifconfig wlan0 up**
**root@sionko:/# iwconfig wlan0 mode Managed**
**root@sionko:/# dhclient  wlan0**
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

**wifi0**: unknown hardware address type 801
**wifi0**: unknown hardware address type 801
Listening on LPF/wlan0/00:e0:00:87:5c:4e
Sending on   LPF/wlan0/00:e0:00:87:5c:4e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
**root@sionko:/# ping 64.233.161.44**
PING 64.233.161.44 (64.233.161.44) 56(84) bytes of data.
From 169.254.4.232 icmp_seq=1 Destination Host Unreachable
From 169.254.4.232 icmp_seq=2 Destination Host Unreachable
From 169.254.4.232 icmp_seq=3 Destination Host Unreachable

--- 64.233.161.44 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms
, pipe 3


Why are there still references to wifi0?
f
> **chili555 said:**
> Also, may I please see:```
lsmod | grep prism
```

Sure, but there is no output:

```
root@sionko:/# lsmod | grep prism
root@sionko:/# 
root@sionko:/# lsmod  #So instead:
Module                  Size  Used by
8139too                27520  0 
ipv6                  267780  8 
radeon                124192  2 
drm                    82580  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
bay                     6912  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  1 bay
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
af_packet              23812  8 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
irda                  203068  0 
crc_ccitt               3072  1 irda
evdev                  13056  6 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
psmouse                40336  0 
hostap_pci             56848  2 
hostap                110724  1 hostap_pci
ieee80211_crypt         7040  1 hostap
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
ac                      6916  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
pcspkr                  4224  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
intel_agp              25492  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  2 
libata                159344  3 pata_acpi,ata_generic,ata_piix
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
uhci_hcd               27024  0 
usbcore               146028  2 uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
root@sionko:/#
```

which together with:
> **chili555 said:**
> the prism2 drivers should not be loaded.

Is a good or a bad thing?

> **chili555 said:**
> I wonder why you proceeded with wifi0, since you know it doesn't work and wlan0 does.

I don't know either. Maybe I do as I am told by manuals a bit too much at times?

Thanks again!

EDIT: So I guess the question is how I disable that prism2 driver, if that is what's needed. Some quick Googling has not told me much.
EDIT II: I will be gone untill Monday, but would of course appreciate some help and I will do what may suggest on Monday.

---

### Post by chili555 on 2008-06-12
If you did *lsmod | grep prism* (meaning, roughly 'list all the modules that are currently loaded but just list any with 'prism' anywhere in the name') and it returned nothing, that means there is nothing to report, that there is no module loaded with 'prism' in the name. It saves both of us from having to sift through a lengthy list like the one you provided. Let the computer do the work!

Since no prism modules are loading, we may turn our efforts elsewhere. I am very interested in this:> Try to find WPA-enabled AP
0: 00:17:9a:9f:67:cc ssid='micro' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
skip - no WPA/RSN IEThis suggests to me, although I am no expert on WPA, that your wpa_supplicant.conf file specifies the WPA details to match to join your network at the router. It suggests to me the router and wpa_supplicant.conf file are not in agreement about the WPA specifications.

I'd revisit the .conf file and the administration pages of the router and try to refine the .conf file.

Is your router broadcasting the ESSID?

May I please see:```
sudo iwlist wlan0 scan
```

---

