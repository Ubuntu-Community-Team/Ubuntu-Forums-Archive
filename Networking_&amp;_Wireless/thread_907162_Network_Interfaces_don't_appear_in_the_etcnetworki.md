---
title: "Network Interfaces don't appear in the /etc/network/interfaces configuration file."
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by laith43d on 2008-09-01
Hi,

I have a trouble, when I run ifconfig at the command line it gives this output:

> [laith@laith ~]$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1c:25:14:6e:c5  
          inet addr:192.168.20.11  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe14:6ec5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:82203773 (78.3 MB)  TX bytes:9699150 (9.2 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103455 (101.0 KB)  TX bytes:103455 (101.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.78.1  Bcast:192.168.78.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.251.1  Bcast:192.168.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:a5:2a:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-A5-2A-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


But when I cat /etc/network/interfaces, it displays:

> [laith@laith ~]$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback




what is the problem exactly, I have all my interfaces up and running, yet they don't appear at the config file.

FYI: I use wicd application instead of the Network Manager, to administer my network connections.

Thanks,

---

### Post by tolmeda on 2008-09-01
Are you having a problem with the interfaces that aren't listed in the file? I don't think that file is meant to show them unless you want to create a non-default configuration. Can you provide more details as to what you're trying to accomplish?

---

### Post by caljohnsmith on 2008-09-01
> **laith43d said:**
> 
FYI: I use wicd application instead of the Network Manager, to administer my network connections.

Network Manager uses the /etc/netork/interfaces file to save all its network interface card (NIC) settings, but I think WICD uses /opt/wicd/data/*.conf, or /etc/wicd/data/*.conf depending on the version. Check for those files and I think you'll find your NIC configuration.

---

### Post by laith43d on 2008-09-02
Hi,

> **tolmeda said:**
> Can you provide more details as to what you're trying to accomplish?

I would like to change the MAC address of my NIC.

Also, I found my config files in /opt/wicd/data/*.conf, but I did not find any line to configure the MAC address.

Thanks,

---

### Post by caljohnsmith on 2008-09-02
> **laith43d said:**
> 
I would like to change the MAC address of my NIC.

Also, I found my config files in /opt/wicd/data/*.conf, but I did not find any line to configure the MAC address.

Thanks,
It is always helpful if you state your ultimate goal on the outset, because sometimes there are different and/or better ways of doing things then what you might initially think. First, do you know for sure your NIC supports changing its MAC address? Not all of them do. You can try the following to temporarily change your NIC's MAC and see if it works:
```
sudo ifconfig wlan0 down  [COLOR="Blue"](or disable your wireless interface manually with WICD)[/COLOR]
sudo ifconfig wlan0 hw ether 00:28:C7:0A:42:A2
sudo ifconfig wlan0 up
ifconfig
```
Of course change the MAC address above to be whatever you want. Look for "HWaddr" for your NIC after using that ifconfig command, and that should be your new MAC. So does that change the MAC of your NIC?

---

### Post by laith43d on 2008-09-03
Hi,

Yes, It does work, when I change my MAC address as you noticed.

Now, I would like to change my MAC address permanently, thus, when I reboot, it remains untouched.

Thanks,

---

### Post by caljohnsmith on 2008-09-03
I'm not certain this will work with WICD, but you could try using Gnome's Configuration Editor. Just go to Applications > System Tools > Configuration Editor, then go to apps > gtkwifi and select network interface, right click, and you can edit the MAC address.

---

### Post by laith43d on 2008-09-03
Hi,

I don't have such entry (gtkwifi) in the gconf-editor.
Also, I searched for such entry, but my search went useless.

Any help would be appreciated.

Thanks,

---

