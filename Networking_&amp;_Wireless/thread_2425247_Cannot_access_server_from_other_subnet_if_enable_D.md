---
title: "Cannot access server from other subnet if enable DHCP on server 18.04"
date: 2019-08-22
forum: Networking &amp; Wireless
---

### Post by navysu on 2019-08-22
subnet1: 192.168.1.0/24
subnet2: 192.168.2.0/24
Server IP: 192.168.1.20
Client IP: 192.168.2.100

If server is configured as static ip, there is no problem to access the server from the client. 
If the server is configured as DHCP, most time the client cannot ping the server. Sometime it works but I cannot reproduce it.
If the server is configured as DHCP and I ran command *[COLOR=#0000cd]sudo dhclient -v ens9 [/COLOR], *there is no problem to access the server from the client.

Server info:
[COLOR=#800080]$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic[/COLOR]

Configuration file:
[COLOR=#800080]$ cat /etc/netplan/50-cloud-init.yaml 
network:
  renderer: networkd
  ethernets:
    ens9:
      dhcp4: true
      dhcp-identifier: mac
  version: 2[/COLOR]

Anyone has an idea about it?

Thanks

---

### Post by SeijiSensei on 2019-08-22
Servers should have static addresses. Don't use DHCP.

---

