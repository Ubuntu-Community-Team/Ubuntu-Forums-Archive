---
title: "Ubuntu 20.04.2 LTS: UDP multicast: AddMembership failed"
date: 2021-04-28
forum: Networking &amp; Wireless
---

### Post by nimeni-on on 2021-04-28
Turned out that on case of tried UDP Multicast/AddMemership, it fails.
In case of Ubuntu 18.04 LTS everything fine ( .NET Core 3.1).

I even tried to lower kernel 5.8.0-49 --> 5.4.0-71-lowlatency, but didn't help.

My network shows as :
-------------------------------

~# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether b8:cb:29:b1:56:13 brd ff:ff:ff:ff:ff:ff
    inet 192.168.42.200/24 brd 192.168.42.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::bacb:29ff:feb1:5613/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether b8:cb:29:b1:56:14 brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether b4:96:91:a0:a1:d4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.41.200/24 brd 192.168.41.255 scope global eth2
       valid_lft forever preferred_lft forever
5: eth3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether b4:96:91:a0:a1:d5 brd ff:ff:ff:ff:ff:ff

So as the lo-interface is index #0, eth0 is #1 and so on.
But as below shown, interface is said to be #0 (which is "lo")

 Listener Task Start: failed : SetSocketOption: SocketOptionName.AddMembership, _mcastGroup '239.0.1.249-->192.168.42.220' Interface #0 Error : System.Net.Sockets.SocketException (0xFFFFFFFF): Bad value for ai_flags
   at System.Net.Sockets.Socket.UpdateStatusAfterSocketErrorAndThrowException(SocketError error, String callerName)
   at System.Net.Sockets.Socket.SetMulticastOption(SocketOptionName optionName, MulticastOption MR)
   at System.Net.Sockets.Socket.SetSocketOption(SocketOptionLevel optionLevel, SocketOptionName optionName, Object optionValue)
   at Grabber.UdpMulticastListener.Start(CancellationToken cancellationToken)


When I (after created MulticastGroup) changed interface index to #1 describing correctly "eth0", it did pass over, but still, not joined to MultiCast Group.

So this seems to relate to Ubuntu Distro as by code is working on about 6 different computers running Ubuntu 18.04 LTS.
There seems to be discussion about kernel 5.8 and Networking problems but not seen others UDP-multicast related.

-niilo

---

### Post by nimeni-on on 2021-04-28
[SOLVED] Reason behind this - and also solution was to fix structure of "[COLOR=#000000]MulticastOption" [/COLOR]by self.
Originally that's working on Ubuntu 18.04 LTS but now failing - dunno in which side
[COLOR=#000000][/COLOR]https://docs.microsoft.com/en-us/dotnet/api/system.net.sockets.multicastoption?view=net-5.0
-----------
            _mcastGroup = new MulticastOption(IPAddress.Parse("239.0.1.249"), IPAddress.Parse("192.168.42.200"));


            _mcastGroup.InterfaceIndex = 2; // Solution: insert manually after constructor as above in my question, index of "eth0" is just #2
            UdpListener = new UdpClient();
            ....................
            UdpListener.Client.SetSocketOption(SocketOptionLevel.IP, SocketOptionName.AddMembership, _mcastGroup);
-----------

So the class constructor and engine behind need to fill addresses & index of interface, which it did not in Ubuntu 20.04 LTS

---

