---
title: "No PXE boot after LTSP set up"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Tobsie on 2009-08-17
Hello to everyone in the forum!

Here is the problem I'm dealing with. I'm really new to Ubuntu and Linux in general. I started with installing Ubuntu and really liked it. Now i read about a LTSP and booting your X-Server over the network. 

I started off by using the normal To-Do's you find after a google search and everything went pretty smoothly. I installed an LTSP server with the Ubuntu Alternate CD... so I didn't set it up by myself and tested the network boot with my notebook. 

It worked fine the first time I started it and i was pretty happy. But it seems as though my Notebook is the only one that can boot to the Ubuntu-"server". 

I tried the network boot with another desktop pc i had and it just didn't seem to find the x-server. I'm guessing the network interface card in my desktop computer is to old?

This is what it says when I start the network boot:

-- Intel UNDI, PXE - 2.0 (build 082)
-- SiS900 PXE Boot ROM v1.09 Hook Int 19

Compared to my notebook:

-- Yukon PXE v.3.5.2.3
-- PreBoot exEcution Environment PXE v2.1

Could this be the problem. Those anyone have any tips where I can go from here? Is there any other information I should post to my Problem?

Thanks alot for the help!

---

### Post by Shig on 2009-08-17
Hi

PXE is all you need, what do you get following the PXE message on the desktop?
i.e. what do you get after:
```
-- Intel UNDI, PXE - 2.0 (build 082)
-- SiS900 PXE Boot ROM v1.09 Hook Int 19
```

Do you know which DHCP server software you are running on the LTSP server? If so, could you please post the configuration file?
Do you only have DHCP running on the one system (the LTSP server) or could you be picking up DHCP from another device like a DSL router?

---

### Post by Tobsie on 2009-08-17
Hi

> Do you know which DHCP server software you are running on the LTSP server?Ehm not really :-) This is the dchp.conf file I found on my server. 

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
}
```> Do you only have DHCP running on the one system (the LTSP server) or could you be picking up DHCP from another device like a DSL router?Well actually there is a different DHCP Server in the network. I was kind of figuring that durin my LTSP Server set up with the alternate Ubuntu CD he figured that out on his own and set up everything so the DCHP Server would connect computers booting with PXE with my LTSP Server automatically. I thought this was working because i could connect to the X-Server from my Notebook the first time i tried without altering any files or set ups. 

But I guess you could be right that I have problems with the seperate DCHP server. Since i pretty much have no knoweldge of this kind of stuff yet it could turn out to be a big problem too :-).

Here is some more information on how I installed the LTSP Server:

I just connected my "Server"-Computer to the network with two cables since it had to network interface cards ( i read in some How-to that this would work if you had a DCHP server allready running in your network ).

After that I just started the installation of the alternate CD, "LTSP Server Install".

It took a while till everything was set up, but everything pretty much installed automaticly. 

After that I connected my Notebook to the network and used network boot and i automatically connected with the LTSP Server.

>  i.e. what do you get after:
     Code:
     -- Intel UNDI, PXE - 2.0 (build 082)
-- SiS900 PXE Boot ROM v1.09 Hook Int 19 
This is what it says:

--Client Mac ADDR: ..............
--DCHP...../
--
--PXE MOF: Exiting PXE ROM

---

### Post by Shig on 2009-08-17
Hi 

I would say that it is picking up the other DHCP server for sure.

I had to disable DHCP on my router, and in the DHCP configuration on the LTSP server, ensure the IP address of your router is specified as the "router" and "domain-name-servers" option. The below two lines from your config file indicate that 192.168.0.1 is being sent to DHCP clients from the LTSP server as the router and DNS server, if 192.168.0.1 is your router, you should simply need to disable DHCP on your router.

```
option routers 192.168.0.1;
option domain-name-servers 192.168.0.1;
```

Also, it would be a good idea to only run one LAN cable from the server to the switch. Having multiple interfaces will confuse the DHCP server, as the two network plugs on the computer are treated as seperate network interfaces, and without advanced configuration will behave as completely seperate networks. The net affect of this will be that DHCP and LTSP will work on one network card, but will not work on the other as you can not have two interfaces on the same network subnet (e.g. 192.168.0.0).

Hope this clears things up, let us know how you go.

---

### Post by Tobsie on 2009-08-17
Thanks alot for your quick answer. 

I guess I will really have to look into this then. I am allready thinking about installing a plain ubuntu and then setting up the ltsp server step by step to understand the configurations. 

I can't switch off the DCHP on the router since alot of different computers are connected to it and need to be working all the time.. so i guess I'll have to find a work around for this then.

Thanks again! I'll probably have more questions coming :-)

---

