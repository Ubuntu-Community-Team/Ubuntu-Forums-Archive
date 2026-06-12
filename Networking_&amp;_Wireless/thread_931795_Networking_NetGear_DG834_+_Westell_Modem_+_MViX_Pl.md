---
title: "Networking: NetGear DG834 + Westell Modem + MViX Player"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2008-09-27
Hi, all.

I have a Netgear DG834G Wireless DSL router that I had been using for over a year, but the modem side o it failed a while ago...

So I went back to using the old Westell 6100 that Verizon supplied me when I started my subscription.

SWMBO recently bought a Mac, and wants to use the internet connection, so I decided to resurrect the Netgear DG834G just as a router, in order to share the connection.

So, I took two lengths of ethernet cable:
[LIST]
[*]the first connects my computer to the DG834G,
[*]the second connects the DG834G to the Westell 6100 modem.
[/LIST]

Success! I have wired internet connectivity to the internet.

BUT if I want to change any parameters on the DG834G, I have to disconnect the modem and reboot. Then I can point a browser at 192.168.0.1 to get the web interface on the DG834G.

At the moment, while I have the computer <-> DG834G <-> Westell 6100 setup, 192.168.1.1 is the Westell 6100 modem, and I can't view the DG834 (which should be 192.168.0.1)...

Any idea how I should set things up on the DG834G so I could see both devices at the same time?

Also, I recently got an MViX media player, and I'd like to be able to copy files to it over the wireless network. Ive been following the instructions in the manual, but it doesn't go into much detail...

I seem to have done everything I need to, and if I can ping the IP address I assigned.

```
$ ping -c 5 192.168.1.5
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
64 bytes from 192.168.1.5: icmp_seq=1 ttl=64 time=1.84 ms
64 bytes from 192.168.1.5: icmp_seq=2 ttl=64 time=2.22 ms
64 bytes from 192.168.1.5: icmp_seq=3 ttl=64 time=1.82 ms
64 bytes from 192.168.1.5: icmp_seq=4 ttl=64 time=1.83 ms
64 bytes from 192.168.1.5: icmp_seq=5 ttl=64 time=3.25 ms

--- 192.168.1.5 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 1.820/2.193/3.255/0.553 ms

```

But how can I connect to this device to upload files to it?

K.

---

