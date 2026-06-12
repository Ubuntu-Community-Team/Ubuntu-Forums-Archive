---
title: "Ubuntu Server and Masquerading"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by stego_s_aurus on 2007-01-10
Greetings!

I have run into a problem which I cannot find any proper solution for:

When FTPing from my Windows box through my Ubuntu Dapper Internet Server to a machine outside of my LAN, I get this error returned when I attempt to get a file listing from the FTP server:

*500 I won't open a connection to 192.168.0.2 (only to 216.117.xxx.xxx)*

192.168.0.2 is my LAN IP address.
216.117.xxx.xxx is my Ubuntu servers Internet address.

I am using the following commands on the Ubuntu Server to allow my computer to masquerade my Internet connections to the outside world:

[I]echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.0.2 -o eth1 -j MASQUERADE
iptables -I FORWARD -j ACCEPT -s 192.168.0.2[/I]

eth1 (the NIC connected to the ISP) is configured with the IP address of 216.117.xxx.xxx
eth0 (the NIC connected to the LAN) is configured with the IP address of 192.168.0.1
My Windows machine uses 192.168.0.1 as its gateway and DNS.
The LAN is set up with Static IP addresses to make life easy.

I am able to browse the web just fine with this configuration, but it seems that my packets are not being masqueraded properly.

Might anyone see something in the commands that I'm using that I am incorrectly setting?

](*,) :confused:

---

### Post by kipeloff on 2007-01-11
Masquerade rule is correct (as it is standard masquerade rule).
You need to check that FTP client is using passive connection settings.

---

### Post by stego_s_aurus on 2007-01-26
Thanks! That worked!!

---

