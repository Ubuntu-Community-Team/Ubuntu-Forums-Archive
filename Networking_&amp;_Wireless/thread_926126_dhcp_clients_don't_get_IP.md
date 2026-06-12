---
title: "dhcp clients don't get IP"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by marioquark on 2008-09-21
hi
i have a LTSP 5 system on edubuntu hardy.
there are 15 workstations.

my dhcp server gives static MAC-based IP addresses.
this is what happens:

- the workstations make DHCPREQUEST
- the server makes the DHCPOFFERs
- SOME WORKSTATIONS ACK after many repeated offers, other worlstations
don't ACK at all! (syslog is below...)

my firewall is off...
can anyone tell me something about this?  :( 
thanks
quark





some of my syslog:
```
$ cat some_syslog.txt |grep dhcp
Sep 13 11:43:23 continuity dhcpd: DHCPDISCOVER from 00:50:ba:bf:66:29
via eth2
Sep 13 11:43:28 continuity dhcpd: DHCPOFFER on 192.168.11.106 to
00:50:ba:bf:66:29 via eth2
Sep 13 11:43:34 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:87
via eth2
Sep 13 11:43:44 continuity dhcpd: DHCPOFFER on 192.168.11.107 to
00:c0:df:25:31:87 via eth2
Sep 13 11:43:49 continuity dhcpd: DHCPDISCOVER from 00:50:ba:bf:66:29
via eth2
Sep 13 11:43:54 continuity dhcpd: DHCPOFFER on 192.168.11.106 to
00:50:ba:bf:66:29 via eth2
Sep 13 11:43:59 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:87
via eth2
Sep 13 11:44:04 continuity dhcpd: DHCPOFFER on 192.168.11.107 to
00:c0:df:25:31:87 via eth2
Sep 13 11:44:09 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:44:14 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:44:19 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:44:30 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:44:40 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:44:50 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:44:55 continuity dhcpd: DHCPDISCOVER from 00:50:ba:bf:66:29
via eth2
Sep 13 11:45:00 continuity dhcpd: DHCPOFFER on 192.168.11.106 to
00:50:ba:bf:66:29 via eth2
Sep 13 11:45:05 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:45:11 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:45:16 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:87
via eth2
Sep 13 11:45:21 continuity dhcpd: DHCPOFFER on 192.168.11.107 to
00:c0:df:25:31:87 via eth2
Sep 13 11:45:26 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:45:31 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:45:36 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:45:41 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:45:46 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:45:51 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:45:56 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:46:01 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:46:06 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPREQUEST for 192.168.11.116
(192.168.11.254) from 00:50:ba:bf:66:20 via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPACK on 192.168.11.116 to
00:50:ba:bf:66:20 via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:50:ba:bf:66:29
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.106 to
00:50:ba:bf:66:29 via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:1d:0f:ff:db:08
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.112 to
00:1d:0f:ff:db:08 via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:87
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.107 to
00:c0:df:25:31:87 via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPDISCOVER from 00:c0:df:25:31:4c
via eth2
Sep 13 11:46:11 continuity dhcpd: DHCPOFFER on 192.168.11.115 to
00:c0:df:25:31:4c via eth2

```

---

### Post by nixscripter on 2008-09-21
It looks to me like **00:50:ba:bf:66:20** is different from all the others. It appears to be dropping the DHCP acknowledgements. My questions would be:

1. Why does it think it wants 192.168.11.116? Has it had this address before?
2. What is its firewall status and its DHCP client configuration? It appears to be dropping or ignoring the replies.

---

### Post by marioquark on 2008-09-22
yes it had that address, but note that i use static ip addresses, that is that i wrote MAC-IP entries in the dhcp conf file.

yes, the answer is that client refuses acks, but firewall is not present on the client (it's a LTSP thin client, it boots with etherboot).

how can i understand it refuses acks?
why it sould do so?
should i sniff from server?

thanks

---

### Post by superprash2003 on 2008-09-22
what DHCP range have you seT?

---

### Post by marioquark on 2008-09-22
i have 15 workstations as clients: 192.168.11.101 to 192.168.11.115
...why?

---

### Post by nixscripter on 2008-09-22
What does your dhcp.conf on the server look like? Etherboot requires the DHCP replies to contain a file name to boot; it ignores those that don't have one.

---

### Post by marioquark on 2008-09-22
boot image file is in the dhcp file. i'll try to catch the dhcpoffer packet with wireshark to test if it's really correct, but i think it's not this the problem :confused:

---

### Post by marioquark on 2008-09-23
here:
[http://etherboot.org/wiki/troubleshooting](http://etherboot.org/wiki/troubleshooting)
i can get my error: the **No IP Address** message in the client screen.

the "solution" i found is:
> You will have to set it to the IP address of the TFTP server (in most cases, the same machine as the DHCP server):

next-server 192.168.0.1;

in your dhcpd.conf, somewhere in the global section near the top, will do the trick. 
**_but i already did it..._**

what can i do?:confused::(

---

### Post by superprash2003 on 2008-09-23
try increasing the range to 192.168.11.120

---

### Post by marioquark on 2008-09-23
this is my dhcp.conf file:
```
#
# Default LTSP dhcpd.conf config file.
#

#authoritative;

option domain-name "linuxlab";
#option domain-name-servers 192.168.11.254;
option routers 192.168.11.254;
option root-path "/opt/ltsp/i386";
option option-128 code 128 = string;
option option-129 code 129 = text;
option broadcast-address 192.168.11.255;
#get-lease-hostnames true;
option subnet-mask 255.255.255.0;
default-lease-time 604800;
next-server 192.168.11.254;

#option option-129 "acpi=force";

subnet 192.168.11.0 netmask 255.255.255.0 {
    range 192.168.11.1 192.168.11.99;
    next-server 192.168.11.254;
    
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
        next-server 192.168.11.254;
    } else {
        filename "/ltsp/i386/nbi.img";
        next-server 192.168.11.254;
    }

    host studente1 {
        hardware ethernet    00:1d:0f:ff:d1:07;
        fixed-address        192.168.11.101;
    }

    host studente2 {
        hardware ethernet    00:1d:0f:ff:db:03;
        fixed-address        192.168.11.102;
    }

    host studente3 {
        hardware ethernet    00:1d:0f:ff:db:08;
        fixed-address        192.168.11.103;
    }

    host studente4 {
        hardware ethernet    00:50:ba:bf:66:20;
        fixed-address        192.168.11.104;
    }

    host studente5 {
        hardware ethernet    00:80:c8:e6:92:cc;
        fixed-address        192.168.11.105;
    }

    host studente6 {
        hardware ethernet    00:c0:26:ed:4d:58;
        fixed-address        192.168.11.106;
    }

    host studente7 {
        hardware ethernet    00:c0:df:24:ff:32;
        fixed-address        192.168.11.107;
    }

    host studente8 {
        hardware ethernet    00:c0:df:25:31:4c;
        fixed-address        192.168.11.108;
    }

    host studente9 {
        hardware ethernet    00:d0:09:16:20:54;
        fixed-address        192.168.11.109;
    }

    host studente10 {
        hardware ethernet    00:d0:09:17:57:5d;
        fixed-address        192.168.11.110;
    }

}
```

---

### Post by puppywhacker on 2008-09-23
your log (10 days old) shows a different range than your dhcpd.conf (5 minutes old) ... I guess you were playing with it.

In my dhcpd.conf the subnet part and the host part are strictly seperated. In yours the hosts are also part in of your subnet, but they fall out of the range

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.50 192.168.2.99;
}

host bambam {
	hardware ethernet 0:c:76:29:ff:9c;
	filename "pxelinux.0";
	fixed-address 192.168.2.4;
	server-name "bambam.linuxlab";
}

if that didn't solve it make the tcpdump on the server, I wouldn't be surprised if it had to do something with the broadcast address or something blocking ports.

Regards

---

### Post by marioquark on 2008-09-27
i modified my dhcpd.conf file like this:

```
option domain-name "linuxlab";
option routers 192.168.11.254;
option root-path "192.168.11.254:/opt/ltsp/i386";
option option-128 code 128 = string;
option option-129 code 129 = text;
option broadcast-address 192.168.11.255;
option subnet-mask 255.255.255.0;
default-lease-time 604800;
next-server 192.168.11.254;

group LABClients {
    next-server 192.168.11.254;

    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }

    host studente1 {
        hardware ethernet    00:1d:0f:ff:d1:07;
        fixed-address        192.168.11.101;
    }

    [...]

    host studente10 {
        hardware ethernet    00:d0:09:17:57:5d;
        fixed-address        192.168.11.110;
    }
}

```

but it doesn't works.
so i tried** dhcpdump** and it gives me this (this is the reply):

---------------------------------------------------------------------------
  TIME: 11:58:08.386955
    IP: > (00:c0:df:25:1c:4a) >  (00:1d:0f:ff:db:03)
    OP: 2 (BOOTPREPLY)
 HTYPE: 1 (Ethernet)
  HLEN: 6
  HOPS: 0
   XID: 0fffe761
  SECS: 0
 FLAGS: 0
CIADDR: 0.0.0.0
YIADDR: 192.168.11.102
SIADDR: 192.168.11.254
GIADDR: 0.0.0.0
CHADDR: 00:1d:0f:ff:db:03:00:00:00:00:00:00:00:00:00:00
 SNAME: .
 FNAME: /ltsp/i386/nbi.img.
OPTION:  53 (  1) DHCP message type         2 (DHCPOFFER)
OPTION:  54 (  4) Server identifier         192.168.11.254
OPTION:  51 (  4) IP address leasetime      86400 (24h)
OPTION:   1 (  4) Subnet mask               255.255.255.0
OPTION:   3 (  4) Routers                   192.168.11.254
---------------------------------------------------------------------------

clients continue to don't ACK... any suggestion?   :(
thanks
quark

---

### Post by nixscripter on 2008-09-29
Try adding that subnet...range superphrash suggested:

```

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.50 192.168.2.99;
}

group ...

```

And the code tags are just forum tags. Type the word "code" with square brackets around your stuff, the same way you make things bold and underlined. The result will be a block like I had above.

---

