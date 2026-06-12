---
title: "Help with DHCP server error"
date: 2021-08-15
forum: Networking &amp; Wireless
---

### Post by spschneer on 2021-08-15
Help...

I've been working on a problem with my home network's DHCP server for a week now and have made little or no progress and could use a new set of eyes (or something)...

Background...

Home server for file storage running Ubuntu 20.04 LTS with DNS, DHCP, Samba, and that's pretty much it.  Very straighforward configuration done with Webmin and everything seems to be working fine except for the startup of my DHCP server....

I'm getting the error "Can't create PID file /run/dhcp-server/dhcpd.pid: No such file or directory." in my syslog at startup.  I've researched (extensively) and it appears this is a known bug that has existed in isc--dhcp-server since 2012 (or maybe earlier).  It is caused by the directory for the dhcpd.pid file being on /run/ and not being created when DHCP attempts to write the newly started task's pid into it.  

Initially, I tried modifying the startup script and couldn't get that to work properly so I figured I'd run a batch script at boot-up to mkdir the directory.  That worked fine but the startup script still failed when trying to write the pid (since it didn't exist).  Next I tried to add "touch /run/dhcpd.pid" to the script to create the file but no luck there either...

HELP...

Thanks in advance. 

S

---

