---
title: "cannot access internet form PC with ltsp running"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by Philippe_Rousselot on 2013-10-14
Hi,

I have an edubuntu server 13.04.

there are two net cards one to connect to the internet (via the main network, modem + ipcop + dhcp) and the other one for the local network.

eth0 is connected to the main network
eth1 is connected to a switch

I have one thin client, a Lubuntu PC (same machine) and an  XP PC

from the server, I can go on the internet

from the thin client I can go on the internet hear sound mount usb key but cannot unmount them

from the same machine but running lubuntu 13.04 form a hard drive, **I cannot go on the internet but I get an IP adress**

from the XP PC, I cannot go on the internet but I get an IP adress. It does not seem to be a dns problem as I neither can go to an online serveur using its IP adress, nor ping it.

I thought it could have been an IPtable problem and I used the following command

iptables -A POSTROUTING -t nat -o eth1 -j MASQUERADE

It still does not work 

ifconfig server
```


eth0      Link encap:Ethernet  HWaddr 00:1a:4b:fe:48:c4  
          inet adr:192.168.77.124  Bcast:192.168.77.255  Masque:255.255.255.0
          adr inet6: fe80::21a:4bff:fefe:48c4/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:61834 erreurs:0 :0 overruns:0 frame:0
          TX packets:43119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:63850217 (63.8 MB) Octets transmis:4454837 (4.4 MB)
          Interruption:16 

eth1      Link encap:Ethernet  HWaddr 00:18:71:ea:38:c3  
          inet adr:192.168.0.1  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::218:71ff:feea:38c3/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:163287 erreurs:0 :0 overruns:0 frame:0
          TX packets:236957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:46034110 (46.0 MB) Octets transmis:261497115 (261.4 MB)
          Interruption:16 Mémoire:fdee0000-fdf00000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:142434 erreurs:0 :0 overruns:0 frame:0
          TX packets:142434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:165022185 (165.0 MB) Octets transmis:165022185 (165.0 MB)

lxcbr0    Link encap:Ethernet  HWaddr 2e:7f:cc:32:e5:1d  
          inet adr:10.0.3.1  Bcast:10.0.3.255  Masque:255.255.255.0
          adr inet6: fe80::2c7f:ccff:fe32:e51d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:53903 (53.9 KB)


```


ifconfig thin client
```


eth0      Link encap:Ethernet  HWaddr 00:1a:4b:fe:48:c4  
          inet adr:192.168.77.124  Bcast:192.168.77.255  Masque:255.255.255.0
          adr inet6: fe80::21a:4bff:fefe:48c4/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:68783 erreurs:0 :0 overruns:0 frame:0
          TX packets:47921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:68121201 (68.1 MB) Octets transmis:4911530 (4.9 MB)
          Interruption:16 

eth1      Link encap:Ethernet  HWaddr 00:18:71:ea:38:c3  
          inet adr:192.168.0.1  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::218:71ff:feea:38c3/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:241810 erreurs:0 :0 overruns:0 frame:0
          TX packets:345149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:60744329 (60.7 MB) Octets transmis:371206098 (371.2 MB)
          Interruption:16 Mémoire:fdee0000-fdf00000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:235742 erreurs:0 :0 overruns:0 frame:0
          TX packets:235742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:216798365 (216.7 MB) Octets transmis:216798365 (216.7 MB)

lxcbr0    Link encap:Ethernet  HWaddr 2e:7f:cc:32:e5:1d  
          inet adr:10.0.3.1  Bcast:10.0.3.255  Masque:255.255.255.0
          adr inet6: fe80::2c7f:ccff:fe32:e51d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:55055 (55.0 KB)

```


ifconfig PC lubuntu (same as thin client)
```


eth0      Link encap:Ethernet  HWaddr 44:4d:50:04:a7:c4  
          inet adr:192.168.0.11  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::464d:50ff:fe04:a7c4/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:98 erreurs:0 :0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:11287 (11.2 KB) Octets transmis:16156 (16.1 KB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:149 erreurs:0 :0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:11150 (11.1 KB) Octets transmis:11150 (11.1 KB)

```


/var/lib/tftpboot/ltsp/i386/lts.conf
```

# lts.conf, provided by Edubuntu installer
# see http://edubuntu.org/documentation for more information

[default]
  LDM_THEME=edubuntu
  LANG=fr_FR.UTF-8
  LANGUAGE=fr_FR.UTF-8
  LDM_LANGUAGE=fr_FR.UTF-8
  LDM_SESSION=gnome-fallback
  XKBLAYOUT=fr
  SOUND=True
  LOCALDEV=True
  LDM_AUTOLOGIN = TRUE
  HOSTNAME_BASE = ltspComp

[192.168.0.11]
LDM_USERNAME = poste1
LDM_PASSWORD = xxxxx


```


dhcpd.conf 
```


#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
host amshubuntu1 {
        hardware ethernet 44:4D:50:04:a7:c4;
        fixed-address 192.168.0.11;
}
}


```


[B]remarque : 

What I would prefer is to have the server with only one net card, having the ipcop acting as DHCP server.[/B]


Thanks in advance for your help

Philippe

---

