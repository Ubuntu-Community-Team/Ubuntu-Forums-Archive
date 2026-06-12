---
title: "Share internet from one wired network to another"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by Paloseco on 2017-12-05
I have a PCI ethernet (physical RJ45) on my notebook, which has internet access through the router.
The other ethernet adapter is a USB dongle, which connects to a home computer with no other internet access.

I want to use my notebook as a man-in-the-middle router for my home computer. How can I do that with ubuntu?

[IMG]http://oi63.tinypic.com/i2k2me.jpg[/IMG]

Internet <--> Router (192.168.0.1) <--> PCI ethernet (192.168.0.25) <--> Notebook <--> USB ethernet <--> Offline computer

```
ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 4c:cb:6a:40:3d:44 brd ff:ff:ff:ff:ff:ff
4: wlp1s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 8c:c6:a0:12:21:db brd ff:ff:ff:ff:ff:ff
6: enx000ec6c4403c: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:0b:c1:c4:40:1c brd ff:ff:ff:ff:ff:ff

```

---

### Post by Kirk Schnable on 2017-12-06
The easiest would probably be to create a separate private network on a different IP range for the small network between the two computers, and set up iptables masquerade NAT.

This may help you get started:  [https://www.revsys.com/writings/quicktips/nat.html](https://www.revsys.com/writings/quicktips/nat.html)

---

### Post by Paloseco on 2017-12-06
> **Kirk Schnable said:**
> The easiest would probably be to create a separate private network on a different IP range for the small network between the two computers, and set up iptables masquerade NAT.

This may help you get started:  [https://www.revsys.com/writings/quicktips/nat.html](https://www.revsys.com/writings/quicktips/nat.html)

Can't it be done with the gui?

I've tried your command, but it does not work straightaway. It's mandatory to set a static IP to the shared network and do the same on the other computer.

On the computer that is connected to the internet (uses Linux):
```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo /sbin/iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo /sbin/iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo sudo ifconfig eth1 192.168.127.1 netmask 255.255.255.0
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```

On the other computer which is offline, using Windows CMD or Command Prompt (uses Windows 10):
```
netsh interface ipv4 set address name="Ethernet" static 192.168.127.2 255.255.255.0 192.168.127.1
netsh interface ipv4 set dns name="Ethernet" static 8.8.8.8
```

To have Windows 10 with dynamic IP connecting automatically, probably I will need some dhcp server on eth1, which I don't know how to do.

Sources:

[LIST]
[*][How to Change Your Computer’s IP Address From the Command Prompt]("https://www.howtogeek.com/103190/change-your-ip-address-from-the-command-prompt/")
[*][Change IP Address and DNS Servers using the Command Prompt]("https://helpdeskgeek.com/networking/change-ip-address-and-dns-servers-using-the-command-prompt/")
[*][How to Change Your IP Address Using PowerShell]("https://www.howtogeek.com/112660/how-to-change-your-ip-address-using-powershell/")
[*][Use PowerShell to Configure Static IP and DNS Settings]("https://blogs.technet.microsoft.com/heyscriptingguy/2012/02/28/use-powershell-to-configure-static-ip-and-dns-settings/")
[/LIST]

---

### Post by Paloseco on 2017-12-09
New tutorial:

[[HOWTO] Share internet to another computer serving IP and DNS automatically]("https://ubuntuforums.org/showthread.php?t=2379769")

---

