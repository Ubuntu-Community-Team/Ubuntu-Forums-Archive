---
title: "diskless hostname via dhcp"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by justDIY on 2006-11-11
greetings

I have a diskless nfsroot of ubuntu 6.06 that I want to share with several diskless workstations.

right now, they all think they are the same machine, hostname wise.  

each has a reservation in the dhcp server, and the server pushes a hostname and domainname to the clients, but the clients are ignoring that information

I tried removing /etc/hostname to see if it'd pickup on the dhcp supplied information, but it doesn't.

/etc/dhcp3/dhclient.conf has request host-name and domain-name in the list of informations requested... and the kernel shows this information just before it starts init off the nfsroot.

google gives me lots of results on updating the dhcp server (dnsmasq or similar) with a client hostname, using send host-name, but nothing about receiving the hostname from the server

I seem to remember the installer asking about retrieving this info from dhcp, so how do I do it now after the fact?  any ideas?!

---

### Post by justDIY on 2006-11-11
ok, so this solution is not pretty ... still waiting on an expert to show me the right way :)

```

#!/bin/bash
# toss this in /etc/init.d - i named mine sethostname
# the idea: get our IP addr, reverse lookup against the dhcp/dns server
# how get the hostname, and use the hostname command to set it without using /etc/hostname

# get our IP address
ip=`ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`

# get our fqdn from the dhcp/dns server (dnsmasq)
fqdn=`dig -x $ip +short`

# strip off the dn
myname=${fqdn%%.*}

# voila
echo "Found my hostname is" $myname
hostname $myname
```

to make sure my clients run this before a whole bunch of hostname dependent services get started, I added it early to runlevel 2

cd /etc/rc2.d
ln -s ../init.d/sethostname S10sethostname

reboot and presto, each client sets its own hostname, without overwriting the would-be shared /etc/hostname file

---

### Post by justDIY on 2006-11-11
oh, I also found out, according to the xorg.conf manpage, that xorg will look in alternate places for its config file if /etc/X11/xorg.conf is missing

# mkdir -p /usr/etc/X11
# cp /etc/X11/xorg.conf /usr/etc/X11/xorg.conf.hostname
# rm /etc/X11/xorg.conf

allows one to create multiple xorg configurations for machines that might have different video cards or input options

---

### Post by xdcdx on 2007-02-08
The information and script you provided are great.

I am stuck with a problem similar to yours, but with the difference that my server does not have a DNS server, and just provides a DHCP server.

Clearly, the DHCP server can provide a hostname, via 'option host-name "foobar";' but then I cannot seem to be able to query this value directly. I tried several options with the dhclient command, but I could not get the hostname. If one does a full dhcp configuration from a diskless machine booted from NFS, the NFS connection is lost and everything crashes. I think there should be a way to query *just* for the hostname through DHCP.

Maybe we should submit this as a bug/suggestion to dhclient/dhcpsd or to Ubuntu?

Right now, I am working in a simple workaround script similar to yours, that uses the common /etc/hosts file to determine the local hostname based on the local IP.

Cheers.

---

### Post by justDIY on 2007-02-08
what daemon are you using for DHCP?   I was using dnsmasq on a wrt54g firewall, so it plays both roles.   I've since moved to a full BIND implementation on another server but it doesn't really make much difference.

If you check out nsswitch.conf I think there is a way to have the resolver check the hosts file first, and then the dns server

---

### Post by xdcdx on 2007-02-08
I am using Ubuntu's dhcp3-server package.

Yes, the resolver already checks first the /etc/hosts. My objection was that I do not want to rely on /etc/hosts for manually inverse resolving the hostname, but I would want the DHCP server to supply it to the initrd NFS image (this is already working) and the initrd NFS to properly set the hostname (this is failing), in the same way that you initially asked.

An alternative if the initrd NFS image can not (or will not) directly do this, and you do not have an available DNS server, would be to have a little DHCP client that asks the hostname to the DHCP server (not to the DNS server), without reconfiguring any ethernet device.

Anyway, here follows my solution, the script that gets the hostname from the hosts file. It was inspired by yours (thanks!). By the way, I think it is better to symlink it from /etc/rcS/, just after hostname.sh, than to do it on /etc/rc2/ like you suggested.

Cheers.


```

#!/bin/bash

# [http://www.ubuntuforums.org/showthread.php?t=297530](http://www.ubuntuforums.org/showthread.php?t=297530)
# put this file in /etc/init.d and symlink it from /etc/rcS/ just after hostname.sh

# get IP address
ip=`ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | cut -d' ' -f1`

# get hostname from hosts file
hostname=`cat /etc/hosts | grep $ip`
hostname=${hostname##*' '} # remove everything before the last ' '

# set hostname
echo "Hostname found:" $hostname
hostname $hostname
```

---

### Post by xdcdx on 2007-02-08
I have been doing some more experimentation, and this issue is solved in Ubuntu 6.10!

If /etc/hostname is missing, and the dhcp server passes the hostname with 'option host-name "foobar";' the initrd image picks it up and sets it correctly.

---

