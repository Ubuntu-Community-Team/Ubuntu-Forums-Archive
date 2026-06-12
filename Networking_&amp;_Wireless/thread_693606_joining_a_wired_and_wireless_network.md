---
title: "joining a wired and wireless network"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Klunk on 2008-02-11
Hi,

I am trying to organise my network and use Xen. I have an ADSL connection coming into the network via and ADSL router. I have this connected to a wireless router. From the wireless router I have a wirless Linux machine running Xen (Dom0), a wireless playstation 3 (PS3) and a wireless Windows machine (win1). The Xen server has 3 DomUs one of which will run a DHCP server. Dom0 was built from a base Gutsy server build, with SSH, and runs iptables, the Xen install was the xen-ubuntu-server package. It has a wired ethernet as well and acts as a gateway machine for the main network which has a windows machine attached (win2)

The network looks something like this:

```

        ISP
          |
          |/|
            |
     ---------------
    |    ADSL       |
    |    Modem /    |
    |    Router     |
    | 192.168.254.x |
     ---------------
            |
            |             | .))))         ((((. |
     ---------------      |                     |         --------------------
    |   Wireless    |-----                       --------| Playstation 3      |
    |   Router      |                                    | DMZ – 192.168.1.50 |
    | 192.168.1.x   |                                     --------------------
     ---------------
                            ((((. |
            | .))))               |         --------------
      Wlan0 |                      --------| Windows Host | 
     -------------------                   | 172.16.45.x  |
    | Linux Xen Dom0    |                   --------------
    | running iptables  |
    | 3 x DomU          |
    | Dom1 running DHCP |
     -------------------
      Eth0  |
            |
     --------------
    | Windows Host |
    | 172.16.45.x  |
     --------------
```

The ADSL coming in, through wireless to Dom0 is fine, and I hope that I will soon have the DomU will also be fine (I have one outstanding issue which I think I know the resolution to.) My challenge is I want the wireless windows host (win1) to have an address in the same range and win2 and go through Dom0 to access the internet from behind the firwall.

I assume I need a vlan from wlan0 but I am not sure where to start. On the assumption that this is possible can win1 be a dchp client or does it need a fixed ip? Does anyone know of a good site that will help me with this?

---

### Post by Klunk on 2008-02-11
Apologies but ***BUMP ***

As it had gone onto page 3.

---

