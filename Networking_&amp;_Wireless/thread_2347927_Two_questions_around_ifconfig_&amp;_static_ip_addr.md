---
title: "Two questions around ifconfig &amp; static ip addresses"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by blackagave2 on 2016-12-29
I have a network set up at home that is giving me back different responses
for ifconfig for each computer(having just read that during a proofread I
realized...duh). There are currently 3 computers, will be four eventually,
in total on the network that I would like to be able to access a few from
stable static ip addresses.

The mac is wireless.
the HTPC is wired.
BigBox sits behind a Asus RT-n16 running dd-wrt and is set up to be a
client bridge.

Now I know per
[https://www.swiftstack.com/docs/install/configure_networking.html](https://www.swiftstack.com/docs/install/configure_networking.html) I'm
supposed to edit /etc/network/interfaces.

however, I'm getting really confused with the ifconfig outputs.

eth0 on the htpc:

```
eth0      Link encap:Ethernet  HWaddr 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76072836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31133640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:97038587365 (97.0 GB)  TX bytes:8395717189 (8.3 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:602966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57609169 (57.6 MB)  TX bytes:57609169 (57.6 MB)

```

lo0, gif0, stf0, en0, en1, en2, p2p0, awdl0, bridge0 on the mac:

```
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
    options=3<RXCSUM,TXCSUM>
    inet6 ::1 prefixlen 128
    inet 127.0.0.1 netmask 0xff000000
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
    nd6 options=1<PERFORMNUD>
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d
    inet6 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d prefixlen 64 scopeid 0x4
    inet 192.168.1.9 netmask 0xffffff00 broadcast 192.168.1.255
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active
en1: flags=963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX> mtu 1500
    options=60<TSO4,TSO6>
    ether 4a:00:07:76:e7:e0
    media: autoselect <full-duplex>
    status: inactive
en2: flags=963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX> mtu 1500
    options=60<TSO4,TSO6>
    ether 4a:00:07:76:e7:e1
    media: autoselect <full-duplex>
    status: inactive
p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
    ether 06:b3:01:c9:1d:53
    media: autoselect
    status: inactive
awdl0: flags=8943<UP,BROADCAST,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1484
    ether 211d:58c7:9682:937a:366e:494f:41a2:da18
    inet6 211d:58c7:9682:937a:366e:494f:41a2:da18 prefixlen 64 scopeid 0x8
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active
bridge0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    options=63<RXCSUM,TXCSUM,TSO4,TSO6>
    ether c6:b3:01:9c:82:00
    Configuration:
        id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
        maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
        root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
        ipfilter disabled flags 0x2
    member: en1 flags=3<LEARNING,DISCOVER>
            ifmaxaddr 0 port 5 priority 0 path cost 0
    member: en2 flags=3<LEARNING,DISCOVER>
            ifmaxaddr 0 port 6 priority 0 path cost 0
    nd6 options=1<PERFORMNUD>
    media: <unknown type>
    status: inactive

```


lo, p4p1 on the BigBox:

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:21151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6169882 (6.1 MB)  TX bytes:6169882 (6.1 MB)

p4p1      Link encap:Ethernet  HWaddr 10:bf:48:82:d4:69
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 211d:58c7:9682:937a:366e:494f:41a2:da18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:173155572 (173.1 MB)  TX bytes:36165221 (36.1 MB)
```

What do all those mean?
Do I create the static ip addresses as noted above in the link but just
where the current entry is but "should be" eth0?

---

### Post by oldfred on 2016-12-30
The names have been changed to protect the innocent. (was that Dragnet?)
New naming:
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Do not mix gui configuration with network manager and command line with ifconfig.
You can create real problems trying to use both, and I do not know enough details to resolve those kind of issues.

I know my old routers reserved 50 or 100 addresses for DHCP typically starting at 100. So I set a fixed IP outside that range. Before I knew that and tried to assign within range had all sorts of problems.

My newest router allows one to set fixed address in the router. 
Not sure if I also had to set same address in router & computer or not? 
Now usually using DHCP, but it usually has same IP for each device without specifying fixed. But would expect rebooting router might change that.

Old router was first come first served on addresses.

If you have a Netgear router be sure to update its firmware.
[http://www.ghacks.net/2016/12/21/netgear-releases-first-final-firmware-updates-for-router-security-issue/](http://www.ghacks.net/2016/12/21/netgear-releases-first-final-firmware-updates-for-router-security-issue/)

---

### Post by The Cog on 2016-12-30
Probably the easiest approach is to configure fixed IP addresses against the known MAC addresses in the DHCP server, so that when these devices boot, it always gives them the same IP address. This configuration will almost certainly be somewhere inside your router configuration. If your router uses a pool of addresses for DHCP, e.g. 2-100, then you will probably have to allocate an address outside that range, i.e. above 100.

If you choose to use /etc/network/interfaces to configure addresses then you must ensure you don't allocate adresses that might be allocated by the DHCP server. DHCP servers normally seem to allocate from 2 upwards so again, allocate addresses over 100 to avoid conflicts.

Given your uncertainty about the meaning of the ifconfig output, I think configuring your DHCP server (router) to dish out fixed addresses to known MAC addresses The MAC addresses of the computers won't change, they are rather like serial numbers, and can be found from the ifconfig output.

EDIT: 
P.S. 
Your MAC address will be 12 hex digits probably separated by colons to improve readability. e.g. HWaddr 10:bf:48:82:d4:69 on BigBox. 
I really don't understand the ifconfig output from htpc claiming a 16 byte hardware address for eth0. That's not possible. Eternet uses 6-byte hardware addresses.
The command "ip link" also gives the hardware MAC address of each interface.

Recent versions of Linux tend to use really strange names rather than eth0, eth1 etc. The reasoning is to make the interface names more stable - the old numbering depended on the order in which hardware was discovered during boot-up, which might vary from one reboot to the next.

Regards "what do all those mean?":
[http://www.aboutlinux.info/2006/11/ifconfig-dissected-and-demystified.html](http://www.aboutlinux.info/2006/11/ifconfig-dissected-and-demystified.html)
More specific questions are welcome, but I'm not going to write an essay when there are good ones already out there.

---

### Post by 1clue on 2016-12-30
There comes a point where juggling config files on multiple boxes becomes time consuming and frustrating, and another point where it becomes impossible.

You should have a central authority on ip addresses and a central authority on names, if you use them.  These authorities can be your router if it has the capability, or it can be a different device serving dhcp and dns.

For critical servers you typically manually configure the address and dns settings, but they still are marked static in dhcp and dns. If you have a dhcp server then that should automatically become your single authority on ip addresses, and if you have a DNS server it should become your single authority on names. Any difference between any host and those services, the host is wrong.

---

### Post by slickymaster on 2016-12-30
*Thread moved to **Networking & Wireless**.*

---

### Post by blackagave2 on 2016-12-30
> **oldfred said:**
> The names have been changed to protect the innocent. (was that Dragnet?)
New naming:
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)


Thanks.

> **oldfred said:**
> 
Do not mix gui configuration with network manager and command line with ifconfig.
You can create real problems trying to use both, and I do not know enough details to resolve those kind of issues.


I wouldn't.

> **oldfred said:**
> 
I know my old routers reserved 50 or 100 addresses for DHCP typically starting at 100. So I set a fixed IP outside that range. Before I knew that and tried to assign within range had all sorts of problems.


Thanks for pointing this out. I'd accidently assigned my bridge to the DHCP range.

> **oldfred said:**
> 
My newest router allows one to set fixed address in the router. 
Not sure if I also had to set same address in router & computer or not? 
Now usually using DHCP, but it usually has same IP for each device without specifying fixed. But would expect rebooting router might change that.

Old router was first come first served on addresses.

If you have a Netgear router be sure to update its firmware.
[http://www.ghacks.net/2016/12/21/netgear-releases-first-final-firmware-updates-for-router-security-issue/](http://www.ghacks.net/2016/12/21/netgear-releases-first-final-firmware-updates-for-router-security-issue/)

Mine does as well.

---

### Post by blackagave2 on 2016-12-30
> **The Cog said:**
> Probably the easiest approach is to configure fixed IP addresses against the known MAC addresses in the DHCP server, so that when these devices boot, it always gives them the same IP address. This configuration will almost certainly be somewhere inside your router configuration. If your router uses a pool of addresses for DHCP, e.g. 2-100, then you will probably have to allocate an address outside that range, i.e. above 100.

It appears that my router allows me to assign static ip addresses in the router admin based off MAC addresses. 

> **The Cog said:**
> If you choose to use /etc/network/interfaces to configure addresses then you must ensure you don't allocate adresses that might be allocated by the DHCP server. DHCP servers normally seem to allocate from 2 upwards so again, allocate addresses over 100 to avoid conflicts.

Knowing what I know now I doubt I will. Having the router assing seems simplest. After that a hosts file should suffice.

> **The Cog said:**
> Given your uncertainty about the meaning of the ifconfig output, I think configuring your DHCP server (router) to dish out fixed addresses to known MAC addresses The MAC addresses of the computers won't change, they are rather like serial numbers, and can be found from the ifconfig output.

EDIT: 
P.S. 
Your MAC address will be 12 hex digits probably separated by colons to improve readability. e.g. HWaddr 10:bf:48:82:d4:69 on BigBox. 
I really don't understand the ifconfig output from htpc claiming a 16 byte hardware address for eth0. That's not possible. Eternet uses 6-byte hardware addresses.
The command "ip link" also gives the hardware MAC address of each interface.

Recent versions of Linux tend to use really strange names rather than eth0, eth1 etc. The reasoning is to make the interface names more stable - the old numbering depended on the order in which hardware was discovered during boot-up, which might vary from one reboot to the next.

Yeah about that. Sorry. I'm a newb but not a noob. or something. I went and found a bunch of random ip addreses and cut and paste them where I thought they might go to obfuscate myself a bit. Learning about the new interfaces clarified things but I think I'll let that resolve itself so I don't muck it up.

> **The Cog said:**
> Regards "what do all those mean?":
[http://www.aboutlinux.info/2006/11/ifconfig-dissected-and-demystified.html](http://www.aboutlinux.info/2006/11/ifconfig-dissected-and-demystified.html)
More specific questions are welcome, but I'm not going to write an essay when there are good ones already out there.

Thanks for this.

---

### Post by chili555 on 2016-12-31
It's all pretty simple and pretty straight-forward with or without a router that allows DHCP reservations.

* Find out the DHCP range in the router. For example, let's assume the router uses 192.168.1.2 to 192.168.1.51; a pool of 50 addresses. All the addresses from  x.52 on up are free for static IPs.

* In a server, without a desktop environment, set the address in /etc/network/interfaces: [http://askubuntu.com/questions/392941/ubuntu-server-wont-recognize-ethernet/393030#393030](http://askubuntu.com/questions/392941/ubuntu-server-wont-recognize-ethernet/393030#393030)

* In a desktop machine, set the address in Network Manager: [https://www.youtube.com/watch?v=Hvi2cTMmTq0](https://www.youtube.com/watch?v=Hvi2cTMmTq0)

* Assuming you are the administrator of all this, keep a ledger of machine names, addresses and other details such as, perhaps, location, service history, update history, etc.

---

### Post by blackagave2 on 2016-12-31
> **chili555 said:**
> 
* Assuming you are the administrator of all this, keep a ledger of machine names, addresses and other details such as, perhaps, location, service history, update history, etc.


I think across all the answers I have a pretty solid understanding of what I need to set where. But out of curiosity why keep a ledger like that? No background in administration on a production level.

---

### Post by SeijiSensei on 2016-12-31
I think you're much better off using DHCP reservations if you have multiple machines you want to recognize by name.  Most modern routers will also provide a DNS server with the forward and reverse resolution tables built from the DHCP requests.  Make sure each server has a hostname (run the "hostname" command from the terminal to make sure).  The DHCP client script announces the machine with the string that reports; it is stored in /etc/hostname.  If for some reason that isn't working correctly for you, edit the "send host-name" directive in /etc/dhcp/dhclient.conf to use a static hostname as that file illustrates.

---

### Post by chili555 on 2016-12-31
> But out of curiosity why keep a ledger like that?Most basically, when you are away from the perhaps headless server and want to access it by ftp or ssh and ask yourself, "Now what was the IP address of the server I set? 110? 120? 150? Drat, how can I figure it out?? Hmmmm, I shoulda kept a list."

---

