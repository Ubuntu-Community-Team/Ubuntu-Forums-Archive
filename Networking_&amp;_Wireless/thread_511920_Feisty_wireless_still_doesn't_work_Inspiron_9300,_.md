---
title: "Feisty wireless still doesn't work: Inspiron 9300, ipw2200"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by HippoMan on 2007-07-28
I am trying a wireless connection for the first time under my **Kubuntu/Feisty** system which is running on a **Dell Inspiron 9300** laptop. I've had my entire Kubuntu system working fine without wireless ever since Dapper, but I recently have wanted to try to connect to my wireless router, to no avail.

I am able to connect without any problem to my wireless router from my MacBook pro and from a Windows system, and so I know that the router is working.

Also, the Windows system is actually running on my same **Inspiron 9300** in dual-boot mode, and so I know that my wireless card is enabled, configured properly, and working.

My network is managed via **ipw2200**, and I want to connect via **WAP-PSK**, which works fine via the MacBook and Windows systems.

I have followed the instructions in all of these places, but none of them have worked for me:
```
http://ubuntuforums.org/showthread.php?t=263136
http://ubuntuforums.org/showthread.php?t=460929
http://ubuntuforums.org/showthread.php?t=430925
http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html

```I have **wpa-supplicant** installed, and its config file looks like this (psk not shown, of course):
```
# cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="WiFi Home"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk=..................................
}
```I also have this:
```
# cat /etc/network/interfaces
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dipw -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```After setting this up, I run **/etc/init.d/networking restart**, but it doesn't bring up the wireless network.  I know this to be true because after the restart, I do this, which doesn't show **eth1**:
```
# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```If I manually run the **wpa_supplicant** command, I get this:
```
# wpa_supplicant -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=11):
     58 79 7a 7a 79 20 50 6c 75 67 68                  WiFi Home
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='WiFi Home'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
zsh: segmentation fault (core dumped)  wpa_supplicant -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd
```Note the **ioctl** errors.  I'm sure that this is at least part of my problem.  However, I don't know how to fix these errors.

Can anyone shed any light on this problem?

Thank you very much in advance.
[RIGHT] .[/RIGHT]

---

### Post by erfahren on 2007-07-28
this is the one that worked for me, it basically just sets up everything in /etc/network/interfaces
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

do the part where it says: "VERY IMPORTANT:
Now convert your WPA ASCII password using the following command (' ' single quotes required):" just like it says to. That tripped me up the first time, just being an idiot!

gl

EDIT:
just for information; my card is a Atheros AR5005G 802.11abg

my network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.3
gateway 192.168.0.1
dns-nameservers 205.171.3.65
netmask 255.255.255.0
wpa-driver madwifi
wpa-ssid <myssid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mypsk>

```

One other thing; I think I still had to go into System>Adminisration>Network and set both of my DNS servers.

good luck

---

### Post by HippoMan on 2007-07-28
Thanks, **erfahren**, but sadly, that still doesn't work for me.  I followed the steps in the instructions that you pointed me to, but when I get to the networking restart step, this happens:
```
# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```
For some reason, my system isn't seeing **eth1**, apparently.

???

---

### Post by noob12 on 2007-07-28
We need to get the interface working first.  Let's start by checking your hardware and seeing which driver if any
is associated to the device.  Please post the output of:
```

lshw -C network

```

---

### Post by erfahren on 2007-07-28
along with what noob12 said, I think it's important that you undo the previous configuration you did with wpa_supplicant (which you may have already done). but; just for information, the /etc/wpa_supplicant.conf file probably should be renamed although I'm sure that alone won't solve your problem. 

Anyway, I googled the "There is already a pid file" error that you're getting and came up with [url=http://ubuntuforums.org/showthread.php?p=3071343[/url] and bsfah3 (post #13) mentions removing the avahi-daemon. From what the Synaptic description says it has to do with networking. I'm not running a home network and although that's installed it's not in my running processes. (As you can tell I just try to figure this stuff out as I go along!)

---

### Post by HippoMan on 2007-07-29
Thanks to both of you.

In response to noob12, here's the output of the command:
```
# lshw -C network
  *-network:0 DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:71:d2:b6
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=64 link=no multicast=yes port=twisted pair
       resources: iomemory:dcffc000-dcffdfff irq:19
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:dcffe000-dcffffff irq:10
```In reply to erfahren, I have now renamed **/etc/wpa_supplicant.conf**, and I've uninstalled **avahi-daemon**.  This didn't get rid of the pid file message, but I don't think that it's really a problem.  Nothing else seems to have changed:
```
# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```I'm wondering whether I've been on the wrong track with **ipw2200**.  I can see now that my network card is a Broadcom device, which, I believe, isn't the same as i**pw2200**, correct?  If so, I don't recall how I started thinking **ipw2200 **in the first place.

But anyway, does any of this new information help?

Thanks again to all.

---

### Post by HippoMan on 2007-07-29
Well, since posting the last message, I made some good progress, but things are still not quite working for me.

Realizing that I should be using **bcm43xx** instead of **ipw2200**, I found a lot of documentation.  I got rid of the **ipw2200** module and then followed the instructions in the documentation and installed the **bcm43xx-fwcutter** package.  After doing the rest of that setup, I ended up with the following situation:
```
# lsmod | egrep bcm
bcm43xx               126824  0
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac

# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid WiFi Home
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk ........................................................................

# /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 7829
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   LPF/eth1/00:0b:7d:1e:0d:b1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0B:7D:1E:0D:B1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:10 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4883 (4.7 KiB)  TX bytes:588 (588.0 b)
          Interrupt:10 Base address:0x8000

eth1:avah Link encap:Ethernet  HWaddr 00:0B:7D:1E:0D:B1
          inet addr:169.254.5.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```This is much better than before, because I can now see the **eth1** interface and my machine's WiFi light is now turned on.  However, my WPA connection is not getting properly made.
[FONT=monospace]
I don't understand why I have the 169.254.5.9 connection, but that seems to occur if there is a network problem, such as when I'm using a wired network and the cable is unplugged.  Therefore, I don't think that the 169.254.5.9 entry is an issue.

[/FONT] I know my router is working because my MacBook Pro is properly connected with the same WPA credentials.  Also, since my Linux machine is set up to dual-boot into Windows, I re-tested the ability for this machine to connect via that OS, and the wireless connection indeed gets properly made.  So I know that my wireless card is working.

Back in Linux, I get the above results even after rebooting.

Thanks again for any further help.

---

### Post by noob12 on 2007-07-29
So it was a good thing to check the chipset because it wasn't the Intel 2200 at all.

I'd recommend trying this HOWTO on the forum for Broadcom 43xx cards:  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990).  Several people are reporting success with that.  If that doesn't work for you, you should try the Windows driver and ndiswrapper.

If you're following your own path, I'd try to first verify the device level stuff is right and that **iwconfig eth1** and **iwlist eth1 scan** shows what you expect  before moving on to the rest.  Also if you control the wireless access point, you might want to disable the security and try connecting unsecured first, then adding the security back.  Helps to separate problems.

---

### Post by HippoMan on 2007-07-29
Yes, I already followed the instructions in that thread, both for the native and the **ndiswrapper** versions, and in each case, I get the same results: **eth1** is now visible, the WiFi light is on, but my WPA connection keeps failing.

I guess I'll have to disable security and test it that way.

I'll post whatever results I get after further investigation, be they a success or a failure.

Thanks again for all your help.

---

### Post by HippoMan on 2007-07-29
It turns out that I needed to use **ndiswrapper**/**bcm43xx** along with **wpasupplicant**.  When I put the WPA parameters directly into **/etc/network/interfaces**, it didn't work.  The corresponding parameters in **/etc/wpa_supplicant.conf **did the trick.

Thanks again for all the help.

---

