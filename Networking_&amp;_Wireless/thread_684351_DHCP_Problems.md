---
title: "DHCP Problems"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by tjb_15 on 2008-02-01
I can't get DHCP to start. I keep getting this message

```
travis@ubuntu:~$ sudo /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was: 
Address range 192.168.1.20 to 192.168.1.40 not on net 192.168.0.0/255.255.255.0!
travis@ubuntu:~$ 

```
I'm trying to make a thin client server with LSTP but I can't get the DHCP to work.

Could some one help me make a dhcpd.conf?
Router: 192.168.1.1  ---- The routers dhcp is off 
Server: 192.168.1.102
Subnet: 255.255.255.0
Broadcast: 192.168.1.255

All of my other computers have static ip's from 192.168.1.100 - 192.168.1.102 and one on 192.168.1.200

I've been trying to get this to work for about 6 hours

---

### Post by HermanAB on 2008-02-01
Here you go.  File /etc/dhcpd.conf:

ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
        # default gateway
        option routers 192.168.1.1;
        option subnet-mask 255.255.255.0;

        option domain-name "example.com";

        # Change this to your DNS Server
        option domain-name-servers w.x.y.z;

        range dynamic-bootp 192.168.1.100 192.168.1.253;
        default-lease-time 21600;
        max-lease-time 43200;
}

---

### Post by Mithrilhall on 2008-02-01
Could you post the contents of your conf file?

---

### Post by tjb_15 on 2008-02-01
This is what I had

```


authoritative;



subnet 192.168.1.0 netmask 255.255.255.0 {

range 192.168.1.20 192.168.1.40;

option domain-name "example.com";

option domain-name-servers 192.168.1.1;

option broadcast-address 192.168.1.255;

option routers 192.168.1.1;

option subnet-mask 255.255.255.0;

option root-path "/opt/ltsp/i386/boot";

next-server 192.168.1.102;

filename "pxelinux.0";

}
```

No matter what I change it to I get the same error when i restart dhcp.

---

### Post by tjb_15 on 2008-02-01
I think i've gotten the DHCP working now the thin client computer says
```

Searching for server (DHCP).....
Me: 192.168.1.20, DHCP: 192.168.1.102, TFTP: 192.168.1.102, Gateway 192.168.1.1
No filename
<sleep>
<abort>
```
My dhcpd.conf
```
ddns-update-style none;
ddns-updates off;
option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;


authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    interface eth0;
    range 192.168.1.10 192.168.1.20;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
    option domain-name-servers 192.168.1.1;
    option T150 "/opt/ltsp/i386/boot/pxelinux.0";
}
```

---

### Post by tjb_15 on 2008-02-01
anyone?

---

### Post by tjb_15 on 2008-02-01
Heres my the stats from ltspadmin

```
ltspcfg v0.16            The Linux Terminal Server Project (http://www.LTSP.org)
[U]
Interface IP Address      Netmask         Network         Broadcast        Used [/U]
eth0      192.168.1.102   255.255.255.0   192.168.1.0     192.168.1.255   <-----

_Service    Installed   Enabled   Running   Notes  _                              
dhcpd      Yes         no        Yes       Version 3
tftpd      Yes         Yes       Yes       Has '-s' flag
portmapper Yes         Yes       Yes       
nfs        Yes         Yes       Yes       
xdmcp      Yes         Yes       Yes       gdm   Using: gdm
[U]
File                                Configured  Notes[/U]                           
/etc/hosts                          Yes         
/etc/hosts.allow                    Yes         
/etc/exports                        Yes         
/opt/ltsp-4.2/i386/etc/lts.conf     Yes         

Argument "(value of initdefault in /etc/inittab)" isn't numeric in printf at /usr/sbin/ltspcfg line 164, <STDIN> line 2.
Use of uninitialized value in printf at /usr/sbin/ltspcfg line 164, <STDIN> line 2.
Configured runlevel: 0         
   Current runlevel: 2         (output of the 'runlevel' command)

Installation dir...: /opt/ltsp-4.2

Press <enter> to return to the main menu... 

```

I don't know what the argument is?

---

### Post by tjb_15 on 2008-02-01
> **HermanAB said:**
> Here you go.  File /etc/dhcpd.conf:

ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
        # default gateway
        option routers 192.168.1.1;
        option subnet-mask 255.255.255.0;

        option domain-name "example.com";

        # Change this to your DNS Server
        option domain-name-servers w.x.y.z;

        range dynamic-bootp 192.168.1.100 192.168.1.253;
        default-lease-time 21600;
        max-lease-time 43200;
}

This didn't work

---

