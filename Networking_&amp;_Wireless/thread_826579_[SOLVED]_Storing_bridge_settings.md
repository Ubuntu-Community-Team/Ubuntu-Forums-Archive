---
title: "[SOLVED] Storing bridge settings"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by mwjones on 2008-06-12
I have Kubuntu 8.04 running on my desktop, along with [VirtualBox]("http://www.virtualbox.org/").  Following the [Community Ubuntu Documentation]("https://help.ubuntu.com/community/VirtualBox") works fine when I enter the following commands manually: 
```
sudo tunctl -t tap1 -u mwjones
sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun

sudo brctl addbr br0 
sudo ifconfig eth0 0.0.0.0 promisc 
sudo brctl addif br0 eth0
sudo dhclient br0 

sudo brctl addif br0 tap1 
sudo ifconfig tap1 up
```

However, when I put those commands into an executable script **/etc/init.d/bridge** and **update-rc.d bridge multiuser 98**, my bridge *br0* and interface *eth0* end up with the same IP address and no packets will route out to the rest of the network.  When those commands are entered manually, *br0* gets the address and *eth0* has no address -- the packets flow just fine.  

What is the difference and how is it corrected?

Cheers,
mwjones

PS: On the script version, I've waited for the bridge's state changes (forwarding and learning) with still the same behavior occurring of no traffic flow.

---

### Post by mwjones on 2008-06-12
I've got it working.  First the init.d script and links were removed:```
rm -v /etc/init.d/bridge /etc/rc*/*bridge
```

Then the configuration settings were tweaked and moved to **/etc/network/interfaces**```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 0.0.0.0

auto br0
iface br0 inet dhcp
  pre-up tunctl -t tap1 -u mwjones
  pre-up chown root.vboxusers /dev/net/tun
  pre-up chmod g+rw /dev/net/tun
  pre-up ifconfig eth0 down
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth0
  pre-up brctl addif br0 tap1
  pre-up ifconfig eth0 0.0.0.0 promisc up
  pre-up ifconfig tap1 up
  post-down ifconfig eth0 down
  post-down ifconfig tap1 down
  post-down ifconfig br0 down
  post-down brctl delif br0 eth0
  post-down brctl delif br0 tap1
  post-down brctl delbr br0
```

I used the [NetworkMonitoringBridge]("https://help.ubuntu.com/community/NetworkMonitoringBridge") document.

---

