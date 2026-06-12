---
title: "Wireless network interface down, fresh install Ubuntu Server 14.04"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by Isaac_Graham on 2014-06-09
Hi, I'm relatively inexperienced with the linux command-line. Just installed Ubuntu Server and have been unable to use my wlan0 interface. I have done no configuration since installing it. The wireless interface worked fine during the installation process.

**Model**
```
Dell Latitude E6400
```
[B]System
[/B]```
Ubuntu 14.04 LTS
3.13.0-24-generic x86_64
```
**lspci**
```
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
```
[B]iwconfig
[/B]```
wlan0
IEEE 802.11abgn  ESSID:off/any
Mode:Managed  Access Point: Not-Associated  Tx-Power=0 dBm
Retry  long limit:7  RTS thr:off    Fragment thr:off
Power Management:off
```
[B]lshw
[/B]```
*-network DISABLED
description: Wireless Interface
product: Ultimate N WiFi Link 5300
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wlan0
version: 00
serial: 00:21:6a:66:cc:02
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
resources: ird:48 memory:f69fe000-f69fffff
```
[B]iwlist scan
[/B]```
Failed to read scan data : Network is down
```
[B]service networking restart
[/B]```
stop: Job failed while stopping
start: Job is already running: networking
```

---

### Post by Ian_Cosgrove on 2014-06-22
Just installed Ubuntu Server 14.04 and was having the exact same problems, very frustrating that the server installer doesn't configure this automatically, at least the install sees your wireless device and driver though that's a good sign.

I ran lshw -C network and it listed my wlan as *-network DISABLED

Turns out the problem was I just needed to manually specify the wireless connections details in /etc/network/interfaces

sudo nano /etc/network/interfaces

At first this only contained
auto lo
iface lo inet loopback

Beneath this I added

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8
wpa-ssid <routers ssid>
wpa-psk <routers key>

Obviously replacing <routers ssid> and <key> withe the name and password of your own router

This assumes a fairly standard setup, configure your wireless interface with a static ip address of 192.168.1.100, routers ip is 192.168.1.1, use it as the default dns server or fallback to Googles 8.8.8.8

You probably know all those settings already or can get them from your routers admin page. Now save and close the file

Restart the interface:
sudo ifdown wlan0 && sudo ifup wlan0

Run ifconfig to confirm settings worked
Confirm you can ping the router
ping -c3 192.168.1.1
Confirm you can reach the internet
ping -c3 google.com

If all is ok do your happy dance and sudo apt-get update

Sorry for not using code boxes but I'm typing this on my phone and assume you can't copy&paste anyway

---

### Post by Isaac_Graham on 2014-06-22
I'm certain there's something wrong with mine that has nothing to do with the network interface file. I've tried configuring those settings the same way, and it wasn't working. I've got it plugged in via ethernet now, and that works just fine. I'd still prefer if it worked wirelessly though.

---

