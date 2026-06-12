---
title: "Wireless not working unless boot to older kernel"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by inselaffe on 2008-05-13
I've been in a different office today and have spend a silly amount of time trying to connect to the wireless network with no success. After entering the WEP key when prompted, the network manager shows the spinny icon but the balls remain grey; eventually it prompts again for a key.

Finally out of pure desperation I booted the laptop into Windows XP (for the first time in over a month). Windows connected to the network without a problem. It turns out there's nothing strange about this particular network at all; it is Ubuntu that is playing silly beggars.

I have experimented a bit, and have found that I can connect to no available wireless network whilst running a 2.6.24-* kernel. Using 2.6.22-14-generic (or Windows!) on the same machine I can. This is an Intel iwl3945.

A recent package update must have introduced this incompatibility. What can be done to fix this?

---

### Post by dmizer on 2008-05-13
how or what did you do to make the card work in the first place?  did you compile ndiswrapper from source?

from your non-working kernel, post the output of:
```
lshw -C network
```

---

### Post by inselaffe on 2008-05-14
> **dmizer said:**
> how or what did you do to make the card work in the first place?  did you compile ndiswrapper from source?


I did nothing at all to make it work. Hardy as Feisty and Gutsy before provide a driver. And it has worked until recently on at least some of the other kernels with which it now doesn't..

I'll run that command for you first chance I get.

---

### Post by inselaffe on 2008-05-14
Here's the output of that command while booted with the non-working kernel:

```
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:67:af:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:0e:7b:b2:27:e6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

```And with a working one:

```
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:67:af:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 [COLOR=Red]driverversion=1.2.2mp.ubuntu1 [/COLOR]firmware=14.2 1:0 () ip=192.168.0.2 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:0e:7b:b2:27:e6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
```The difference seems to be the driverversion not being present. In the non working kernel, I still see the available wireless networks, it just fails to connect to them. In fact, I was even able to scan with kismet and grab enough with airodump to crack a 64 k wep key, so the card is working to some extent.

---

### Post by dmizer on 2008-05-14
try disabling network manager according to these directions: [https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5)
(you only need to perform the two steps under "disabling networkmanager")

then see if you can configure your card via sysem > administration > networking

---

### Post by chili555 on 2008-05-14
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Please let us know.

---

### Post by inselaffe on 2008-05-15
> **chili555 said:**
> There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Please let us know.

I got somewhere with this. After installing that package, I could connect to wireless in 2.6.24-16-generic. However, performance over the network was awful - a simple page like the Firefox/Google start page took minutes to load, and then without most pf the images on the page. Booting into 2.6.22-14, normal service is resumed.

I did note that iwconfig consistently shows about 50% more signal noise when in the newer kernel than the old - but as an environmental factor I'm surprised this is different depending on kernel/driver version.

I also tried removing the package. After doing so i can still connect with the newer kernel, but with the same poor performance.

---

### Post by chili555 on 2008-05-15
May we please see:```
iwconfig
lsmod | grep iwl
```Thanks.

---

### Post by Andre-D on 2008-05-15
Same problem (?)

I assume I have the very same problem.

> WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:de:59:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g




I cannot conect to my job's network, nor to it's guest network.
It seems I can't get IP address, and it attempts to fallback to 192.168.1.x (that only works on my home network - and might be the reason I can use it at home)

It DID work before. - so I assume a new kernel is the reason to this bug.

I also attach the syslog, that displays unsuccessful attempts to connect to both job-networks.  Strange thing's is going on there.

Connection at home works, but I think it's only luck, as Ubuntu seems to try my last home-DHCP address everywhere, and it works here.., and only here.

>  lsmod | grep iwl
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211


I hope somebody looks into this bug.

---

### Post by chili555 on 2008-05-15
That looks like a Network Manager issue, not iwl3945. If you turn off Roaming and do:```
sudo iwconfig wlan0 essid <ur_job_essid>
sudo dhclient wlan0
```Does it connect?

---

### Post by Andre-D on 2008-05-16
I did not disable roaming mode, - but ensured that no connection was made.

(Using GUI - disabling roaming mode means I need to select an SSID and encryption, but I am testing with an open guest-network.)

So, without any activity in network manager:
this is the result:
> andre@Ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6862
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:de:59:ac
Sending on   LPF/wlan0/00:18:de:de:59:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I must add that DHCP is working perfectly for eth0 interface. (wired)

---

### Post by inselaffe on 2008-05-16
> **chili555 said:**
> May we please see:```
iwconfig
lsmod | grep iwl
```Thanks.

```
$ lsmod | grep iwl
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945

```

---

### Post by dmizer on 2008-05-16
> **Andre-D said:**
> (Using GUI - disabling roaming mode means I need to select an SSID and encryption, but I am testing with an open guest-network.)

disabling romaing mode does not force you to enter encryption.  all wireless access points have an ssid.  just enter the ssid and hit click ok.

---

### Post by Andre-D on 2008-05-16
> **dmizer said:**
> disabling romaing mode does not force you to enter encryption.  all wireless access points have an ssid.  just enter the ssid and hit click ok.

Sure- what I did wrong, was that I needed to select ip-configuration in order to be able to click "OK"

Disabled now, but still the same problem:

> andre@Ubuntu:~$ sudo iwconfig wlan0 essid tkgjest
[sudo] password for andre: 
andre@Ubuntu:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 7079
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:de:59:ac
Sending on   LPF/wlan0/00:18:de:de:59:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
andre@Ubuntu:~$ 


(This is an clean installed & patched up Ubuntu 8.04 - I did NOT fool around with other drivers or NDIS drivers.)

Nor did I mess with the internal firewall (did not even look at it)

thanks for helping - hope you can find a solution

---

### Post by dmizer on 2008-05-16
> **inselaffe said:**
> ```
$ lsmod | grep iwl
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945

```

take a look here for the complete directions on how to get your card working: [http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

---

### Post by dmizer on 2008-05-16
> **Andre-D said:**
> Sure- what I did wrong, was that I needed to select ip-configuration in order to be able to click "OK"

Disabled now, but still the same problem:

[snip]

(This is an clean installed & patched up Ubuntu 8.04 - I did NOT fool around with other drivers or NDIS drivers.)

Nor did I mess with the internal firewall (did not even look at it)

thanks for helping - hope you can find a solution

try just disabling network manager as suggested in post 5.  if that doesn't work for you, you should start a new thread.

---

### Post by Andre-D on 2008-05-19
> **dmizer said:**
> try just disabling network manager as suggested in post 5.  if that doesn't work for you, you should start a new thread.


I did, (thread 4992251)  - disabling network amanger did not change anything.

---

### Post by Andre-D on 2008-05-19
-

---

### Post by inselaffe on 2008-05-20
> **dmizer said:**
> take a look here for the complete directions on how to get your card working: [http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)
Seems a bit drastic but I'll give a go later.

---

### Post by Andre-D on 2008-05-20
Please disregard my messages in this thread.
both guest and employee networs at my job have huge problems...

---

