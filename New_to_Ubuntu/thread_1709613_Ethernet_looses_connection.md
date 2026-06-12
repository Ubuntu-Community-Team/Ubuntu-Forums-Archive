---
title: "Ethernet looses connection"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Zeke501 on 2011-03-18
Hi

I have a strange problem, when I connect my notebook directly to a switch, my network link goes up and down none-stop. When I connect it to a normal point that is patched to the same switch it works. I have tried this on different switches, Netgear, Linksys, Trendnet and cisco, 100MB and 1000MB. Not much I can see in /var/log/messages. Only the following:

ar 18 12:58:58 zeke-nb kernel: [  255.131426] e1000e: eth0 NIC Link is Down
Mar 18 12:59:04 zeke-nb kernel: [  261.350168] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX

Thanking you in advance

Zeke

---

### Post by tkelito on 2011-03-18
DHCP or Static IP?

If you are using DHCP I would suggest attempting to assign a static just for testing purposes to see if the network will stay connected.

The file to edit in terminal for Static IPs would look like this:

Back up your interfaces file first using:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.`date +%F~%T` 
```

Then:

```
gksudo gedit /etc/network/interfaces
```

Insert this code into the new interfaces file where xxx is the specific info of your network.  Forgive me for assuming the prefix is 192.168.

```

# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.xxx.xxx
gateway 192.168.xxx.xxx
netmask 255.255.255.0
network 192.168.xxx.0
broadcast 192.168.xxx.255

```

---

