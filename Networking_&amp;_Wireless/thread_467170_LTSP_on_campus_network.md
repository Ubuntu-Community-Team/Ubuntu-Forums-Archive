---
title: "LTSP on campus network"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by tastygroove on 2007-06-07
so i'm trying to set up ltsp on our server here.  i have 3 diskless workstations that need to connect to it.  i'm running kubuntu feisty and i'm trying to use ltsp 5.  i've followed the instructions on various pages, including the edubuntu setup page.  i think i have everything installed properly, i think its a matter of not configuring my dhcpd.conf file properly.  that trick is that the server and thin clients are connected through the university network (which i do not administer).  these thin clients were configured on the previous server, and i copied the dhcpd.conf file from it thinking it would work just fine, but no luck.  here is my currently config file.  i know the host sections are different.  i've just been altering the top one until i get it right.  any ideas?

```
# Make changes to this file and copy it to /etc/dhcpd.conf.sample
#

authoritative;

ddns-update-style            none;

default-lease-time           21600;
max-lease-time               21600;

##
## If you want to use static IP address for your workstations, then un-comment
## the following section and modify to suit your network.
## Then, duplicate this section for each workstation that needs a static
## IP address.
##
subnet 129.64.52.0 netmask 255.255.255.0 {

    host jet {
        hardware ethernet    00:13:90:00:39:35;
        fixed-address        129.64.52.13;
        option subnet-mask   255.255.255.0;
        option routers       129.64.52.0;
        option domain-name-servers 129.64.2.3;
        option domain-name   "astro.brandeis.edu";
        server-name          "129.64.52.34";
        filename             "pxelinux.0";
    }
    host hotspot {
        hardware ethernet    00:13:90:00:3D:95;
        fixed-address        129.64.52.14;
        filename             "/opt/ltsp/i386/boot/pxelinux.0";
    }
    host plasma {
        hardware ethernet    00:13:90:00:75:C9;
        fixed-address        129.64.52.17;
        filename             "/opt/ltsp/i386/boot/pxelinux.0";
    }
}
```

---

### Post by tastygroove on 2007-06-07
i should probably mention what is not working about the whole setup. 

so what i've done so far is 
- installed ltsp-server (actually i installed edubuntu-server) using aptitude
- ran the ltsp-client-setup
- configured my dhcpd.conf to what you see in the previous post
- restart dhcpd

so what i start the thin client it tries to boot for a bit then says, 
"PXE-E53:No boot filename received"

PXE-M0F: Exiting PXE ROM"

and that's it.  i can't tell if its connecting to my dhcpd server and just not seeing the correct file or if its simply not connecting at all.

---

