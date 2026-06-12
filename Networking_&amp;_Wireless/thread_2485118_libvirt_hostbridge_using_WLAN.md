---
title: "libvirt hostbridge using WLAN"
date: 2023-03-20
forum: Networking &amp; Wireless
---

### Post by randy-1 on 2023-03-20
Hi,
my search for "br0 bridge wifi wlan enslaved" is unsuccessful. 
I got a br0 host-bridge with eth0-device enslaved for my libvirt-VMs on Ubuntu 22.04 with kernel "Linux version 5.15.0-25-generic" brought up by  systemd-networkd.service, everything works perfectly. 
Now I want to get rid of network-cable using a WiFi-bridge with enslaved wlan0.
Found some informaion here:

[https://major.io/2015/03/26/creating-a-bridge-for-virtual-machines-using-systemd-networkd/](https://major.io/2015/03/26/creating-a-bridge-for-virtual-machines-using-systemd-networkd/)

[https://github.com/systemd/systemd/issues/936](https://github.com/systemd/systemd/issues/936) 

So I managed to set TP-Link WiFi-USB-Stick (Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter) to 4addr-mode via  /usr/sbin/iw dev wlan0 set 4addr on

using new "wlan-set-4addr-on.service":
```
[Unit]
Description=WiFi-Stick-4addr
Wants=network.target
Before=network.target systemd-networkd.service

[Service]
Type=oneshot
ExecStart=/usr/sbin/iw dev wlan0 set 4addr on
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

Files in /etc/systemd/network/ are as follows:

10-wlan0.link renames WiFi-device to wlan0
```
[Match]
MACAddress=f4:f2:6d:0c:5e:61
[Link]
Description=WiFi
Name=wlan0

```

45-wlan0.network
```
 [Match]
Name=wlan0
[Network]
Bridge=br0

``` 

br0.netdev
```
 [NetDev]
Name=br0
Kind=bridge

```

br0.network
```
 [Match]
Name=br0

[Network]
DNS=194.25.0.125
Address=192.168.178.112/24
Gateway=192.168.178.1

```

Bringing up the bridge by "systemctl start systemd-networkd.service" looks promissing at first sight 

route -n
```
 Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 br0
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 br0

```

ifconfig br0
```
 br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.178.112  netmask 255.255.255.0  broadcast 192.168.178.255
        inet6 2a02:8108:3dc0:13b8::4  prefixlen 128  scopeid 0x0<global>
        inet6 fe80::900f:ffff:fe3a:7c65  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:8108:3dc0:13b8:900f:ffff:fe3a:7c65  prefixlen 64  scopeid 0x0<global>
        ether 92:0f:ff:3a:7c:65  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

networkctl
```
 IDX LINK   TYPE     OPERATIONAL      SETUP     
  1 lo     loopback carrier          unmanaged
  2 enp2s0 ether    off              configured
  3 wlan0  wlan     enslaved         configured
  4 br0    bridge   carrier          configured

4 links listed.
```

I can successfully ping br0-device 192.168.178.112, but gateway 192.168.178.1 can't be reached . . .

systemctl status wlan-set-4addr-on.service
```
&#9679; wlan-set-4addr-on.service - WiFi-Stick-4addr
     Loaded: loaded (/etc/systemd/system/wlan-set-4addr-on.service; enabled; vendor preset: enabled)
     Active: active (exited) since Mon 2023-03-20 18:00:29 CET; 1h 40min ago
    Process: 749 ExecStart=/usr/sbin/iw dev wlan0 set 4addr on (code=exited, status=0/SUCCESS)
   Main PID: 749 (code=exited, status=0/SUCCESS)
        CPU: 2ms

Mär 20 18:00:28 Kubuntu-22-04-for-KVMs systemd[1]: Starting WiFi-Stick-4addr...
Mär 20 18:00:29 Kubuntu-22-04-for-KVMs systemd[1]: Finished WiFi-Stick-4addr.

```

systemctl status wpa_supplicant-at-wlan0.service
```
&#9679; wpa_supplicant@wlan0.service - WPA supplicant for wlan0
     Loaded: loaded (/etc/systemd/system/wpa_supplicant@wlan0.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-03-20 18:16:23 CET; 1h 28min ago
   Main PID: 3385 (wpa_supplicant)
      Tasks: 1 (limit: 9476)
     Memory: 1.8M
        CPU: 981ms
     CGroup: /system.slice/system-wpa_supplicant.slice/wpa_supplicant@wlan0.service
             &#9492;&#9472;3385 /sbin/wpa_supplicant -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf

Mär 20 18:16:23 Kubuntu-22-04-for-KVMs systemd[1]: Started WPA supplicant for wlan0.
Mär 20 18:16:23 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: Successfully initialized wpa_supplicant
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: SME: Trying to authenticate with a4:2b:b0:dd:0a:7e (SSID='Maniswlan' freq=2437 MHz)
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: Trying to associate with a4:2b:b0:dd:0a:7e (SSID='Maniswlan' freq=2437 MHz)
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: Associated with a4:2b:b0:dd:0a:7e
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: WPA: Key negotiation completed with a4:2b:b0:dd:0a:7e [PTK=CCMP GTK=CCMP]
Mär 20 18:16:25 Kubuntu-22-04-for-KVMs wpa_supplicant[3385]: wlan0: CTRL-EVENT-CONNECTED - Connection to a4:2b:b0:dd:0a:7e completed [id=0 id_str=]

```

systemctl status systemd-networkd.service
```
 &#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-03-20 18:16:28 CET; 1h 41min ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
   Main PID: 3391 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 9476)
     Memory: 1.4M
        CPU: 376ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;3391 /lib/systemd/systemd-networkd

Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: br0: Gained IPv6LL
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: wlan0: Gained IPv6LL
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: Enumeration completed
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd[1]: Started Network Configuration.
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: br0: netdev exists, using existing without changing its parameters
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: wlan0: Connected WiFi access point: Maniswlan (a4:2b:b0:dd:0a:7e)
Mär 20 18:16:28 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: wlan0: found matching network '/etc/systemd/network/45-wlan0.network', based on potentially unpredictable interface name.
Mär 20 18:16:30 Kubuntu-22-04-for-KVMs systemd-networkd[3391]: br0: DHCPv6 address 2a02:8108:3dc0:13b8::4/128 (valid for 1d, preferred for 1d)
``` 

What's going wrong?

---

### Post by TheFu on 2023-03-20
IDK, but not all wifi adapters support the necessary network features required to support bridging.  That's my first guest for why it doesn't work.

BTW, servers should be ethernet connected, not wifi. There are many, many, many, reasons for this.

But only you know your requirements and stubbornness level.

---

### Post by randy-1 on 2023-03-21
```
IDK, but not all wifi adapters support the necessary network features required to support bridging. That's my first guest for why it doesn't work.
``` 
May be You are right. Trying to set up another TP-Link WiFi-Stick(TU4, user-compiled driver) for 4addr, I get an error-message . . .
With used one(kernel-driver) there is no . . .

```
        BTW, servers should be ethernet connected, not wifi. There are many, many, many, reasons for this.

        But only you know your requirements and stubbornness level. 

```
You are right. 
Ethernet bridge is working perfectly, so this project is "just for fun" and to know . . .
Just for playing around, I tested "Proxmox VE"-software, which uses Debian11 with NetworkManager.Service.
As I cannot set my router to "bridge-mode", one has to "masquerade" packages from VMs. This way they aren't discarded by the router and setup works . . .
BUT:
How to do this "masquerading" with systemd-networkd.service ?

---

### Post by TheFu on 2023-03-21
I use netplan files for setting up KVM bridges.  Don't know that lesser tools can do it.  Also, the bridge-utils package must be installed.
There are lots of example netplan files in these forums and on netplan.io where the documentation is for that tool.

If you use a bridge, no masquerading is used.

---

### Post by randy-1 on 2023-03-21
> If you use a bridge, no masquerading is used.
Using WiFi-bridge to router things are complicated . . .
i.e. read section 3.2 on this site(using NetworkManager.service): 

[https://ostechnix.com/install-proxmox-ve-on-debian-in-intel-nuc/](https://ostechnix.com/install-proxmox-ve-on-debian-in-intel-nuc/) 

In /etc/network/interfaces one has to add theses lines:
> post-up   echo 1 > /proc/sys/net/ipv4/ip_forward
post-up   iptables -t nat -A POSTROUTING -s '192.168.1.0/24' -o wlo1 -j MASQUERADE
post-down iptables -t nat -D POSTROUTING -s '192.168.1.0/24' -o wlo1 -j MASQUERADE 

What now for systemd-networkd.service ?

---

### Post by TheFu on 2023-03-21
/etc/network/interfaces  is deprecated and hasn't been used in over 3 yrs for Ubuntu systems.  Use netplan, as stated above. DDG-search for "netplan kvm bridge" to find examples.  
Or ... [https://netplan.io/examples](https://netplan.io/examples)

---

