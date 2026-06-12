---
title: "[ask] Fails to bring up eth2"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by thougi on 2013-10-25
hai guys im new in ubuntu server 
today im instal ubuntu 12.04 LTS
this topology in  my network 

modem 1
(192.168.1.1)
              -----------Router ubuntu------LAN-----cleint 
modem 2                  (192.168.3.254)
(192.168.2.1)

setting ip in ubuntu server

auto eth0
iface eth0 inet static
    address 192.168.3.254
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255

auto eth1
iface eth1 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.3.255
    gateway 192.168.1.1

auto eth2
iface eth2 inet static
    address 192.168.2.2
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1

setting dns server
8.8.8.8
202.134.1.10

after reboot cant  ping example to google.com
then im restart  network with command 
/etc/init.d/networking restart
have  eror
running /etc/init.d/networking restart is deprecated beacouse it may not enable again some interfaces
reconfiguring network interfaces...
sshstop/waiting
ssh start/running,process 1679
ssh stop/waiting
ssh start/running,process 1724
RTNETLINK Answers :file ezist
failed to bring up eth2

how to fix this problem

---

### Post by tenmoi on 2013-10-25
auto eth2
iface eth2 inet static
address 192.168.2.2
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.3.255 > 192.168.[COLOR="#FF0000"]2[/COLOR].255
gateway 192.168.2.1

---

### Post by thougi on 2013-10-25
sory for my mistake i worng typing in forum 
alrady fix that 

how to fix that problem

---

### Post by tenmoi on 2013-10-26
Maybe, you'll find the answer here.
[http://askubuntu.com/questions/313236/rtnetlink-answers-file-exists-configure-interface](http://askubuntu.com/questions/313236/rtnetlink-answers-file-exists-configure-interface)

And if the above link doesn't help. You should take a look at /etc/udev/rules.d/70-persistent-net.rules. Find if there are two instances of eth2. Remove one of them and reboot. Or reload your network.

---

