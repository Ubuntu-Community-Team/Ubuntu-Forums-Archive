---
title: "Where are samba [shares] in smb.conf??"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by geokok1981 on 2008-07-23
Hey. I 've just set up some shared folders between ubuntu and winxp and it works great. 
However I 've been reading all these guides and they all mention that in smb.conf you can restrict access to one ip like this:

[public, homeshare, whatever]

path=
host=10.0.0.1
mask etc etc.


However in smb.conf there is no such entry although I do have shared folders on my pc. What do I do to restrict the machines allowed to acces my shares? Does ubuntu store this  entry about shared folders somewhere else that needs to be edited appropriately?

---

### Post by df6269 on 2008-07-23
Here is my smb.conf file.
I can't make sure it will help for you.

[global]
workgroup = WORKGROUP
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
map to guest = Bad User
include = /etc/samba/dhcp.conf
logon path = \\%L\profiles\.msprofile
logon home = \\%L\%U\.9xprofile
logon drive = P:
usershare allow guests = Yes
add machine script = /usr/sbin/useradd -c Machine -d /var/lib/nobody -s /bin/false %m$
domain logons = No
domain master = No
security = user
[homes]
comment = Home Directories
valid users = %S, %D%w%S
browseable = No
read only = No
inherit acls = Yes
[profiles]
comment = Network Profiles Service
path = %H
read only = No
store dos attributes = Yes
create mask = 0600
directory mask = 0700
[users]
comment = All users
path = /home
read only = No
inherit acls = Yes
veto files = /aquota.user/groups/shares/
[groups]
comment = All groups
path = /home/groups
read only = No
inherit acls = Yes
[printers]
comment = All Printers
path = /var/tmp
printable = Yes
create mask = 0600
browseable = No
[print$]
comment = Printer Drivers
path = /var/lib/samba/drivers
write list = @ntadmin root
force group = ntadmin
create mask = 0664
directory mask = 0775
[COLOR="Blue"][bryan_data]
comment = bryan&#8217;s data
inherit acls = Yes
path = /tmp/data1
read only = No[/COLOR]

---

### Post by geokok1981 on 2008-07-23
Well this is just the thing. None of these appear on my smb.conf.

I have this shared: /home/username/sharedfolder And it works! It is indeed shared!!

Shouldn't there be something in smb.conf to point to this share and that I could modify similarly to your entry's???

---

### Post by dash86no on 2008-12-27
> **geokok1981 said:**
> Well this is just the thing. None of these appear on my smb.conf.

I have this shared: /home/username/sharedfolder And it works! It is indeed shared!!

Shouldn't there be something in smb.conf to point to this share and that I could modify similarly to your entry's???

This troubled me for a while as well. I found the answer here:

[http://ubuntuforums.org/showthread.php?t=749765&highlight=samba](http://ubuntuforums.org/showthread.php?t=749765&highlight=samba)

---

