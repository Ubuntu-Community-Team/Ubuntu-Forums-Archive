---
title: "Can't connect to Samba server with &quot;force user&quot; option set"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by rrwright on 2008-08-17
Hey all,

I have a new Ubuntu 8.04 LTS server running as a PDC for a small school. It's a mixed XP/Macintosh (Leopard) environment for the users. Everything is working fine except that I have a Samba share called [school] for which I need to use the "force user" Samba option. When I do, neither Windows nor Mac clients can connect. If I comment out that one option and restart the samba server, it mounts just fine. Is there a problem in my [global] setting that is limiting the "force user" option, since I'm using LDAP?

If anyone is interested, I am trying to use the "force user" option because there is an issue with Leopard (OS X 10.5) where AFTER it copies a file, it runs a chmod on the file to give it the permissions of the original from the Mac desktop. This causes problems when sharing files among other users. OS X wants to set permissions to something like 644. If there is another way to get around this, I'm all ears, but the "force user" option should do it for our needs… except for this problem I'm having.

Thanks all! smb.conf posted below:


[global]
	ldap user suffix = ou=Users
	add group script = /usr/sbin/smbldap-groupadd -p "%g"
	passwd chat = *New*password* %n\n *Retype*new*password* %n\n *all*authentication*tokens*updated*
	delete group script = /usr/sbin/smbldap-groupdel "%g"
	socket options = TCP_NODELAY
	obey pam restrictions = no
	add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
	delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
	domain master = yes
	passwd program = /usr/sbin/smbldap-passwd %u
	passdb backend = ldapsam:ldap://localhost/
	ldap delete dn = Yes
	netbios name = ubuntu-server
	ldap passwd sync = Yes
	ldap group suffix = ou=Groups
	ldap machine suffix = ou=Computers
	ldap suffix = dc=cpcstl, dc=org
	local master = yes
	workgroup = workgroup
	logon path = \\192.168.10.11\home\%U\%a
	os level = 33
	add user script = /usr/sbin/smbldap-useradd -m "%u"
	ldap admin dn = cn=admin,dc=example,dc=com
	set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
	security = user
	add machine script = /usr/sbin/smbldap-useradd -w "%u"
	ldap idmap suffix = ou=Users
	panic action = /usr/share/samba/panic-action %d
	delete user script = /usr/sbin/smbldap-userdel "%u"
	domain logons = yes

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = yes
guest ok = yes
browsable = no


[home]
path = /home
read only = no
create mask = 0700
directory mask = 0700
browsable = no
allow hosts = 192.168.10.0/24

[shared]
writeable = yes
path = /home/shared
directory mode = 0770
comment = Shared Drive
create mode = 0770
browsable = yes
allow hosts = 192.168.10.0/24

[acs]
path = /home/acs
read only = no
browsable = yes
allow hosts = 192.168.10.0/24
create mode = 0770
directory mode = 0770

[school]
path = /home/shared/school
browsable = yes
writable = yes
force user = user1
valid users = user1,user2
force create mode = 0770
force directory mode = 0770

---

### Post by dmizer on 2008-08-17
This is because the share location is in the home directory. The local permissions will need to be adjusted to accommodate this option.

Please post the output of:
```
ls -l /home/shared
```

Edit:
Just for more information, this would not likely have been a problem if the share was not located in the /home directory.  Locating the shares in a directory like /media would have avoided this.

---

### Post by rrwright on 2008-08-17
Relevant output from that command:

```
drwxrwx--- 12 user1  school         4096 2008-08-17 18:33 School
```

user1 and user2 are in the same "school" group.

As a test, I created /school and changed the "path =" of that share to point to that folder. I set the permissions on that folder exactly as they are listed above. After restarting the samba server, I got exactly the same result.

Other thoughts? Thanks!

---

### Post by dmizer on 2008-08-17
Okay, remove the "force user", and add this option to the global section:
```
unix extensions = no
```

restart samba:
```
sudo /etc/init.d/samba restart
```

Fix found here: [http://bugs.contribs.org/show_bug.cgi?id=4164](http://bugs.contribs.org/show_bug.cgi?id=4164)

---

### Post by rrwright on 2008-08-17
Yes! That's it. Thank you very much!


> **dmizer said:**
> Okay, remove the "force user", and add this option to the global section:
```
unix extensions = no
```

restart samba:
```
sudo /etc/init.d/samba restart
```

Fix found here: [http://bugs.contribs.org/show_bug.cgi?id=4164](http://bugs.contribs.org/show_bug.cgi?id=4164)

---

