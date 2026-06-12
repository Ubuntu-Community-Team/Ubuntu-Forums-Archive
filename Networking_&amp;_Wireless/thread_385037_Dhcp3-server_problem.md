---
title: "Dhcp3-server problem"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by incin on 2007-03-15
Hi

i have a problem with my dhcp3 server, everytime i try and start it, it fails.
in the syslog i get the standard message:
No subnet declaration for eth1 (192.168.124.128)
and the message that it ignores the requests on eth1
i also get the same error on eth0 (192.168.254.128)
on the end it says: Not configured to listen on any interfaces.
i have added the INTERFACES="eth0 eth1" to the /etc/default/dhcp3-server
and the dhcp3.conf file is a auto generated file made with ltsp 4.2.
can this have any thing to do with the fact that ltsp keeps asking me about the inittab file that i dont seem to be able to find anywere. i have read all the solutions i could find on the forum here but none seem to work for my server. i have added a second network card to the server to test if that worked but, it didn't.
anyone out there that can help?
my dhcp3-server file
> # Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0 eth1"
my dhcpd.conf file
> # dhcpd.conf

ddns-update-style             ad-hoc;

option subnet-mask            255.255.255.0;
option broadcast-address      192.168.254.255;
option routers                192.168.254.128;
option domain-name-servers    192.168.254.128;
option domain-name            "ltsptest.org";   # You really should fix this
option option-128 code 128 = string;
option option-129 code 129 = text;


get-lease-hostnames           true;

next-server                   192.168.254.128;
option root-path              "192.168.254.128:/opt/ltsp/i386";

subnet 192.168.0.0 netmask 255.255.255.0 {
    range   192.168.0.100   192.168.0.199;
    if substring (option vendor-class-identifier, 0, 9) = "PXEClient" {
        filename "/lts/2.6.16.1-ltsp-1/pxelinux.0";
    }
    else{
        filename "/lts/vmlinuz-2.6.16.1-ltsp-1";
    }
}
#
# If you need to pass parameters on the kernel command line, you can
# do it with option-129.  In order for Etherboot to look at option-129,
# you MUST have option-128 set to a specific value.  The value is a
# special Etherboot signature of 'e4:45:74:68:00:00'.
#
# Add these two lines to the host entry that needs kernel parameters
#
#        option option-128     e4:45:74:68:00:00;       # NOT a mac address
#        option option-129     "NIC=ne IO=0x300";
#

and the syslog
> Mar 15 13:35:05 ltsptest dhcpd: No subnet declaration for eth1 (192.168.124.128).
Mar 15 13:35:05 ltsptest dhcpd: ** Ignoring requests on eth1.  If this is not what
Mar 15 13:35:05 ltsptest dhcpd:    you want, please write a subnet declaration
Mar 15 13:35:05 ltsptest dhcpd:    in your dhcpd.conf file for the network segment
Mar 15 13:35:05 ltsptest dhcpd:    to which interface eth1 is attached. **
Mar 15 13:35:05 ltsptest dhcpd: 
Mar 15 13:35:05 ltsptest dhcpd: 
Mar 15 13:35:05 ltsptest dhcpd: No subnet declaration for eth0 (192.168.254.128).
Mar 15 13:35:05 ltsptest dhcpd: ** Ignoring requests on eth0.  If this is not what
Mar 15 13:35:05 ltsptest dhcpd:    you want, please write a subnet declaration
Mar 15 13:35:05 ltsptest dhcpd:    in your dhcpd.conf file for the network segment
Mar 15 13:35:05 ltsptest dhcpd:    to which interface eth0 is attached. **
Mar 15 13:35:05 ltsptest dhcpd: 
Mar 15 13:35:05 ltsptest dhcpd: 
Mar 15 13:35:05 ltsptest dhcpd: Not configured to listen on any interfaces!
Mar 15 13:50:45 ltsptest -- MARK --

i am runing the ubuntu 6.10 server on a vmware sesion.

---

### Post by Mr. C. on 2007-03-15
Where is the subnet declaration that encompasses these two IP addresses of the NICs?

```
eth1 192.168.124.12
eth0 192.168.254.12
```

Certainly this is not it:

```
subnet 192.168.0.0 netmask 255.255.255.0
```

See: Week 7: "DHCP/BOOTP" notes and lab work:
[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by incin on 2007-03-19
thanks that pointed me in the right direction.
but now i cant get the thinclient to mount the nfs dir :( 
have been looking in diferent forums and googled it, but it dont seem to be a direct sulotion to this, dont know if there is any one else here that has the same problem with ltsp?
get the error > mount: 192.168.254.128:/opt/ltsp/i386 failed, reason given by server: permission denied
mount: nfsmount failed: bad file descriptor
mount: mounting 192.168.254.128:/opt/ltsp/i386 on /newroot/nfsroot failed: invalis argument
ERROR! Failed to mount the root directory via NFS!
possible reasons include:
1 ) NFS services may not be running on the server
2 ) Workstation IP does not map to a hostname, either in /etc/hosts, or in DNS
3 ) Wrong address for NFS server in the DHCP config file
4 ) Wrong pathname for root directory in the DHCP config file
i have cheked all the points in the error and it did not seem like there was any error in the files.
the /etc/hosts file has all the IP-addresses that the DHCP gives out.
one of the lines in the hosts file is
> 192.168.254.199 ws199.ltsp ws199
is this the problem or?
im kinda new to linux so plz dont talk way over my head :)

---

### Post by Mr. C. on 2007-03-19
Let's open a new thread for your NFS/mount issues.  This was about DHCP, and it is more useful to other's when Title's match content, and you're more likely to get help.

I'll  help you in the new thread.
MrC

---

### Post by incin on 2007-03-20
now have i made another tread about the nfs mount problem
[http://ubuntuforums.org/showthread.php?t=388959]("http://ubuntuforums.org/showthread.php?t=388959")

---

