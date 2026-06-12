---
title: "Strange bridge behaviour, need sugestions"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by miguelcastilho on 2014-02-14
I have this 3 machines with this setup:
 Computer1----Computer with Ubuntu 12.04-----Computer2
 
Computer1 have IP 192.168.10.1 and Computer2 have 192.168.10.10. 
My computer with Ubuntu have 2 ethernet interfaces. I want to create a bridge in Ubuntu so Computer1 and Computer2 can talk to each other.

I have created a bridge in Ubuntu with

```
sudo ifconfig eth0 0.0.0.0 down
sudo ifconfig eth1 0.0.0.0 down
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig br0 up
sudo ifconfig eth0 promisc up
sudo ifconfig eth1 promisc up
```
The command "brctl showstp br0" shows me that the state of eth0 and eth1 is forwarding. Then I start tshark in bridge with

```
sudo tshark -i br0

```If in Computer2 I try to ping Computer1 I get

```
ARP 60 Who has 192.168.10.1? Tell 192.168.10.10

```In the bridge I get the ARP Request from Computer2 but I don't see ARP Reply from Computer1

When I run the tshark at Computer1 gets this

```
ARP 60 Who has 192.168.10.1? Tell 192.168.10.10
ARP 42 192.168.10.1 is at XX:XX:XX:XX:XX:XX (mac hidden)

```With this I see that ARP gets passed through the brige, Computer1 receives the ARP and sends the reply but that reply don't go through the bridge.

Any ideas???

Thanks

---

