---
title: "Changing DNS to OpenDNS"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by mirrorhall on 2007-07-27
My ISP DNS Servers keep getting spoofed and i would like to change to OpenDNS. I have a broadband ISP and use a router to log into the PPPoE account (pretty standard).

I would like to tell DHCP to not do DNS and then tell it which servers to use. However, the router will always reset the DNS on renewing their lease. I use dnsmasq to set a local DNS cache (speeds up access to often visited sites) so my first entry is 127.0.0.1, but otherwise the setup is pretty standard.

In gentoo i can go to /etc/conf.d/net and set:

> config_eth0="dhcp"
dhcpcd_eth0="-t 10"
dhcp_eth0="nodns"
dns_servers_eth0="127.0.0.1 208.67.222.222 208.67.220.220"

How can i do this in Ubuntu so that the change survive rebooting the router?

New to Ubuntu! Obvious isn't it - Loving it so far. :)

---

### Post by dmizer on 2007-07-27
fantastic directions right on opendns ... [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php) under "Using OpenDNS with DHCP"

---

### Post by mirrorhall on 2007-07-27
> **dmizer said:**
> fantastic directions right on opendns ... [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php) under "Using OpenDNS with DHCP"

Thanks, yes. But as I'm new to Ubuntu I'd like to understand how to do this the Debian way. The instructions on the OpenDNS website instruct you to use networking (adjust the DNS servers in the GUI). The problem is this does not survive a router restart.

My question is therefore how do we control DHCP the debian way (on the *.conf command line level or dpkg level?)

1. Tell DHCP not to do DNS (otherwise the router resets the servers on each lease change)
2. Tell DHCP which servers to use for DNS. (redirect to using whichever ones i choose to use)

:: So that the changes are permanent on a router reboot, and "connection information" shows the opendns dns address and not my ISP's.

---

### Post by dmizer on 2007-07-27
no ... under "using opendns with dhcp"

it says this:
> 1) Run: sudo gedit /etc/dhcp3/dhclient.conf

2) Change the prepend line to read:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.

3) Run: sudo /etc/init.d/networking restart

---

### Post by dmizer on 2007-07-27
i see ... there's a link for "ubuntu" at the top of the link i sent you.

for the ubuntu specific directions, the command line directions are also listed under: "If your settings get revoked after reboots, or after periods of inactivity, you can try this:"

but they are the same directions as appears under "Using OpenDNS with DHCP" on the same page i linked you to earlier.

---

### Post by mirrorhall on 2007-07-27
> **dmizer said:**
> i see ... there's a link for "ubuntu" at the top of the link i sent you.

for the ubuntu specific directions, the command line directions are also listed under: "If your settings get revoked after reboots, or after periods of inactivity, you can try this:"

but they are the same directions as appears under "Using OpenDNS with DHCP" on the same page i linked you to earlier.

Yes, i saw all that - thanks.

The problem was that these settings were not being remembered on reboot. However i seem to have found my mistake. Adding user to the "dhcp" group and then setting up the networking options in the GUI seems to work.:popcorn:

NOTE:
**Add user to group "dhcp" seems to allow Ubuntu to remember DHCP settings.**

---

### Post by kevdog on 2007-07-28
I think using OpenDNS with Samba screws up connecting to other "windows" computers, particularly if you are using winbind to refer to them by name rather than by IP address.  Just an FYI if you encounter this in the future.  I contact OpenDNS about this, and they wanted me to subscribe to their service to find a solution.  I told them to forget it!

---

### Post by dmizer on 2007-07-28
> **kevdog said:**
> I think using OpenDNS with Samba screws up connecting to other "windows" computers, particularly if you are using winbind to refer to them by name rather than by IP address.  Just an FYI if you encounter this in the future.  I contact OpenDNS about this, and they wanted me to subscribe to their service to find a solution.  I told them to forget it!

if you're using wins, configure your nsswitch.conf file's hosts line so that it resolves wins before it resolves dns like so:
```
hosts:          files wins dns
```
then opendns doesn't interfere with your windows network.

---

### Post by kevdog on 2007-07-28
Thanks for the tip!!!  Why isnt this info just posted on the OpenDNS site?  Why would they want to charge me for this??

---

### Post by erfahren on 2008-01-28
just adding links for people serching this topic in the future:
[HOWTO get around flaky DNS servers: pointers to some simple methods](http://ubuntuforums.org/showthread.php?t=543659)
[Ubuntu Tutorials - How To Setup OpenDNS On Ubuntu](http://ubuntu-tutorials.com/2007/03/14/how-to-setup-opendns-on-ubuntu/)

---

