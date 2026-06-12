---
title: "ntpdate with VLANS"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by shuaibe on 2007-08-13
Hi,

I have a small network with a server and clients. I have setup NTP server on the server machines and configured the clients to sync themselves to it. So far it (ntp and ntpdate) works fine untill I added vlans. I added a vlan on both client and server with same vlan ID. The IP address of the vlan interface at the client belongs to the range of addresses that NTP servers allows. I can ping the server through the vlan interface of the client but ntpdate replies no suitable server for sync.
Using wireshark, I came to know that the NTP packets (with vlan tags) do reach the server but there is no reply by the server ?
Here are the details of my configs:

Server vlan interface address : **192.168.12.101**
Client vlan interface address: **192.168.12.1**
Server ntp.conf file:

[B]server 127.127.1.0
fudge 127.127.1.0 stratum 10
restrict 127.0.0.1 nomodify
restrict 192.168.12.0 mask 255.255.255.0 nomodify notrap[/B]

any suggestion what might be the problem ?

thank you for your time!

---

### Post by wirelessmonkey on 2007-08-13
Is the VLAN untagged on both switch interfaces?

---

