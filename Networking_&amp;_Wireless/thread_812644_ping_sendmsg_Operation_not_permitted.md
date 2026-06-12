---
title: "ping: sendmsg: Operation not permitted"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by mewt on 2008-05-30
Hi Everyone, 

I'd like to achieve a particular setup for my network at work however I'm encountering several problems. My main aim is to be connected to 2 networks at the same time from my laptop (wireless to internet dmz and 1 to internal cisco call manager system)

To achieve this I set up eth0 as 192.168.30.222/24 manually from network settings menu, while I connected to our wireless dmz through wicd with address 10.40.1.31. 

However my wireless connection seems to take precedence over anything and when i try to ping my call manager server I get the following: 

mewt@tehgraveyard:~$ ping 192.168.30.1
PING 192.168.30.1 (192.168.30.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted


my routing table looks like this: 

mewt@tehgraveyard:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.39.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.184.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
10.40.1.0       0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.40.1.254     0.0.0.0         UG    0      0        0 wlan0


All traffic through 192.168.30.0/24 should pass from eth0 as gateway however this isnt happening :S

Any ideas ?

Thanks

Mewt

---

### Post by SpaceTeddy on 2008-05-30
> **mewt said:**
> mewt@tehgraveyard:~$ ping 192.168.30.1
PING 192.168.30.1 (192.168.30.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

this looks like your machine is not allowed to send pings. this would mean that icmp pakets on are forbidden to be send via iptables. Please check with this command if you have any iptables rules loaded:
```
sudo iptables -L -vnx
```
If so, make sure your firewall is acctually allowing pings.

> **mewt said:**
> All traffic through 192.168.30.0/24 should pass from eth0 as gateway however this isnt happening :S

Any ideas ?
yes. two acctually :)

1.) did you enable ip_forwarding on that machine. Without the kernel allowing passthrough traffic, there is no way your computer can act as a gateway. you can check if it is enabled via this command
```
sudo sysctl net.ipv4.ip_forward
```
of the answer is 0, then overwrite it with this command
```
sudo sysctl -w net.ipv4.ip_forward=1
```


2.) is your internal network (192.168.30.0 ?) known upstream from your machine ? in other words, are the pakets able to find their way BACK to you ? if not, you might need to masquerade the network on your machine so the internet can send the pakets back to it.
you can check if any masquerading is set via this command
```
sudo iptables -L --table nat -vnx
```
if the POSTROUTING is empty, then i'd suspect you need to setup masquerading. Here is a sample command to enable it:
```
sudo iptables -A POSTROUTING --table nat -o %nic -j MASQUERADE
```
make sure you replace %nic the name of the network card that is connected to the internet. 

ok, those were my ideas... 

hope it helps :)

---

