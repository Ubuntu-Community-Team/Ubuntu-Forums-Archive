---
title: "unable to mount cifs share when connected to VPN"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by takeawaydave on 2018-10-13
I have a ubuntu 18.04.1 LTS running at the moment as a Hyper-V VM (not that this really matter) but am using OpenVPN to connect to my VPN (Private Internet Access).

I have a CIFS mount from the Windows 10 host which I want to have hosted while using the VPN. At the moment the CIF mount will not work when connectred over VPN.

I have tried adding a second interface with the intention of using the first (eth0) interface for VPN and the second (eth1) for LAN traffic and getting this CIFS share mounted. But I am not sure how to do this. 

Any way of getting only eth0 traffic to route via tun0? And leaving the default route in place for eth1 ?

---

### Post by TheFu on 2018-10-13
It depends.  Is the VM on the same subnet as the host or is it NAT'd?

**route -n** from the guest VM will show half the answer.  The other half has to come from Windows. There was a route command, but I don't know if Win10 has it.

---

### Post by takeawaydave on 2018-10-13
The VM is on a different network to the Host.

Windows 10 host is on 192.168.0.1/24
Ubuntu VM is on 192.168.1.1/24

The Windows 10 machine is wired to a netgear switch
The Ubuntu Machine has taken the wireless adapter of the host.

Output from Ubuntu VM:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.21.97.129   0.0.0.0         UG    100    0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
172.21.97.128   0.0.0.0         255.255.255.240 U     100    0        0 eth1

Windows 10

C:\Users\david>route print
================================================== =========================
Interface List
  7...f0 79 59 6b 11 cd ......Intel(R) Ethernet Connection (2) I218-V
 12...6e 71 d9 f2 bc 13 ......Microsoft Wi-Fi Direct Virtual Adapter
  8...6e 71 d9 f2 b4 13 ......Microsoft Wi-Fi Direct Virtual Adapter #2
  6...00 ff 0e 83 78 98 ......TAP-Windows Adapter V9
  1...........................Software Loopback Interface 1
 24...fe 15 87 73 78 71 ......Hyper-V Virtual Ethernet Adapter #3
================================================== =========================

IPv4 Route Table
================================================== =========================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.0.1     192.168.0.10    281
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
    172.21.97.128  255.255.255.240         On-link     172.21.97.129   5256
    172.21.97.129  255.255.255.255         On-link     172.21.97.129   5256
    172.21.97.143  255.255.255.255         On-link     172.21.97.129   5256
      192.168.0.0    255.255.255.0         On-link      192.168.0.10    281
     192.168.0.10  255.255.255.255         On-link      192.168.0.10    281
    192.168.0.255  255.255.255.255         On-link      192.168.0.10    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link     172.21.97.129   5256
        224.0.0.0        240.0.0.0         On-link      192.168.0.10    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link     172.21.97.129   5256
  255.255.255.255  255.255.255.255         On-link      192.168.0.10    281
================================================== =========================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0      192.168.1.1  Default
          0.0.0.0          0.0.0.0      192.168.0.1  Default
================================================== =========================

IPv6 Route Table
================================================== =========================
Active Routes:
 If Metric Network Destination      Gateway
  1    331 ::1/128                  On-link
 24   5256 fe80::/64                On-link
  7    281 fe80::/64                On-link
 24   5256 fe80::70dd:bfe1:819:4ee/128
                                    On-link
  7    281 fe80::917d:4515:f2da:9fa2/128
                                    On-link
  1    331 ff00::/8                 On-link
 24   5256 ff00::/8                 On-link
  7    281 ff00::/8                 On-link
================================================== =========================
Persistent Routes:
  None 	 				 				 			 		 	      	  		 		 		 	
```

---

### Post by TheFu on 2018-10-13
And that is why the VPN blocks the CIFS access. By default, PIA/openvpn allows access on the same LAN.  If you want something else, I don't know how to do that without control over the VPN server.


BTW, please use **code tags** with output like above. Too hard to read otherwise.  The output should line up in columns.  Go Advanced (#).

---

### Post by takeawaydave on 2018-10-13
Thanks - Didn't know the restiction here. Deleted the output to clean the thread up.

---

### Post by TheFu on 2018-10-13
There are solutions. If the data was provided with code tags, some smart people can probably help.  The easy answer is to use a bridge connection from the host, not wifi.  Actually, not using wifi would be my recommendation for all VMs anyway.

If the guest and host are on the same subnet, then PIA VPNs should allow the access.
So, if 
Windows 192.168.0.11/24
Ubuntu 192.168.0.222/24
Then PIA provides a new subnet on 10.x.x.x on the Ubuntu system, both windows and ubuntu will be able to talk over 192.168.0/24, no problem.

The IPs aren't important. It is all about the subnets.

---

### Post by oldos2er on 2018-10-13
> **takeawaydave said:**
> Thanks - Didn't know the restiction here. Deleted the output to clean the thread up.

We need to see the command output to help diagnose the problem, so I restored it and added code tags for readability. 

There is information on using tags in posts here: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by TheFu on 2018-10-13
Ubuntu is on 
> 172.21.97.128   0.0.0.0         255.255.255.240
According to the post above, not 192.168.1/24. Is that correct?

Whenever I connect with PIA, the system gets a 10.x.x.x address.  Call me confused.

---

