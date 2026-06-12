---
title: "Get ubuntu to see netbios names in ubuntu"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by jbizcocho on 2008-01-25
I have googled, tried various combinations of files in my /etc/nsswitch.conf file, I've been taken to posts on this forum and elsewhere.  I've been told I need to setup a DNS server for my local network which is overkill for 3-4 PC's and only one linux PC with the problem.

Here is the problem:
I installed gutsy in October on my laptop a thinkpad t23 and within a few hours, I could get it to see and share a drive using the IP address of my server.  I have 3 machines in my network.  My DHCP server is my wireless modem and my linksys simply provides the wireless function and security.  I can ping all machines by ip but I can't ping by netbios name and I suspect that is why I can neither share files on my laptop or view the other workstations via network neighborhood.

I know how to add each individual IP to the LMHOSTS file which is what I've been doing but I really need for them to talk to the network using the wins, netbios, or whatever mixture makes it work.

I have samba installed, I have winbind, etc.

below is my /etc/nsswitch.conf file please let me know anything else I need to do, show or verify.
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

#hosts:          wins dns mdns4 files mdns4_minimal [NOTFOUND=return]
hosts:          wins files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# netgroup:       nis

---

