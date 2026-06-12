---
title: "[URGENT] Configuring NIS on Gutsy/Hardy"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by technomaniac on 2008-08-01
We wish to install Ubuntu Gutsy or Hardy on all our college desktops. The NIS server runs on Red Hat Enterprise 5. However even after trying everything, we are unable to get NIS work on Ubuntu. Earlier the desktops ran Redhat Enterprise WS and NIS worked perfectly. 

The following things have been done

the following lines have been added to the files

/etc/networks
NETWORKING=yes
HOSTNAME=<desktop_number>.computercentre.<mycollegename>.ac.in
NISDOMAIN=computercentre.<mycollegename>.ac.in

where <desktop_number> is the unique name given to each desktop like ccc77,ccc25 etc
/etc/hosts
<IP address of the desktop> <desktop_number>.computercentre.<mycollegename>.ac.in <desktop_number>
<IP address of NIS server> nis1.computercentre.<mycollegename>.ac.in nis1

yp.conf
domain computercentre.<mycollegename>.ac.in server <IP address>
ypserver nis.computercentre.<mycollegename>.ac.in

fstab
<IP address>:/home /home nfs dev,suid,rw,exec 1 1


Is the above config okay?
Why is NIS not getting configured?
I need urgent help

---

