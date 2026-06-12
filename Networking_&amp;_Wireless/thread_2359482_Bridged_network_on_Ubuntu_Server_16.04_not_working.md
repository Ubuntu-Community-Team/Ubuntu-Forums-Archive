---
title: "Bridged network on Ubuntu Server 16.04 not working in VirtualBox guest running Window"
date: 2017-04-24
forum: Networking &amp; Wireless
---

### Post by stuartmillington on 2017-04-24
[COLOR=#111111][FONT=Ubuntu]I have Ubuntu Server 16.04 with GUI (why? I'm lazy!). I have installed Oracle VirtualBox WorkStation 12, and have created a VM that I have installed Windows 7 on, but I cannot get networking to work on the guest.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On the host my /etc/network/interfaces file looks like this:[/FONT][/COLOR]
```
auto lo
iface lo inet loopback

# The primary network interface 
auto enp3s0 iface enp3s0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
# broadcast 192.168.1.255
dns-nameservers 8.8.8.8 192.168.1.1

# This is an autoconfigured IPv6 interface iface enp3s0 inet6 auto
auto virbr0 iface virbr0 inet dhcp
```

[COLOR=#111111][FONT=Ubuntu]When I run **ifconfig** I get the following:
[/FONT][/COLOR]```

enp3s0    Link encap:Ethernet  HWaddr 00:24:1d:c0:87:d1  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:c0a8:2:0:224:1dff:fec0:87d1/64 Scope:Global
          inet6 addr: fe80::224:1dff:fec0:87d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7756 (7.7 KB)  TX bytes:14219 (14.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:12475 (12.4 KB)  TX bytes:12475 (12.4 KB)

virbr0    Link encap:Ethernet  HWaddr 52:54:00:7f:20:1a  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1108 (1.1 KB)

```

[COLOR=#111111][FONT=Ubuntu]I think that the 'virbr0' is configured in NetworkManager. However, it is configured to use DHCP but is giving an IP in ifconfig of 192.168.122.1, not 192.168.1.???.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
In the definition of my VM I set the network to use a Bridged Adapter called 'virbr0'. When I run **ipconfig** in the guest I get an IP address of 169.254.75.144, with a subnet mask of 255.255.0.0.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The above dump from **ifconfig** on the host was done after a reboot. Before the reboot it also had a reference to virbr0:avahi, with an IP address of 169.254.?.?, and a subnet mask of 255.255.0.0. I don't know where the reference to avahi came from, or why it has disappeared, but I suspect that it was this that was (and still is) giving me my unwanted IP address in my VM. I have only noticed this reference to avahi once and quite by accident.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]A little background history: I did have a VM running on KVM (2 in fact). I was trying to install XPEnology on the 2nd VM but I ran into a problem (as it turns out it is the same problem with the IP address). As there were more guided instructions for the installation of XPEnology on a VM for VirtualBox I decided to do away with KVM and try VirtualBox. To get VBox to run I had to remove KVM (VBox will not co-exist with KVM). It was only when I got the same problem with IP address that I realized that the problem is with the Bridge Adapter. Having said that I also set up the 1st VM on KVM to run Windows 7 using the same Bridge Adapter 'virbr0' and that worked OK! It was because of that that I had no reason to suspect the BA when I was trying to install XPEnology. I have done so much messing about that I am really not sure where I am at the moment.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can someone help me get the Bridging Adapter to work please? Is a BA normally set up with a static IP or DHCP? Could that fact that the BA is not configured in /etc/network/interfaces but is in NetworkManager be part of the problem?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-04-24
You shouldn't need to configure anything to use bridged networking in a VirtualBox VM if your network allocates addresses by DHCP.  Simply choose "bridged" in the Network settings in VB, then boot the virtual machine.  It should get the same address information as it would were it a physical machine sitting on the network and using DHCP.

If you want to have the VM be a server, then a static assignment is the better choice.  In your post, you show this:
```

auto enp3s0 iface enp3s0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
# broadcast 192.168.1.255
dns-nameservers 8.8.8.8 192.168.1.1

```
I believe the "iface" directive [needs to be on a separate line]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing").  Did you create this file with an editor using sudo or some other method?

---

