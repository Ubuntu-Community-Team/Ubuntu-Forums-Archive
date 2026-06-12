---
title: "[SOLVED] Can ping local computers, no response from gateway"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by jaestar on 2008-06-30
I have a Dell Optiplex 755, brand new. Installed Ubuntu 8.04 with the alternate CD. Everything is working perfectly (that I've found so far) except for the network. This is not a wireless issue because I don't have any wireless cards.

1) Our network is static IP, dynamic IP is not an option.
2) I have a predefined hostname for the computer that matches the IP address, I can change them to other free ones that we have, but they change as a pair.
3) I have a Linksys Switched Hub connected to my wall port that I have four computers (including the Optiplex 755) connected to.
4) The cable isn't the problem, I've tested it.

The problem: I can ping the local computers on the switched hub using their IP addresses and receive a reply, if I try to use SSH, the connection takes a very long time and is closed by the remote computer.
I cannot: use the hostnames of the machines on my local switch instead of the IP address, I do not receive a ping reply from computers outside of the local hub but within the network using their IP address or hostname, and I do not receive a ping reply from the gateway or anything on the internet.

I think that once the problem of being able to contact the gateway is solved, the others will fall into place as well.

Here's some info that usually is asked for.

Ethernet Card:
```
$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
```

Hosts file (IPv6 stuff removed):
```
$ cat /etc/hosts
127.0.0.1 localhost
130.127.24.129 vanzetti.parl.clemson.edu vanzetti
```

Resolv.conf file:
```
$ cat /etc/resolv.conf
search parl.clemson.edu
nameserver 130.127.200.2
nameserver 130.127.8.8
nameserver 130.127.28.40
```

Ifconfig:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:4f:f0:8b:7c  
          inet addr:130.127.24.129  Bcast:130.127.24.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4fff:fef0:8b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:295975 (289.0 KB)  TX bytes:10144 (9.9 KB)
          Memory:febe0000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78160 (76.3 KB)  TX bytes:78160 (76.3 KB)
```

Any thoughts on what could be wrong? I originally had the problem where sudo could not resolve the host name, but found the solution posted on the forums and modified the hosts file; don't know if that's related or not. Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-06-30
Maybe something is wrong with your routing table? Please post the output of "route" as that may give some clue as to your problem...

---

### Post by jaestar on 2008-07-01
Sure thing. When I typed it in it took about 45-60 seconds to come back to the prompt.

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         130.127.24.2    0.0.0.0         UG    100    0        0 eth0

```

---

### Post by caljohnsmith on 2008-07-01
So you've verified that 130.127.24.2 is your Linksys switched hub and you can successfully ping it from the other computers? 

I noticed in your /etc/hosts you don't have an entry for 127.0.1.1; I've seen conflicting information on whether there needs to be a "127.0.1.1" entry in the /etc/hosts file if your name.domain is all ready given as a static IP address in the same file, so I'm not sure this will work, but it will only take you a few minutes to try: just add "127.0.1.1 vanzetti" as a line in /etc/hosts, reboot, and see if that changes anything. If not you can always change it back.

---

### Post by jaestar on 2008-07-01
> **caljohnsmith said:**
> So you've verified that 130.127.24.2 is your Linksys switched hub and you can successfully ping it from the other computers? 

Yep. I can ping the gateway and do an nslookup on the IP address to get the name of the gateway on my other computers.

> **caljohnsmith said:**
> I noticed in your /etc/hosts you don't have an entry for 127.0.1.1; I've seen conflicting information on whether there needs to be a "127.0.1.1" entry in the /etc/hosts file if your name.domain is all ready given as a static IP address in the same file, so I'm not sure this will work, but it will only take you a few minutes to try: just add "127.0.1.1 vanzetti" as a line in /etc/hosts, reboot, and see if that changes anything. If not you can always change it back.

I added "127.0.1.1 vanzetti" to the hosts file, reboot, same problem. So I added the "vanzetti.parl.clemson.edu" to the same line, reboot, same problem.

Could the network card be defective? I tried to install FC9 on the computer previously, but the video and the network didn't work. I switched to Ubuntu and the video works but still not the network. I haven't tried any other OSes.

---

### Post by caljohnsmith on 2008-07-01
Can you swap your network card into one of your other computers that is working with your LAN? Or as you mentioned, if you can try a different OS on your problematic computer that might be a good idea at this point. Anything you can do like that to get some more clues would sure help narrow down your problem.

---

### Post by jaestar on 2008-07-01
Unfortunately, it is an onboard port. I took it to our install group to have them put Windows Vista on it and test the network port with their diagnostic tools. Are there driver issues with the default network driver and the 82566DM-2?

---

### Post by Iowan on 2008-07-01
What's in **/etc/networking/interfaces**?

---

### Post by jaestar on 2008-07-02
Instead of installing Vista, they did some diagnostics by setting the computer to DHCP and hooked it up to their network (which uses DHCP). They said that everything was working fine. I guess that makes it a software issue and not a faulty onboard NIC.

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 130.127.24.129
	netmask 255.255.255.0
	network 130.127.24.0
	broadcast 130.127.24.255
	gateway 130.127.24.2
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 130.127.200.5 130.127.8.8
	dns-search parl.clemson.edu

```

---

### Post by jaestar on 2008-07-02
And I should mention that the system is using the e1000e driver that came default from the installation. I tried to switch to the e1000 driver from Intel, but I couldn't get the e1000 to create an eth0 interface.

---

### Post by jaestar on 2008-07-03
I moved the computer off of my switch and placed it on the switch in the neighboring office, now everything is working perfectly. I don't know why, but it's working now. Thank you for all the help.

---

