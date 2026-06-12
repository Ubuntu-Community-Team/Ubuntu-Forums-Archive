---
title: "Help tweaking strongSwan VPN server"
date: 2020-04-07
forum: Networking &amp; Wireless
---

### Post by pssturges on 2020-04-07
Hi,

I'm trying to set up strongSwan VPN server on my home "server". Basically, I want to be able to securely access all the bits & pieces on my home network whilst away from it.

I'm running my mythbuntu box as a quasi home server. It only has one network port which is connected to my modem router, but I have the DHCP server running in mythbuntu. It hands out addresses on my local network in the range 192.168.0.1 - 192.168.0.200. Most devices on the network have predefined addresses.

I've set up strongSwan using this guide:
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ikev2-vpn-server-with-strongswan-on-ubuntu-18-04-2](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ikev2-vpn-server-with-strongswan-on-ubuntu-18-04-2)

Setup was quite uneventful. I can successfully get clients to connect and they can access other devices on my home network.

My issues are:

1) Nothing seems to get discovered by clients. Samba, airplay, DLNA etc
2) No internet on clients
3) Not sure how my DHCP server integrates with this? It seems to be allocating the same IP to all remote clients ie 192.168.0.1. I'd like it to hand out the local IPs for the remote clients, but not sure if that needs any configuration.

Config files below.

Thanks in advance for any help.


```
/etc/ipsec.conf
config setup
    charondebug="ike 1, knl 1, cfg 0"
    uniqueids=no

conn ikev2-vpn
    auto=add
    compress=no
    type=tunnel
    keyexchange=ikev2
    fragmentation=yes
    forceencaps=yes
    dpdaction=clear
    dpddelay=300s
    rekey=no
    left=%any
    leftid=xxx.xxx.xx.xx
    leftcert=server-cert.pem
    leftsendcert=always
    leftsubnet=0.0.0.0/0
    right=%any
    rightid=%any
    rightauth=eap-mschapv2
    rightsourceip=192.168.0.1/200
    rightdns=8.8.8.8,8.8.4.4
    rightsendcert=never
    eap_identity=%identity

```


```
# /etc/dhcp/dhcpd.conf created Tue 10 Mar 12:12:17 AEDT 2020 by updatedhcp script
default-lease-time 3600;
allow unknown-clients;
max-lease-time 3600;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option netbios-name-servers 192.168.0.10;
option domain-name-servers 192.168.0.1;
option domain-name "home";
subnet 192.168.0.0 netmask 255.255.255.0 {
    option domain-name "home";
	host modem {
		hardware ethernet xx:xx:xx:xx:xx:xx;
		fixed-address 192.168.0.1;
		}
	host frontap {
		hardware ethernet xx:xx:xx:xx:xx:xx;
		fixed-address 192.168.0.2;
		}
	host kitchenap {
		hardware ethernet xx:xx:xx:xx:xx:xx;
		fixed-address 192.168.0.3;
		}
	host livingroom-atv {
		hardware ethernet xx:xx:xx:xx:xx:xx;
		fixed-address 192.168.0.4;
		}
.
.
.
.
range 192.168.0.1 192.168.0.200;
}

```

---

