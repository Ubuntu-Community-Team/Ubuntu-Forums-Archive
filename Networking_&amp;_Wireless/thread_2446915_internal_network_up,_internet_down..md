---
title: "internal network up, internet down."
date: 2020-07-09
forum: Networking &amp; Wireless
---

### Post by chaosmstr on 2020-07-09
So, I have a fun one.
I'm running 18.04.4 on a Xenserver 7.6 VM with NordVPN.
This started... beginning of June, I think.
Other VM's still have connection. 

After a random amount of time (hours to days) my internet connectivity drops.
Issue goes away after reboot.

I can still access the local network, but ping outside of the local network goes nowhere - though one of the times I did get an "operation not permitted" for ping.
I have dis/connected eth0, I have removed/added the nic in the VM, I have added additional VM nics, none of these actions make a difference.
NordVPN commands do nothing, since it can't connect to the net to login, connect, disconnect, etc.
Since I still have internet through other VMs (some use the VPN and have no issues), I'm left with the OS.


However, I've run out of ideas for additional troubleshooting of which aspect of the OS is having issues.
I'm only slightly above avg user level of linux, so I'm looking for help for when this connection goes down again.

What commands should I issue to find out what part has failed?

---

### Post by TheFu on 2020-07-10
DNS issue or truly connectivity problem?
ping by ip works or not?

---

### Post by chaosmstr on 2020-07-17
ping by IP works on internal network, nothing external. I can see my router and everything behind it.
I cannot see beyond my router, yet other devices can.

---

### Post by TheFu on 2020-07-18
Any chance NordVPN has a device limit for connections which has been exceeded?
Does networking without any VPN work from this VM?

Can you post the common network information commands and output for both working and non-working configs?
```
ip addr
route -n
```

AND clearly label which is for each?  It isn't that we don't believe you, but ... best to lead with facts.

BTW, I haven't used Xen in about 9 yrs. I don't remember networking issues, but did have some others usually after a new kernel was placed on the hostOS.

---

### Post by chaosmstr on 2020-07-19
Ok.. here's the working correctly info, I'll have to wait for it to fail for that bit.

For the VPN, no.. I'm not hitting the device limit.
And from what I can find, it will simply decline to connect if there's more devices than allowed.
This unit is connected to the VPN, and when the connection fails I cannot do anything with the VPN, including disconnect.

```
ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 0e:73:56:72:10:82 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.127/8 brd 192.255.255.255 scope global eth0
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.8.1.24/24 brd 10.8.1.255 scope global tun0
       valid_lft forever preferred_lft forever

~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.1.1        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.8.1.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
50.3.173.186    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.8.1.1        128.0.0.0       UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 eth0
192.0.0.0       0.0.0.0         255.0.0.0       U     100    0        0 eth0
```

---

### Post by TheFu on 2020-07-19
eth0 netmask is very likely incorrect.  Use a /24, not a /8.  You don't own all of 192.x.x.x/8.
I see something else funny, but let's start by fixing that netmask first.

---

### Post by uninvolved on 2020-07-19
I'll toss this into the mix, as it may help.

I've found NordVPN flaky at times. I'll lose my connection to the outside world, disconnect NordVPN with 'nordvpn d', and all is well. I reconnect and the internet is still down. Changing servers w/NordVPN doesn't always even work but will sometimes work if I connect to a different country endpoint. 

I've no idea if that'll help, but it might be something to look into.

---

### Post by chaosmstr on 2020-08-08
Well.. somethings changed because it hasn't lost link since I originally posted. 
Not that I'm complaining. :)
Still keeping an eye on it just in case, but looks like I'm good for now.

---

### Post by TheFu on 2020-08-08
Did you fix these routes!?
```
192.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 eth0
192.0.0.0       0.0.0.0         255.0.0.0       U     100    0        0 eth0
```

As mentioned, 192.0.0.0/8 is not all private addresses, only 192.168.0.0/16 are. The rest are owned by different companies.

192.1.0.0/16 is owned by a company in Cambridge, for example. But you can't get their and they can't get to you with that wrong netmask.

That route needs to be fixed.

---

