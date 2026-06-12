---
title: "Samba announce lan only"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-09-01
From time to time do I connect to a vpn and have noticed that samba is broadcasting (udp port 137 & 138) on the vpn network. What would be preferred was that samba only broadcasted on the local network 192.168.1.0/24

---

### Post by coffee412 on 2011-09-01
I think you can change that in the smb.conf file. There is a setting in there to tell it which network address to broadcast on.

Im not a wiz-bang on samba/windows but I think this is the area you are looking for in the file:

> # ----------------------- Network-Related Options -------------------------
#
# workgroup = the Windows NT domain name or workgroup name, for example, MYGROUP.
#
# server string = the equivalent of the Windows NT Description field.
#
# netbios name = used to specify a server name that is not tied to the hostname.
#
# interfaces = used to configure Samba to listen on multiple network interfaces.
# If you have multiple interfaces, you can use the "interfaces =" option to
# configure which of those interfaces Samba listens on. Never omit the localhost
# interface (lo).
#
# hosts allow = the hosts allowed to connect. This option can also be used on a
# per-share basis.

# hosts deny = the hosts not allowed to connect. This option can also be used on
# a per-share basis.
#
    workgroup = MYGROUP
    server string = Samba Server Version %v

;    netbios name = MYSERVER

; **   interfaces = lo eth0 192.168.12.2/24 192.168.13.2/24**
;    hosts allow = 127. 192.168.12. 192.168.13.

---

