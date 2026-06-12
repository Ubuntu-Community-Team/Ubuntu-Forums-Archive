---
title: "LTSP - no subnet declaration for eth0"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by JayKay3OOO on 2014-04-17
I've been searching for a solution for this for the last few hours. - I'm on ubuntu 13.10 desktop.

I want to re-aquaint myself with ltsp using my main and only network card. (1 network card)

I've set up ltsp a few years ago and it was easy even on a single networked car machine. Just a matter of getting the dhcpd.conf file set up right.

 tail -f /var/log/syslog


Apr 18 00:06:45 FS1 dhcpd: Wrote 0 leases to leases file.
Apr 18 00:06:45 FS1 dhcpd: 
Apr 18 00:06:45 FS1 dhcpd: No subnet declaration for eth0 (192.168.1.65).
Apr 18 00:06:45 FS1 dhcpd: ** Ignoring requests on eth0.  If this is not what
Apr 18 00:06:45 FS1 dhcpd:    you want, please write a subnet declaration
Apr 18 00:06:45 FS1 dhcpd:    in your dhcpd.conf file for the network segment
Apr 18 00:06:45 FS1 dhcpd:    to which interface eth0 is attached. **
Apr 18 00:06:45 FS1 dhcpd: 
Apr 18 00:06:45 FS1 dhcpd: 
Apr 18 00:06:45 FS1 dhcpd: Not configured to listen on any interfaces!

I've had a go at setting the eth0 and even putting in static ips in /etc/network/interfaces. All that does is just stops the Ethernet from being seen by ubuntu.

This ended up hashed to death.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#mapping hotplug
#       script grep
#       map eth0


#iface eth0 inet dhcp


#auto eth0
#iface eth0 inet loopback
#       address 192.168.1.65
#       network 192.168.1.0/24
#       netmask 255.255.255.0
#       broadcast 192.168.1.255




I've not touched the /etc/default/isc-dhcp-server config file except to put eth0 in interfaces, but it has no visible effect:

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"


Finally, this is my dhcpd.conf file. Where I put that subnet declaration, whatever it looks like I have no idea.

#
# Default LTSP dhcpd.conf config file.
#


authoritative;


subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.200;
    option domain-name "lns";
    option domain-name-servers 8.8.8.8;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.254;
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




I've read the 10 or so threads, but most people seem to have given up on it. I remember ltsp being a 10 minute job.

Cheers.

---

### Post by JayKay3OOO on 2014-04-21
Got it working. If you're a noob like me then, here's all my hair tearing compressed into a short (ish) post - using completley default ltsp settings.

I have it running on my home Ubuntu server 13.10
Gnome desktop installed and my choice of  server services.

[rant removed]

There are currently so many guides that are out of date with regards to ltsp and many forum threads that people have given up on and naturally I chose to read none of them - like a boss.

Here is  the guide I followed:

[http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html](http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html)

This guide fails to tell you the most important thing.

 You have to edit  /etc/ltsp/dhcpd.conf **and** /etc/dhcp/dhcpd.conf 
Coppy the  network config section into a space in /etc/dhcp/dhcpd.conf - I put it into the section "A slightly different configuration for an interrnal subnet", but I doubt it matters.

e.g. ```
# A slightly different configuration for an internal subnet.
  subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.201 192.168.1.250;
  option domain-name-servers 192.168.1.254;
  option domain-name "example.org";
  option routers 192.168.1.254;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```



Re-start it using: ```
sudo /etc/init.d/isc-dhcp-server restart
```

It used to be sudo /etc/init.d/dhcp3-server restart (when I last did it like that guide says)

You might need to put your network device in /etc/default/isc-dhcp-server

```
INTERFACES=eth0
```


There was another place, but right now I can't recall. (edit this later)

dhcp should start now!

I had a couple of 'cannot find tftp server' or something like that so I installed the  dnsmasq package and found a conflict witth the IP I stated in the /etc/network/interfaces file. So I changed the IP and then used the code in the following thread to  fix it.

[http://ubuntuforums.org/showthread.php?t=1473485]("http://ubuntuforums.org/showthread.php?t=1473485sudo")

```
sudo aptitude install dnsmasq dnsmasq-base
sudo aptitude remove dnsmasq+ dnsmasq-base
```

Now  build the client and don't forget to put ltsp-build-client i386 if you want it to be 32 bit. ltsp-build-client makes a 64bit version in  which case you'd need to change the /etc/ltsp/dhcpd.conf to point to the amd64 folder (/opt/ltsp/amd64)

If you did not know this (like me) and you built the wrong version and found it refused to work again (cannot download xyz file) now all you need to do is the following:
```

sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get update
```

Original post here  [http://itsfoss.com/solve-ubuntu-error-failed-to-download-repository-information-check-your-internet-connection/](http://itsfoss.com/solve-ubuntu-error-failed-to-download-repository-information-check-your-internet-connection/)

You need to delete the incomplete build folder before having another go it's protected so you can either chmod the persmissions or launch the file manager in super mode (assuming ubuntu) ```
su nautilus
``` or ```
su dolphin
```

Virtual box  won't boot still (that's for another time), but your real thin client should after a  server restart. 

Hope this helps anyone else till the next time ltsp is changed and this information is irrelevant.

---

