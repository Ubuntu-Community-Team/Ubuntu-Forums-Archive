---
title: "IPsec tunnel mode"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by ezacon on 2008-06-06
I want to connect two branch offices with an ipsec tunnel througt internet. In both branches, i have an ubuntu server with 2 nics. One nic is connected to internet with a static public ip an the other is connected to branch office lan. Both ubuntu server gateways uses shorewall for firewall config. One is 8.04 and other is 7.10
I have configured ipsec-tools, racoon and shorewall with the document [http://www.shorewall.net/3.0/IPSEC-2.6.html](http://www.shorewall.net/3.0/IPSEC-2.6.html)
Mi scenario is:
Network A: 
Private net 172.25.11.0/24
Net A gateway 172.25.11.201
Public internet IP: xxx.xxx.xxx.xxx

Network B:
Private net 192.168.0.0/24
Net B Gateway 192.168.0.2
Public internet IP: yyy.yyy.yyy.yyy

The problem is: The ipsec connection is working and i can ping from any machine in net a the net b gateway and vice-versa, but i cant reach any other ip in the remote private net. From one network, i can access the other branch office server but all other devices connected to that network are unreachable.

My config files are:

Side A:

/etc/ipsec-tools.conf
flush;
spdflush;
spdadd 192.168.0.0/24   172.25.11.0/24   any -P in  ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd 192.168.0.0/24   xxx.xxx.xxx.xxx/32  any -P in  ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd yyy.yyy.yyy.yyy/32 xxx.xxx.xxx.xxx/32  any -P in  ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd yyy.yyy.yyy.yyy/32 172.25.11.0/24   any -P in  ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd 172.25.11.0/24   192.168.0.0/24   any -P out ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd 172.25.11.0/24   yyy.yyy.yyy.yyy/32 any -P out ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd xxx.xxx.xxx.xxx/32  192.168.0.0/24   any -P out ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd xxx.xxx.xxx.xxx/32  yyy.yyy.yyy.yyy/32 any -P out ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;

/etc/racoon/racoon.conf
path pre_shared_key "/etc/racoon/psk.txt";
log notify;

listen
{
        isakmp xxx.xxx.xxx.xxx;
        strict_address;
}
remote yyy.yyy.yyy.yyy
{
        exchange_mode main;
        send_cr off;
        send_cert off;
        proposal {
                encryption_algorithm blowfish;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group 2;
        }
}

sainfo address 172.25.11.0/24 any address 192.168.0.0/24 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address xxx.xxx.xxx.xxx/32 any address 192.168.0.0/24 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address xxx.xxx.xxx.xxx/32 any address yyy.yyy.yyy.yyy/32 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address 172.25.11.0/24 any address yyy.yyy.yyy.yyy/32 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}


Side B:

/etc/ipsec-tools.conf
flush;
spdflush;
spdadd 192.168.0.0/24   172.25.11.0/24   any -P out ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd 192.168.0.0/24   xxx.xxx.xxx.xxx/32  any -P out ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd yyy.yyy.yyy.yyy/32 xxx.xxx.xxx.xxx/32  any -P out ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd yyy.yyy.yyy.yyy/32 172.25.11.0/24   any -P out ipsec esp/tunnel/yyy.yyy.yyy.yyy-xxx.xxx.xxx.xxx/require;
spdadd 172.25.11.0/24   192.168.0.0/24   any -P in  ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd 172.25.11.0/24   yyy.yyy.yyy.yyy/32 any -P in  ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd xxx.xxx.xxx.xxx/32  192.168.0.0/24   any -P in  ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;
spdadd xxx.xxx.xxx.xxx/32  yyy.yyy.yyy.yyy/32 any -P in  ipsec esp/tunnel/xxx.xxx.xxx.xxx-yyy.yyy.yyy.yyy/require;


/etc/racoon/racoon.conf
path pre_shared_key "/etc/racoon/psk.txt";
log notify;

listen
{
        isakmp yyy.yyy.yyy.yyy;
        strict_address;
}

remote xxx.xxx.xxx.xxx
{
        exchange_mode main;
        send_cr off;
        send_cert off;
        proposal {
                encryption_algorithm blowfish;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group 2;
        }
}
sainfo address 192.168.0.0/24 any address 172.25.11.0/24 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address yyy.yyy.yyy.yyy/32 any address 172.25.11.0/24 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address yyy.yyy.yyy.yyy/32 any address xxx.xxx.xxx.xxx/32 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

sainfo address 192.168.0.0/24 any address xxx.xxx.xxx.xxx/32 any
{
        pfs_group 2;
        encryption_algorithm blowfish;
        authentication_algorithm hmac_sha1, hmac_md5;
        compression_algorithm deflate;
}

---

### Post by peitschie on 2008-06-06
Hi.  Firstly I don't have a solution for your current problem.  I ran into the same issue myself, and eventually figured out it was a router somewhere between the two locations that was stuffing up the IPsec tunnel.

What I eventually did was replace the whole outfit with an OpenVPN setup.  This has both linux + windows clients.  3 days screwing around with IPsec without any joy (I could connect from inside the lan, but not outside the lan?!), and I had OpenVPN up and running within an hour.  This may not suit your requirements, but I thought I'd suggest it just in case you hadn't heard of OpenVPN :)

You can find open vpn here: [http://openvpn.net/](http://openvpn.net/)
There are some good tutorials on that site.

---

### Post by ezacon on 2008-06-13
Thx.
In fact, i was using openvpn before switching to ipsec.
The problem is that i need to pass low level trafic, so openvpn is not an option.
My problem is not related to routing problems, my ubuntu servers are routers with a dsl modem giving the public internet address to the external nics.

Still trying...

---

