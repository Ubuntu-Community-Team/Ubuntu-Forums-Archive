---
title: "enp2s0 not recognised by router config"
date: 2016-01-25
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2016-01-25
I have my router configured to assign a specific IP address to my Linux PC based on its MAC address. However, the PC picks up a different one (there is only one NIC, no WiFi).
I'm wondering if this (new problem) is anything to do with the fact my network connection is no longer called eth0 but enp2s0 ?

Has anyone else had issues assigning static addresses to this interface or am I on the wrong track? FWIW I removed and remade the static IP lease in the router but it didn't help.
I did try renaming the interface back to eth0 with [this](https://forum.manjaro.org/index.php?topic=8778.0) tip but after reboot it's still got the same name.

I edited the network connection directly in Ubuntu to force the original LAN IP address and after rebooting the address stuck, but it's not my preferred way of doing things.
As an aside, the ifdown and ifup commands don't appear to work on enp2s0 - unrecognised interface.

---

### Post by chili555 on 2016-01-25
> am I on the wrong track?Correct!

Your router sees a MAC address and a request for an IP address; 192.168.x.y or some such. Assuming that MAC address is not filtered, and that it can auto-negotiate agreeable settings; speed, duplex, et al, it grants a lease. In your case, the router is set to grant a fixed IP address based on the MAC; sort of '11:22:33:aa:bb:cc = 192.168.1.25'.

> As an aside, the ifdown and ifup commands don't appear to work on enp2s0 - unrecognised interface. Correct. ifup/down are commands that bring interfaces declared in the file /etc/network/interfaces up and down. The usual desktop method uses Network Manager which doesn't use or need declarations there. Therefore, there is no enp2s0 in the file and ifup/down doesn't see anything to up or down.> I edited the network connection directly in Ubuntu to force the original LAN IP address and after rebooting the address stuck, but it's not my preferred way of doing things.Why? In one of my stay-at-home desktops, I simply removed Network Manager, declared my preferred static address settings in /etc/network/interfaces, rebooted and all is perfectly fine. I'm not going to drag my desktop to the coffee shop, work or school, so I don't need the flexibility NM gives us. 

My laptops use NM as I intend to drag at least one of them to Iceland!

Have you double- and triple-checked the MAC address you put in the router? Does it match, in every respect, what is here?```
ifconfig
```A slightly redacted example from my machine:```
enp0s25   Link encap:Ethernet  HWaddr [COLOR="#FF0000"]99:f7:28:ae:83:99 [/COLOR]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f0600000-f0620000 

```Does your router want to see 99:f7:28:ae:83:99 or 99:F7:28:AE:83:99 or 99f728ae8399? Have you double-checked?

---

### Post by pickarooney on 2016-01-25
The MAC address is definitely right.

in /etc/network/interfaces what exactly did you add?

I just have
[B]auto lo
iface lo inet loopback[/B]
currently

I suppose it's much of a muchness between using a hard-coded IP in Network Manager and assigning if from DHCP, it's just odd that the latter doesn't work any more.

---

### Post by chili555 on 2016-01-25
If you'd like to try the manual method:```
auto lo
iface lo inet loopback

auto enp2s0
iface enp2s0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```Of course, use the settings appropriate for your network. Restart the interface:```
sudo ifconfig enp2s0 down
sudo ifup -v enp2s0
```The -v for verbose should give some clues if something goes wrong.

I recommend that you select a static IP outside the range used by the DHCP server in the router. [http://geekness.eu/sites/default/files/linksys.JPG](http://geekness.eu/sites/default/files/linksys.JPG) In this example, the range is x.150 to x.199.

Do you connect?```
ping -c3 www.ubuntu.com
```Reboot and try again:```
ping -c3 www.ubuntu.com
```If everything works as expected, you may safely remove Network Manager.

---

