---
title: "LDAP User for Samba Share"
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by e.ms on 2017-07-27
Hello everybody

I have a very big problem with the installation of LDAP and Samba. I want to install both servers on separate servers. I also do not want a Samba domain controller.

Here's my scenario:
[LIST]
[*]LDAP Server (16.04) 192.168.1.195 
[*]Samba Server (16.04) 192.168.1.197 
[*]Client (16.04) 192.168.1.198 
[*]I do not want a Samba PDC 
[*]I need Samba on a separate server 
[/LIST]

I have done this:

**LDAP Server**
nano /etc/hostname #change
```
LDAP.local.net
```

reboot
apt-get install slapd ldap-utils
nano /etc/ldap/ldap.conf #change
```
BASE    dc=local,dc=net
URI     ldap://localhost:389
```

dpkg-reconfigure slapd
[LIST]
[*]No 
[*]local.net 
[*]local.net 
[*]MDB 
[*]No 
[*]Yes 
[*]No 
[/LIST]

apt-get install phpldapadmin
nano /etc/phpldapadmin/config.php #change
```
$servers->setValue('server','name','LDAP Server');
$servers->setValue('server','host','192.168.1.195');
$servers->setValue('server','base',array('dc=local,dc=net'));
$servers->setValue('login','bind_id','cn=admin,dc=local,dc=net');
// $config->custom->appearance['hide_template_warning'] = true;
```

reboot

**SAMBA & CLIENT**
apt-get install ldap-auth-client nscd
dpkg-reconfigure ldap-auth-config
apt-get -y install libpam-pwquality
nano /etc/nsswitch.conf #change
```
passwd:        compat ldap
group:        compat ldap
shadow:        compat ldap
```

nano /etc/pam.d/common-password #change
```
password        requisite                       pam_pwquality.so retry=3 minlen=12 minclass=4 lcredit=-1 ucredit=-1 dcredit=-1 ocredit=-1 maxsequence=3
password        [success=2 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512 remember=5
```

nano /etc/pam.d/common-account #add
```
account required                        pam_access.so
```

nano /etc/pam.d/common-session #add
```
session required    pam_mkhomedir.so skel=/etc/skel umask=0077
```

**SAMBA-SERVER**
apt-get install samba
mkdir /files
chmod 770 /files
mkdir /files/data
chmod 770 /files/data
nano /etc/samba/smb.conf #add/change
```
[global]
workgroup = local.net

#   passdb backend = tdbsam

# LDAP Settings
   passdb backend = ldapsam:ldap://192.168.1.195
   # Der LDAP-Suffix
   ldap suffix = dc=local,dc=net
   # Admin-DN
   ldap admin dn = cn=admin,dc=local,dc=net
   # User-, Gruppen- und Maschinen-Suffix
   ldap user suffix = ou=Users
   ldap group suffix = ou=Groups
   ldap machine suffix = ou=Computers
   ldap idmap suffix = ou=Idmap
   ldap delete dn = no
   ldap passwd sync = yes
   unix password sync = yes
   # or off if TLS/SSL is not configured
   #ldap ssl = start tls
   #ldap ssl = <no/ssl/start_tls>
   ldap ssl = no

# Scripte zum Hinzufügen/Löschen von Usern, Gruppen und Maschinen
   add user script = /usr/sbin/smbldap-useradd -m -a %u
   delete user script = /usr/sbin/smbldap-userdel %u
   add group script = /usr/sbin/smbldap-groupadd -p %g
   delete group script = /usr/sbin/smbldap-groupdel %g
   add user to group script = /usr/sbin/smbldap-groupmod -m %g %u
   delete user from group script = /usr/sbin/smbldap-groupmod -x %g %u
   set primary group script = /usr/sbin/smbldap-usermod -g %g %u
   add machine script = /usr/sbin/smbldap-useradd -i -w %u

[data]
  comment = Data
  path = /files/data
  browseable = yes
  read only = no
  guest ok = no
```

smbpasswd -w "LDAP admin Password"
chown testuser:users /files/data/

On the client I can log on with the LDAP users. I also see
[LIST]
[*]Getent passwd 
[*]Getent group 
[/LIST]
The users and groups.
However, I do not get a connection to my Samba server.

Does no one have an idea?

---

