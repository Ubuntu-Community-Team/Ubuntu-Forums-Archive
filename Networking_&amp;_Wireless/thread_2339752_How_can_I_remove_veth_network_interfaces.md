---
title: "How can I remove veth network interfaces?"
date: 2016-10-12
forum: Networking &amp; Wireless
---

### Post by enumag on 2016-10-12
My network menu is showing a loooong list of "Ethernet Network () device not managed" - see screenshot: [http://pasteboard.co/1pzxZfaUB.png](http://pasteboard.co/1pzxZfaUB.png)

When I go to terminal and run ```
ip link show
``` I get this long list:

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 18:5e:0f:1a:4a:64 brd ff:ff:ff:ff:ff:ff
3: br-4daba402e4d9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 02:42:35:c5:eb:e4 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:7f:c2:8f:88 brd ff:ff:ff:ff:ff:ff
5: br-c70188afa151: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 02:42:55:0d:fd:11 brd ff:ff:ff:ff:ff:ff
6: br-e550d71ad285: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 02:42:ba:4e:f7:4a brd ff:ff:ff:ff:ff:ff
7: br-f3dad8d94ee2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 02:42:b2:f2:ea:7e brd ff:ff:ff:ff:ff:ff
9: veth1060767@if8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 2a:e1:b1:22:db:6b brd ff:ff:ff:ff:ff:ff link-netnsid 1
11: veth8504b78@if10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 5e:c2:25:36:0e:a8 brd ff:ff:ff:ff:ff:ff link-netnsid 0
13: veth1b6de39@if12: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether 12:c3:7b:b5:73:6a brd ff:ff:ff:ff:ff:ff link-netnsid 22
15: veth0d46e95@if14: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether f2:e6:69:56:01:bb brd ff:ff:ff:ff:ff:ff link-netnsid 17
17: veth4767445@if16: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether 86:a1:a3:26:f9:e4 brd ff:ff:ff:ff:ff:ff link-netnsid 23
19: vethcc16653@if18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether 1a:e7:dd:66:87:4d brd ff:ff:ff:ff:ff:ff link-netnsid 3
21: vethcc35544@if20: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether 7e:4c:7e:d8:9f:83 brd ff:ff:ff:ff:ff:ff link-netnsid 6
23: veth060740a@if22: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether 82:1b:06:b9:a8:3c brd ff:ff:ff:ff:ff:ff link-netnsid 25
25: veth6a04a8c@if24: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether 1a:78:8d:bc:b2:a1 brd ff:ff:ff:ff:ff:ff link-netnsid 2
27: vethbd92582@if26: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 66:08:49:3f:a0:35 brd ff:ff:ff:ff:ff:ff link-netnsid 5
29: veth691802c@if28: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether 12:ed:9e:24:7f:ea brd ff:ff:ff:ff:ff:ff link-netnsid 7
31: veth9189533@if30: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether ca:8a:b8:1b:92:e2 brd ff:ff:ff:ff:ff:ff link-netnsid 16
33: veth5bf09e3@if32: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 66:80:95:da:22:ed brd ff:ff:ff:ff:ff:ff link-netnsid 19
35: vethc9f2166@if34: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether e6:d1:a7:b7:f1:a2 brd ff:ff:ff:ff:ff:ff link-netnsid 26
39: vethe52d7b0@if38: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 22:1d:64:2f:94:ac brd ff:ff:ff:ff:ff:ff link-netnsid 21
41: vethcfa49b7@if40: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether ca:58:f3:9d:4d:52 brd ff:ff:ff:ff:ff:ff link-netnsid 14
43: vethe0a2493@if42: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether 1e:05:ca:59:74:54 brd ff:ff:ff:ff:ff:ff link-netnsid 15
47: vethfd7cf93@if46: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether a2:3a:d4:62:42:00 brd ff:ff:ff:ff:ff:ff link-netnsid 10
49: vethf632746@if48: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether f2:d4:3b:86:7d:0a brd ff:ff:ff:ff:ff:ff link-netnsid 18
51: vethae53313@if50: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether ea:67:b8:9e:74:3a brd ff:ff:ff:ff:ff:ff link-netnsid 20
53: vethd49ef66@if52: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-4daba402e4d9 state UP mode DEFAULT group default 
    link/ether 46:ca:69:a3:8f:38 brd ff:ff:ff:ff:ff:ff link-netnsid 13
55: vethc78969c@if54: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e550d71ad285 state UP mode DEFAULT group default 
    link/ether b2:44:5f:6e:12:e3 brd ff:ff:ff:ff:ff:ff link-netnsid 24
57: veth56869b0@if56: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-f3dad8d94ee2 state UP mode DEFAULT group default 
    link/ether 9e:64:14:8d:1e:f2 brd ff:ff:ff:ff:ff:ff link-netnsid 11
59: vethb4eed8d@if58: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-c70188afa151 state UP mode DEFAULT group default 
    link/ether 5a:19:c6:04:b3:bc brd ff:ff:ff:ff:ff:ff link-netnsid 9
61: veth4d0184a@if60: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue master br-e550d71ad285 state DOWN mode DEFAULT group default 
    link/ether fe:23:4b:41:80:f9 brd ff:ff:ff:ff:ff:ff link-netnsid 8

```

Those virtual veth* interfaces are apparently the problem. They were apparently created by docker which didn't remove them because of some bug. How can I remove them manually?

---

### Post by Hadaka on 2016-10-12
Hi, I know nothing of docker or veth, i found this information and am
just passing it along to you, hope it helps.   have you tried ??
```
ip link delete <ifname>
```
[http://stackoverflow.com/questions/31989426/how-to-identify-orphaned-veth-interfaces-and-how-to-delete-them](http://stackoverflow.com/questions/31989426/how-to-identify-orphaned-veth-interfaces-and-how-to-delete-them)
from google search of "linux docker how to remove veth"
good luck

---

### Post by enumag on 2016-10-13
Yeah I did try that before posting here. No luck though. All the interfaces were back after reboot.

---

### Post by Hadaka on 2016-10-13
Hi, this info may help, give it a read, especially the cleanup for both methods
maybe this will give you some ideas.
[http://lxc.sourceforge.net/old/index.php/about/kernel-namespaces/network/configuration/](http://lxc.sourceforge.net/old/index.php/about/kernel-namespaces/network/configuration/)
good luck

---

### Post by enumag on 2016-11-08
Unfortunately it did not.

I found someone having the same problem here but without a solution :-(

[URL="http://askubuntu.com/questions/783543/remove-ethernet-network-device-not-managed-the-ubuntu-interface"]http://askubuntu.com/questions/783543/remove-ethernet-network-device-not-managed-the-ubuntu-interface
[/URL][http://askubuntu.com/questions/770068/hide-unmanaged-network-interfaces-in-ubuntu](http://askubuntu.com/questions/770068/hide-unmanaged-network-interfaces-in-ubuntu)

The same devices are listed by this command:

```

$ nmcli device
DEVICE           TYPE      STATE        CONNECTION         
br-4daba402e4d9  bridge    connected    br-4daba402e4d9    
br-c70188afa151  bridge    connected    br-c70188afa151    
br-e550d71ad285  bridge    connected    br-e550d71ad285    
br-f3dad8d94ee2  bridge    connected    br-f3dad8d94ee2    
docker0          bridge    connected    docker0            
enx00e04c42f943  ethernet  connected    Wired connection 1 
wlp2s0           wifi      unavailable  --                 
veth02d0d31      ethernet  unmanaged    --                 
veth091bce7      ethernet  unmanaged    --                 
veth13884b6      ethernet  unmanaged    --                 
veth18ae7f7      ethernet  unmanaged    --                 
veth2811f63      ethernet  unmanaged    --                 
veth29cf93d      ethernet  unmanaged    --                 
veth2af5ca0      ethernet  unmanaged    --                 
veth31c3c5a      ethernet  unmanaged    --                 
veth393bf17      ethernet  unmanaged    --                 
veth40b3a24      ethernet  unmanaged    --                 
veth424f5fd      ethernet  unmanaged    --                 
veth4478e44      ethernet  unmanaged    --                 
veth4d89f5a      ethernet  unmanaged    --                 
veth525fa50      ethernet  unmanaged    --                 
veth5ca8a7c      ethernet  unmanaged    --                 
veth61094dc      ethernet  unmanaged    --                 
veth67779b8      ethernet  unmanaged    --                 
veth6a50a6b      ethernet  unmanaged    --                 
veth8507eaf      ethernet  unmanaged    --                 
vethbfc9a32      ethernet  unmanaged    --                 
vethc283191      ethernet  unmanaged    --                 
vethc4e97de      ethernet  unmanaged    --                 
vethcb73d2e      ethernet  unmanaged    --                 
vethdf2b64b      ethernet  unmanaged    --                 
vethf1f34b4      ethernet  unmanaged    --                 
lo               loopback  unmanaged    --     

```

How can I remove them?

---

### Post by Hadaka on 2016-11-08
Ok, since i know nothing about how all this work, please help educate me.
if you ** ip link delete <ifname>** each of these links one at a time...
Do they all come back on reboot or just a new link with a new <ifname>
that wasnt on the list before??
Thanks.

---

### Post by enumag on 2016-11-09
When I run ip link delete <ifname> the interface is removed from the nmcli d table.

It turns out all their names change after reboot. Even those I did not remove. There are always 25 of them after reboot regardless if I deleted some or not.

---

### Post by Hadaka on 2016-11-09
Hi please see if...
```
sudo ip link delete veth* 
```
delets all 25 entries before a reboot.

*If that command does delete all 25 then do..
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo ip link delete veth*\nexit 0" | sudo tee -a /etc/rc.local
```
This will build the delete file in /etc/rc.local and run on every boot or restart sending
the command to delete the devices. Not the most elegant way to do this, but should work
untill you find the correct way or why these are being built.
boot and verify it worked
thanks.

---

### Post by enumag on 2016-11-22
Nope, it says 'Cannot find device "veth*"'. Besides it would only remove the devices from the nmcli device table but not from the network connections GUI.

---

