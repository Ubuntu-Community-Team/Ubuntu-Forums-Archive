---
title: "Samba Share problem"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Uday123 on 2006-11-08
I have configured my Ubuntu server as an Active Directory member server.Samba Security is Winbind.
 Right now my server is in a Network(LAN).Whoever/Whereever in the network accessed my Ubuntu server(Thru windows m/n -> start->run->\\ubuntu), creating 2 directories under my home directory.The 2 directories are named by the UserName , MachineName logged in. Why it is happening? Can you please tell me the solution ...

My Samba configuration file: **/etc/samba/smb.conf**
# Global parameters
[global]
 unix charset = LOCALE
 workgroup = GTLGLOBAL
 netbios name = Ubuntu
 server string = Samba Server
 realm = AD.GLOBE.COM

# security
 security = ads
 encrypt passwords = Yes
 auth methods = winbind
 password server = ad.globe.com

# logging
 log level = 9
 syslog = 0
 log file = /var/log/samba/%m
 max log size = 50

# user info
  username map = /etc/samba/smbusers
  idmap uid = 10000-20000
  idmap gid = 10000-20000
  template shell = /bin/bash
 template home dir = /home/%U

# winbind
 winbind use default domain = yes
 winbind separator = +
 winbind enum users = No
 winbind enum groups = No
 winbind cache time = 300
 winbind nested groups = Yes

# server related
 allow trusted domains = No
 obey pam restrictions = yes
 domain logons = No
 add user script = /usr/sbin/useradd -s /bin/false '%u'
 client signing = no
 client use spnego = No
 client schannel = no

# printing
 printing = cups
 printer admin = "Domain Admins"

shares
[homes]
   comment = Home Directories
   browseable = no
   writable = yes
 This one is useful for people to share files

[tmp]
   comment = Temporary file space
   path = /tmp
   read only = no
   public = yes

---

