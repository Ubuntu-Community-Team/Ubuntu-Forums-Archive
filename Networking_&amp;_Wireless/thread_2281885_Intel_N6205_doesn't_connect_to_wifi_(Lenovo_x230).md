---
title: "Intel N6205 doesn't connect to wifi (Lenovo x230)"
date: 2015-06-10
forum: Networking &amp; Wireless
---

### Post by Klaster on 2015-06-10
Hey folks,

I have troubles with the wifi connection on my x230. Right now, I'm not able to connect to any network. Even though I see them through the network manager, it doesn't connect and re-prompts the password input after some time.
I've had issues with that for a few month now, sometimes the computer connects but the speed is wretched.

I think my iwlwifi-driver is up to date (according to [this]("https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi")). Here is some output:
```
lshw -C network
```
```
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a4:4e:31:b5:39:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-40-generic firmware=18.168.6.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f1c00000-f1c01fff

```

I've obviously checked existing threads and encountered same xp in my college's network as described [here]("http://ubuntuforums.org/showthread.php?t=2056108&highlight=x230+wifi"), but that's not the issue right now (sitting at my parent's).
On an earlier attempt to increase my speed, I think I disabled 802.11n. Didn't help though.
```
**sudo grep 11n -r /etc**

/etc/modprobe.d/iwlwifi.conf:options iwlwifi 11n_disable=1

```

Please note, that I'm still running 12.04 LTS. Do you think an upgrade could help? I'm currently writing my thesis and would rather not update until I'm done.

Anyone knowing about this issue? I'm happy to provide more information in case it's needed. Don't know what else you might need though...

Thanks in advance!
Jakob

---

### Post by fsando on 2015-06-18
I'm having the exact same problem with my x230, both with 14.04 and 15.04.

For 14.04 I'm trying with kernel 3.16 and 3.13 - no dice. (Same card on w520 with kernel 3.13 works fine). I'm right now comparing the two machines but as I don't know what I'm looking for, and I don't have that much time to put into it, it's mostly just poking around for the moment.

It has worked briefly a couple of times for a short while but doesn't anymore.

The interesting part is that the card connects to the router, gets an ip, the router knows about the machine (it's listed on the router with its ip-address), and on the machine it's listed as connected. It just doesn't get any internet. I have a feeling that it doesn't get the dns right - somehow.


```

$ nmcli dev status
DEVICE     TYPE              STATE        
wlan0      802-11-wireless   connected

$ nmcli con status
NAME                      UUID                                   DEVICES    DEFAULT  VPN   MASTER-PATH                                 
ZyXEL_XXXX                xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   wlan0      yes      no    --                                          

$ ifconfig
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:398775 (398.7 KB)  TX bytes:63769 (63.7 KB)

```

EDIT:

Just discovered the following: If I delete and recreate a wifi account it works perfectly for a short while. SO, apparently something gets initialized correctly when a new account is created but is subsequently not correctly updated or reinitialized.

This would, to me, indicate that it is a software issue, a question of finding the right drivers.

EDIT 2:

It may be related to network-manager (and dnsmasq, dnsmasq is built into network-manager) and show itself as dns-servers not setup correctly as seen here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1048430](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1048430)

The gist of it is illustrated by these lines:

```

grep -i error /var/log/syslog

Oct 24 03:15:29 p5q3 NetworkManager[1064]: <error> [1414109729.384414] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct 24 16:26:52 p5q3 NetworkManager[1040]: <error> [1414157212.476590] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name

```

I see the same type of error on my x230, while my w520 with the exact same system and kernel does not show them.

---

