---
title: "2nd nic kills networking"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by Denton Yoder on 2017-08-04
Error when two nics enabled:
service networking restart
Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

After removing the second nic from interfaces file: (second nic shows up and works):
```
Ifconfig -a
enp3s0    Link encap:Ethernet  HWaddr 00:1d:09:6a:f7:3e
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe6a:f73e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24061 errors:1727 dropped:0 overruns:0 frame:1727
          TX packets:23355 errors:3 dropped:0 overruns:0 carrier:3
          collisions:3041 txqueuelen:1000
          RX bytes:36001985 (36.0 MB)  TX bytes:1797781 (1.7 MB)

enp7s0    Link encap:Ethernet  HWaddr 00:1d:09:6a:f7:40
          inet addr:192.168.4.1  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe6a:f740/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34656 (34.6 KB)  TX bytes:30366 (30.3 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)
```

<SystemCTL>
```
systemctl status networking.service
&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Fri 2017-08-04 10:34:43 EDT; 1min 18s ago
     Docs: man:interfaces(5)
  Process: 1881 ExecStop=/sbin/ifdown -a --read-environment --exclude=lo (code=exited, status=0/SUCCESS)
  Process: 1938 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 1932 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list
 Main PID: 1938 (code=exited, status=1/FAILURE)

Aug 04 10:34:43 t1 systemd[1]: Starting Raise network interfaces...
Aug 04 10:34:43 t1 ifup[1938]: RTNETLINK answers: File exists
Aug 04 10:34:43 t1 ifup[1938]: Failed to bring up enp7s0.
Aug 04 10:34:43 t1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Aug 04 10:34:43 t1 systemd[1]: Failed to start Raise network interfaces.
Aug 04 10:34:43 t1 systemd[1]: networking.service: Unit entered failed state.
Aug 04 10:34:43 t1 systemd[1]: networking.service: Failed with result 'exit-code'.
```


<journalctl>
```
journalctl -xe
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit ssh.service has finished reloading its configuration
--
-- The result is done.
Aug 04 10:34:43 t1 sshd[1220]: Server listening on 0.0.0.0 port 22.
Aug 04 10:34:43 t1 sshd[1220]: Server listening on :: port 22.
Aug 04 10:34:43 t1 ifup[1938]: RTNETLINK answers: File exists
Aug 04 10:34:43 t1 ifup[1938]: Failed to bring up enp7s0.
Aug 04 10:34:43 t1 kernel: bnx2 0000:07:00.0 enp7s0: using MSI
Aug 04 10:34:43 t1 kernel: IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
Aug 04 10:34:43 t1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Aug 04 10:34:43 t1 systemd[1]: Failed to start Raise network interfaces.
-- Subject: Unit networking.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit networking.service has failed.
--
-- The result is failed.
Aug 04 10:34:43 t1 systemd[1]: networking.service: Unit entered failed state.
Aug 04 10:34:43 t1 systemd[1]: networking.service: Failed with result 'exit-code'.
Aug 04 10:34:45 t1 kernel: bnx2 0000:03:00.0 enp3s0: NIC Copper Link is Up, 100 Mbps half duplex
Aug 04 10:34:45 t1 kernel:
Aug 04 10:34:45 t1 kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Aug 04 10:34:47 t1 kernel: bnx2 0000:07:00.0 enp7s0: NIC Copper Link is Up, 1000 Mbps full duplex
Aug 04 10:34:47 t1 kernel: , receive & transmit flow control ON
Aug 04 10:34:47 t1 kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp7s0: link becomes ready
Aug 04 10:35:59 t1 /usr/lib/snapd/snapd[1123]: snapmgr.go:496: DEBUG: Next refresh scheduled for 2017-08-04 11:35:33.488
```

---

### Post by TheFu on 2017-08-06
First, whenever posting commands and output, please, please, please, please use code tags so things line up.  It is under "Adv Reply."  Too hard to read otherwise.

Please post **ifconfig** and **route** for the systems impacted.  I don't use systemd, but networking is networking.  It isn't clear what you mean by "kills networking".  If you have any bridges, those tend to break systemd networking.  Manually bringing down and up the interfaces in the correct order is required.

Does each interface work alone?

---

### Post by Denton Yoder on 2017-08-08
sorry, Thanks for the tip on tags...

The results from an ifconfig -a are at the top of the post....

I have two static nics.  when I enable both of them and try to restart the networking service (I am definitely open to a better way) I get the following error:
```
Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.
```
Results of these two commands are in the code windows on the top as well...

Here is my interfaces file: **/etc/network/interfaces**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
   address 192.168.2.12
   gateway 192.168.2.1
   netmask 255.255.255.0
   dns-nameserver 192.168.2.1

#auto enp7s0
#iface enp7s0 inet static
#   address 192.168.4.1
#   gateway 192.168.2.1
#   netmask 255.255.255.0
#   dns-nameserver 192.168.2.1

```

If I comment out the second nic, and restart the networking service, they both magically work.  Which I really don't get how turning it off makes it work...

**Summary**
[LIST]
[*]Need to comment out 2nd nic from interfaces to boot
[*]Then add 2nd nic to interfaces and try to restart service but fail
[*]then comment out 2nd nic again
[*]then restart networking service and it works.
[*]then reset firewall settings...
[*]
[/LIST]
This makes rebooting too complicated...  Is there a better way to configure and enable nics?

---

### Post by Denton Yoder on 2017-08-08
**Route info:**
nic1 = enp3s0
nic2 = enp7s0
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         fw106           0.0.0.0         UG    0      0        0 enp3s0
192.168.2.0     *               255.255.255.0   U     0      0        0 enp3s0
192.168.4.0     *               255.255.255.0   U     0      0        0 enp7s0

```

---

### Post by TheFu on 2017-08-08
I don't use systemd. Sorry.  Most of the problems appear to be with systemd related stuff.  Hopefully someone else will see this and offer help.

Just be certain you only have 1 default gateway.  If you need other routes, outside the netmask ones and the single GW, you'll need to add those manually.

In the interfaces file - don't include the gateway or dns-stuff in the 2nd stanza.  DNS isn't per-network to my knowledge. I miss the old days pre-resolvconf when we just edited the DNS resolv.conf file manually (or using devops tools).  If DNS was per-interface, that could be useful.

---

### Post by Denton Yoder on 2017-09-05
Removed gateway and dns from second stanza and networking service still fails with same error as top of thread...
setup script to execute to clear up problems:  
First copy /etc/network/interfaces to interfaces.one, and interfaces.two... Make sure second nic is commented out of name.one...
```

#!/bin/sh
echo "setup two nices"
cp /etc/network/interfaces.two /etc/network/interfaces

echo "service restart"
service networking restart

echo "setup one nic"
cp /etc/network/interfaces.one /etc/network/interfaces

echo "service restart"
service networking restart

echo "disable ufw"
ufw disable

echo "reset ufw"
ufw --force reset

echo "open ports"
ufw allow 22
ufw allow 80

echo "enable ufw"
ufw --force enable

```

---

### Post by TheFu on 2017-09-05
Does systemd use "service"?

---

