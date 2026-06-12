---
title: "Native Bridge in Networkmanager"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by p-tk-l on 2014-05-29
Hi,
I want to create a bridge in NetworkManager.
Add > [Virtual] Bridge > Add interface eth0 -> Save (I set the IP manually address)
Restart NetworkManager and nothing. 
```
ipconfig

bridge0   Link encap:Ethernet  HWaddr 6e:f1:44:41:9e:22  
          inet6 addr: fe80::6cf1:44ff:fe41:9e22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:10098 (10.0 KB)

eth0      Link encap:Ethernet  HWaddr 78:45:c4:3f:53:9c  
          inet6 addr: fe80::7a45:c4ff:fe3f:539c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197742 (197.7 KB)  TX bytes:4733 (4.7 KB)
```
Interface bridge0 not ip address. 
I do according to this guide [http://avi.alkalay.net/2014/01/fedora-20-virtualization-networkmanager-native-bridge.html](http://avi.alkalay.net/2014/01/fedora-20-virtualization-networkmanager-native-bridge.html)

---

### Post by lambdafox on 2014-06-04
I am a linux newbie also trying to set up a network bridge.  Following all of the links from the link you provided, it appears that this is not possible until possibly Network, manager 0.9.9 which is not yet available for Ubuntu.  Anyone feel free to correct me is that is wrong.

I have:
 kernel:  3.13.0-27-generic
network manager:  0.9.8.8-0ubuntu7
libnl3:  libnl-3-200 v 3.2.21-1

Here is how I have proceeded:

I use dhcp to get my pc's ip address.

```
sudo gedit /etc/network/interfaces
```

replace everything with:

    ```
#tell network manager to leave eth0 alone
iface eth0 inet manual

# enable loopback interface
#auto lo
#iface lo inet loopback

# start bridge on boot
auto br0

#bridge settings

iface br0 inet dhcp
    bridge_ports eth0
    bridge_waitport 0    # no delay before a port becomes available
    bridge_fd 0        # no forwarding delay
```

```
sudo gedit /etc/sysctl.conf
```

append this:

```
# Disable netfilter disabled on all bridges
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0
```

WARNING, you will loose your connection at this step:

Run nm-connection and delete all devices there.

Reboot.

nm-applet in system tray says network is not connected, but it is wrong.  try accessing a web page.

This is a work in progress...

---

