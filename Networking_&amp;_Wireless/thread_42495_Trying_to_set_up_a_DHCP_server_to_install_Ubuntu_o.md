---
title: "Trying to set up a DHCP server to install Ubuntu on a laptop"
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by Dullin on 2005-06-17
Hello everyone,

I have been trying to get a dhcp server up to install ubuntu on a laptop of a friend of mine who has no CD-rom tray.

I have been following the [Ubuntu guide](https://wiki.ubuntu.com//LocalNetInstall) but I get stopped at the point where I need to install dhcp3-server.

It installs fine but when comes the time to start it it gives me. 
```
Starting DHCP server: dhcpd3 failed to start - check syslog for diagnostics.
invoke-rc.d: initscript dhcp3-server, action "start" failed.
```

So i go and check into syslog wich then tells me

```
localhost dhcpd Internet Systems Consortium DHCP Server V3.0.1
localhost dhcpd Copyright 2004 Internet Systems Consortium.
localhost dhcpd All rights reserved.
localhost dhcpd For info, please visit http://www.isc.org/sw/dhcp/
localhost dhcpd Wrote 0 leases to leases file.
localhost dhcpd 
localhost dhcpd No subnet declaration for eth0 (0.0.0.0).
localhost dhcpd ** Ignoring requests on eth0.  If this is not what
localhost dhcpd you want, please write a subnet declaration
localhost dhcpd in your dhcpd.conf file for the network segment
localhost dhcpd to which interface eth0 is attached. **
localhost dhcpd 
localhost dhcpd 
localhost dhcpd Not configured to listen on any interfaces!
```

I have tried to make it work many times but to no avail. Once the dhcp server started but tftp didn't seem to work with it. I have not even been able to reproduce a working DHCP server. I have both computers plugged in a hub.

I now turn to you, oh mighty linux network gurus to help me against the fight of ignorance.

---

### Post by diebels on 2005-06-18
You did this:
[QUOTE=https://wiki.ubuntu.com/LocalNetInstall]6. Set the dhcp server to tell the clients what to boot. I added a default host name, you don't need it but it comes in handy for other things.

root@sahara:~ # cat /etc/dhcp3/dhcpd.conf
# option domain-name-servers 68.87.64.140
# option broadcast-address 192.168.1.255;
# option routers  192.168.1.1;
ping-check = 1;
filename="pxelinux.0";
subnet 192.168.1.0  netmask 255.255.255.0 {
        range 192.168.1.10 192.168.1.254;
         }

root@sahara:~ # /etc/init.d/dhcp3-server restart
Stopping DHCP server: dhcpd3.
Starting DHCP server: dhcpd3.[/QUOTE]
?

---

### Post by Dullin on 2005-06-18
[QUOTE=diebels]You did this:

?[/QUOTE]

Yep, and still no dice. And even more amazing is that I tried a generic sample ```

ping-check=1;
filename="pxelinux.0";

subnet 192.168.0.0 netmask 255.255.255.0 {
# --- default gateway
	option routers			192.168.0.1;
	option subnet-mask		255.255.255.0;

	option nis-domain		"domain.org";
	option domain-name		"domain.org";
	option domain-name-servers	192.168.1.1;

	option time-offset		-5;	# Eastern Standard Time
#	option ntp-servers		192.168.1.1;
#	option netbios-name-servers	192.168.1.1;
# --- Selects point-to-point node (default is hybrid). Don't change this unless
# -- you understand Netbios very well
#	option netbios-node-type 2;

	range dynamic-bootp 192.168.0.128 192.168.0.255;
	default-lease-time 21600;
	max-lease-time 43200;

	# we want the nameserver to appear at a fixed address
	host ns {
		next-server marvin.redhat.com;
		hardware ethernet 12:34:56:78:AB:CD;
		fixed-address 207.175.42.254;
	}
}

``` 

That would be when the DHCP server worked for a little while but now, even with that config it won't start.

---

### Post by blackomegax on 2005-06-18
why cant they just add a "start pxe server" onto the installer disc?
i have the same problem. ibm x40 and no way to boot cd's on it

---

### Post by MattiViljanen on 2005-11-03
I have a solution and a problem.

The solution part: Check your /etc/default/dhcp3-server file, and make sure it has the following line:

INTERFACES="eth0"

It may be missint the eth0 part.
You may also want to check your eth0 IP is a static one.

The problem part: I have tried all those, and still the server fails to start. Log file tells me only that the dhcp server "greeting", version number and such.

It won't start even after dpkg-reconfigure dhcp3-server. I'm tyring to make a BOOTP server, but the result is the same before and after installing ltsp-server-standalone package.

Help, please!

---

