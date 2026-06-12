---
title: "how to connect to a windows network?"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by gaarheidswafel on 2008-10-10
Dear Linux users.

How can I connect to a windows network (windows server 2003) (its the network of my University) via Ubuntu?

My system is Linux--> Ubuntu-->Hardy --> Heron --> 8.04


I can't get in my network menu under the System tab via the GUI (gnome)
Samba in the terminal doesn't work either. VPN client needed? :confused:

I can be root of my own system, but not in the network of course.

Thanks in advance.

---

### Post by gaarheidswafel on 2008-10-17
Problems are already solved.

i had to make a mount point.
Here how it has to be done as root:
goto /etc/samba via the terminal
type gedit samba.conf

use ctrl f to find global settings:

change the workgroup name into the domain name of the server.
below type: server string = %h server (Samba, Ubuntu)

at win server type the name of the server
at Authentication type guest account = [username]

At netlogon type # Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

save the file

than edit fstab in /etc to make a mount point and put in /mnt if you want it to start up by booting the computer.

mount with the command mount -t smbfs -o username=blabla, password= blabla //site you want to mount

than is should work

---

