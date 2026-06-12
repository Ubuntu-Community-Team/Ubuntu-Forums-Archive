---
title: "Seeking De-Centralized DNS Alternative"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by pboin on 2006-09-20
I have a mixed environment, all sorts of machines are brought up and down running a variety of operating systems.  DHCP is offered by a Linksys router, but unfortunately it doesn't do DNS.

Currently, I've been running dnsmasq on a debian box, but for various reasons, I want that to go away.

There must be some way that linux boxes can broadcast and respond for hostnames **other than DNS**.  I think in windows-speak we'd be refering to 'winbind'.  Machines and their NetBIOS names show up in Network Neighborhood **without a DNS server**.  That's more or less what I want to do with linux boxes.

Can someone help me figure out the name of what I'm looking for please?  Once I know that, I should be good-to-go.

Thanks.

---

### Post by mssever on 2006-09-20
I use plain old DNS (BIND9). Never heard of dnsmasq. Of course, that doesn't work well if a given machine's IP is subject to change. You could run your own DHCP server. I've never messed with such a server, but I do know that it's possible to control the hostnames that way (at least it was with BOOTP).

---

### Post by kerry_s on 2006-09-20
i run dnsmasq and i use open dns for dns > [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

here's what i put in my /etc/dhcp3/dhclient.conf

prepend domain-name-servers 127.0.0.1, 208.67.222.222, 208.67.220.220;

just drop 127.0.0.1 if you don't want to use dnsmasq, looks like this>

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

If your going to keep dnsmasq(127.0.0.1) don't worry about the opendns failing it does use it just not first.

Edit: I just read your post again and i don't think this is what your looking for. I don't think i really understand your problem. You get your dhcp from your router(so that's for internet), now i think your saying you need dns to network the computer's? You might be looking for samba.

a LanManager-like file and printer server for Unix
The Samba software suite is a collection of programs that
implements the SMB/CIFS protocol for unix systems, allowing you to serve
files and printers to Windows, NT, OS/2 and DOS clients. This protocol
is sometimes also referred to as the LanManager or NetBIOS protocol.

This package contains all the components necessary to turn your
Debian GNU/Linux box into a powerful file and printer server.

Currently, the Samba Debian packages consist of the following:

 samba - LanManager-like file and printer server for Unix.
 samba-common - Samba common files used by both the server and the client.
 smbclient - LanManager-like simple client for Unix.
 swat - Samba Web Administration Tool
 samba-doc - Samba documentation.
 samba-doc-pdf - Samba documentation in PDF format.
 smbfs - Mount and umount commands for the smbfs (kernels 2.2.x and above).
 libpam-smbpass - pluggable authentication module for SMB/CIFS password database
 libsmbclient - Shared library that allows applications to talk to SMB/CIFS servers
 libsmbclient-dev - libsmbclient shared libraries
 winbind: Service to resolve user and group information from Windows NT servers
 python2.4-samba: Python bindings that allow access to various aspects of Samba

It is possible to install a subset of these packages depending on
your particular needs. For example, to access other SMB/CIFS servers you
should only need the smbclient and samba-common packages.

[http://www.samba.org/](http://www.samba.org/)

---

### Post by Iowan on 2006-09-20
Ther are options which can be pased to a DHCP Server (at least DHCP3) which allow it to keep track of hostnames... but I don't have the details.

---

