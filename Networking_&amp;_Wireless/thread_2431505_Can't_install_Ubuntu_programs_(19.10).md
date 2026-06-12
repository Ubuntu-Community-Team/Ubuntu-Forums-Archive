---
title: "Can't install Ubuntu programs (19.10)"
date: 2019-11-17
forum: Networking &amp; Wireless
---

### Post by lcm-3 on 2019-11-17
When I attempt to install Ubuntu Software, I get the following message:

Unable to download updates: internet access was required but wasn't available

However, I'm using that connection to post this thread. Further I can issue the following command successfully:

**[FONT=courier new]sudo apt-get update[/FONT]**

I set a static IP using netplan ([FONT=courier new]/etc/netplan/01-network-manager-all.yaml[/FONT])

[FONT=courier new]# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
     dhcp4: no
     addresses: [192.168.10.26/24]
     gateway4: 192.168.10.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4][/FONT]
 

After this change I did [FONT=courier new][B]sudo netplan apply

[/B][/FONT][FONT=courier new][FONT=arial]There is no Network settings at the top right of the desktop.

[FONT=courier new]ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether f4:6d:04:13:b4:2a brd ff:ff:ff:ff:ff:ff
3: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 68:05:ca:66:66:05 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.26/24 brd 192.168.10.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::6a05:caff:fe66:6605/64 scope link 
       valid_lft forever preferred_lft forever[/FONT][/FONT]

[/FONT][B][FONT=courier new]nmcli -t -f RUNNING general
running
nmcli -t -f STATE general
disconnected[/FONT][/B][FONT=courier new]

[FONT=arial]How can I correct this problem?[/FONT]

[/FONT]

---

### Post by messiaslg on 2019-12-16
executa o seguintes comandos:




sudo rm /etc/netplan/*.yaml


Crie um novo arquivo:


sudo vi /etc/netplan/01-network-manager-all.yaml


Adicione o seguinte:


# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager




Depois de fazer essas alterações, faça:


sudo netplan generate
sudo netplan apply
sudo service network-manager restart


Estava com o mesmo incidente seu e isto resolveu.


Abs.

---

