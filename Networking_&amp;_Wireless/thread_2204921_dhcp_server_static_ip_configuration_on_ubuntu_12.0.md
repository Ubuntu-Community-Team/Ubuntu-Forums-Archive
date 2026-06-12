---
title: "dhcp server static ip configuration on ubuntu 12.04 for multiple interfaces issue"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by venkatesh484 on 2014-02-11
Hello All,

I have configured DHCP server on ubuntu 12.04 and updated static ip's for multiple interfaces but client host able to get dhcp ip for only one interface(eth0) and not getting ips for remaining interfaces(eth1 and eth2).

Could you please help me?

Server Configuration:
#####################################################
```
ddns-update-style none;
log-facility local7;


subnet 10.xx.xx.0 netmask 255.255.255.0 {


        option routers                  10.xx.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        10.xx.1.255;
        option domain-name-servers      10.xx.xx.32;


        default-lease-time 86400;
        max-lease-time 86400;


        host dhcptest1-eth0 {
                hardware ethernet 00:50:56:xx:xxx;
                fixed-address 10.82.xx.xx;
        }
}


subnet  192.168.1.0 netmask 255.255.255.0 {


        option routers                  192.xxx.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        192.xxx.1.255;
        option domain-name-servers      10.82.xx.xx;


        default-lease-time 86400;
        max-lease-time 86400;


        host dhcptest1-eth1 {
                hardware ethernet 00:50:56:xx:xx:xx;
                fixed-address 192.168.x.xxx;
        }
}


subnet  172.16.1.0 netmask 255.255.255.0 {


        option routers                  172.xx.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        172.xx.x.255;
        option domain-name-servers      10.82.xx.xx;


        default-lease-time 86400;
        max-lease-time 86400;


        host dhcptest1-eth2 {
                hardware ethernet 00:50:56:xxxx;
                fixed-address 172.16.x.xxx;
        }
}

Client Configuration

root@dhcptest1:~# cat /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
```

---

