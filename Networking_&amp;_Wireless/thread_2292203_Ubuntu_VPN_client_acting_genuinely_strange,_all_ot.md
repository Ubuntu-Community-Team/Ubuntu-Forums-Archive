---
title: "Ubuntu VPN client acting genuinely strange, all others work."
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by Matthew_Struble on 2015-08-26
Okay, so: I have a VPN service set up elsewhere which is and has been working for extended periods of time and still continues to work. In addition, all of it's clients are working perfectly... with exception to one of them running Ubuntu. (The server itself and other clients are Ubuntu as well). The computer in question has a dual-boot between Windows 8.1 and Ubuntu 14.04. Whilst in Windows the VPN works perfectly. When in Ubuntu, however, OpenVPN begins active massively strange.

The connection succeeds perfectly and the client and server begin communication with one another normally and the tun0 adapter (or tap0, I've tried both) appear. However, all DNS resolutions fail and pings to outside addresses time out. The strange bit, however, is that I can maintain a Google Hangouts call (non-standard tests. :F) *while* the VPN client that cannot DNS resolve or access IP addresses is running, so long as I joined before starting the VPN client. I can also receive messages through Hangouts, but not send any (these result in a "Sending Failed" error).

Here's some net info both with the VPN client running (openvpn service is started) and not:
[TABLE="width: 1024, align: left"]
[TR]
[TD="align: center"]**OpenVPN Stopped**[/TD]
[TD="align: center"]**OpenVPN Running**[/TD]
[/TR]
[TR]
[TD]```
$ ifconfig tun0
tun0: error fetching interface information: Device not found

```[/TD]
[TD]```
$ ifconfig tun0
Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.4  P-t-P:10.8.0.4  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1946 (1.9 KB)

```[/TD]
[/TR]
[TR]
[TD]```
$ ping 10.8.0.1
PING 10.8.0.1 (10.8.0.1) 56(84) bytes of data.


--- 10.8.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

```[/TD]
[TD]```
$ ping -c3 10.8.0.1
PING 10.8.0.1 (10.8.0.1) 56(84) bytes of data.
64 bytes from 10.8.0.1: icmp_seq=1 ttl=64 time=28.5 ms
64 bytes from 10.8.0.1: icmp_seq=2 ttl=64 time=37.0 ms
64 bytes from 10.8.0.1: icmp_seq=3 ttl=64 time=35.9 ms


--- 10.8.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 28.551/33.847/37.092/3.782 ms

```[/TD]
[/TR]
[TR]
[TD]```
$ ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_seq=1 ttl=47 time=168 ms
64 bytes from 91.189.94.12: icmp_seq=2 ttl=47 time=238 ms
64 bytes from 91.189.94.12: icmp_seq=3 ttl=47 time=164 ms


--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 164.941/190.410/238.263/33.863 ms

```[/TD]
[TD]```
$ ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

```[/TD]
[/TR]
[TR]
[TD]```
$ ping -c3 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=47 time=171 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=47 time=161 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=47 time=164 ms


--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 161.689/165.737/171.460/4.174 ms

```[/TD]
[TD]```
$ ping ubuntuforums.org
ping: unknown host ubuntuforums.org

```[/TD]
[/TR]
[/TABLE]
And here's the config (/etc/openvpn/client.conf):
```
clientdev tun
proto udp
remote vevox.io 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
comp-lzo
verb 6
mute 20

```

What's going on? This was working earlier today and *fresh install*&#8203; of Ubuntu did not help.

---

