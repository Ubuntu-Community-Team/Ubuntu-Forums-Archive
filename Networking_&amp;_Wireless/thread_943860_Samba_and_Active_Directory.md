---
title: "Samba and Active Directory"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by eurohim on 2008-10-10
I have Ubuntu Server 8.04 loaded up with Samba during the install and I joined the test Active Directory server I set up with likewise-open.

What I want to do is share some drives via the command line since I have no GUI on there and I don't want one. I can't seem to get that working. All it seems to be is adding a line to smb.conf, but I can't get that to work. It's simple enough to right-click on any file in Gnome and add a share, but I'm having issues via the smb.conf file.

But wait, there's more! I want whoever is connecting to these shares to authenticate through Active Directory. Is this possible to do? The goal is for it to be a file server on a Windows 2003 network with Active Directory.

---

### Post by eurohim on 2008-10-11
Also, I was hoping to get the proper language for the smb.conf file by creating a share via the gui on another computer and seeing what changes it made, but apparently it doesn't store the share info in /etc/samba/smb.conf. Maybe I'm thinking with too much of a windows mindset, but are you not able to share any folder you want individually or must it be home directories like there is already an uncomment option for in smb.conf?

---

### Post by eurohim on 2008-10-13
I figured part 1 out:

[global]
workgroup = WKG
netbios name = MYNAME
[share1]
path = /tmp
[share2]
path = /my_shared_folder
comment = Some random files

You set up the code as above where [share1] is the name of the share, etc and you can just add that to the end of your smb.conf file.

Now, I just need to figure out how to get it to authenticate with Active Directory.

---

### Post by eurohim on 2008-10-13
I finally got it all working together. Since I got no responses, I assume nobody really cares, but if you want to know, just reply and I'll put my notes in here.

---

### Post by f8l_0e on 2008-10-20
I'd be interested in how you did it.

---

### Post by eurohim on 2008-10-22
> **f8l_0e said:**
> I'd be interested in how you did it.
Sure, here are my step by step notes (6 pages):

STEP 1: SET UP KERBEROS

[http://wiki.samba.org/index.php/Samba_&_Active_Directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory)

Edit /etc/krb5.conf

Use the data below with tweaks for domain like omega.local is your fqdn and ad1.omega.local is your Active Directory Server Name.
---------------------------------------------

[logging]
default = FILE:/var/log/krb5libs.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmind.log

[libdefaults]
default_realm = OMEGA.LOCAL
dns_lookup_realm = false
dns_lookup_kdc = false
ticket_lifetime = 24h
forwardable = yes

[realms]
OMEGA.LOCAL = {
   kdc = ad1.omega.local
   admin_server = ad1.omega.local
   default_domain = omega.local
}

[domain_realm]
.kerberos.server = ad1.omega.local
.ad1.omega.local = AD1.OMEGA.LOCAL

[kdc]
profile = /var/kerberos/krb5kdc/kdc.conf

[appdefaults]
pam = {
   debug = false
   ticket_lifetime = 36000
   renew_lifetime = 36000
   forwardable = true
   krb4_convert = false
}


---------------------------------------------------------

To test the above do the command:

kinit [email]administrator@OMEGA.LOCA[/email]L

Make administrator whatever user you want to authenticate with.

==================================================================================

STEP 2: SET UP SAMBA

Edit /etc/samba/smb.conf

-------------------------
[global]

workgroup = LOCALDOMAIN
realm = LOCALDOMAIN.NET
server string = %h server (Samba %v, Ubuntu)
wins server = 192.168.1.100
password server = DCSERVER
enable privileges =Yes
allow trusted domains = No
dns proxy = no
name resolve order = host wins bcast
log file = /var/log/samba/log.%m
max log size = 1000
log level = 3
security = ADS
encrypt passwords = true
socket options = TCP_NODELAY
time server = Yes
map to guest = nobody
idmap uid = 16777217-33554431
idmap gid = 16777217-33554431
winbind enum users = yes
winbind enum groups = yes
printcap name = cups
printing = cups
cups options = raw
template shell = /bin/bash



#======================= Share Definitions =======================
[data]
comment = Share Data
path = /home/data
read only = No
create mask = 0775
directory mask = 0775
browsable = Yes
public = Yes
writeable = Yes
force create mode = 0775
force directory mode = 0775
force security mode = 0775
guest ok = no
inherit permissions = yes
nt acl support = yes

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700
-------------------------------------------------------------

Test file with sudo testparm

Restart Services in this order:
root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba restart
root@ubuntuserver:/#sudo /etc/init.d/winbind start

The next step is to make sure the time is synchronized with the domain by typing:
root@ubuntuserver:/#sudo net time set

It is now the moment of truth. Type the following to add the linux server to the AD Domain:
root@ubuntuserver:/#sudo net ads join –U Administrator

Now, stop Samba & Winbind for the next steps using the following:
root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba stop
==================================================================================

Step 3: Adding this list to the password list.

The next step is to get the passwd command to check the winbind list for usernames and groups. This is fairly straight forward as it only involves changing one file, /etc/nsswitch.conf and at that fairly minimally. Of course, backup this file before changing it. 

-------------------------------------------
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: compat winbind
group: compat winbind
shadow: compat winbind

hosts: files dns wins
networks: files dns

protocols: files
services: files
ethers: files
rpc: files
netgroup: files
publickey: nisplus
automount: files
aliases: files nisplus
-------------------------------------------------

Save your changes, and start samba and Winbind in the following order:
root@ubuntuserver:/#sudo /etc/init.d/samba start
root@ubuntuserver:/#sudo /etc/init.d/winbind start



Verify that Winbind is working. Use the Winbind utility wbinfo to list users and groups from the AD Domain Controller.

root@ubuntuserver:/#sudo wbinfo –u
LOCALDOMAIN\Administrator
LOCALDOMAIN\Guest
LOCALDOMAIN\Mhinrichsen
LOCALDOMAIN\User
…

root@ubuntuserver:/#sudo wbinfo –g
LOCALDOMAIN\Domain Computers
LOCALDOMAIN\Admins
LOCALDOMAIN\Guests
LOCALDOMAIN\Domain Users

Verify that logins and passwords are coming from the AD Domain Controller as well as the local files:
root@ubuntuserver:/#sudo getent passwd
If Winbind is working you will see the LOCALDOMAIN\ prefix. If not you will probably just see the local accounts on the linux server.


The final Winbind test is to run net ads info to display the AD server information.

root@ubuntuserver:/#sudo net ads info

LDAP server: 192.168.1.100
LDAP server name: DCSERVER
Realm: LOCALDOMAIN.NET
Bind Path: dc=LOCALDOMAIN, dc=NET
LDAP port: 389
Server time: Wed, 18 Oct 2006 18:02:18 EDT
KDC server: 192.168.1.100
Server time offset: 0




===================================================================================

Step 3: Setting up PAM Authentication for Active Directory.

root@ubuntuserver:/#vim /etc/pam.d/samba
----------------------------------------------------------
@include common-auth
@include common-account
@include common-session
@include common-password
----------------------------------------------------------



root@ubuntuserver:/#vim /etc/pam.d/common-account
-----------------------------------------------------------
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system. The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account required pam_unix.so
-----------------------------------------------------------



root@ubuntuserver:/#vim /etc/pam.d/common-auth
-----------------------------------------------------------
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.). The default is to use the
# traditional Unix authentication mechanisms.
#
auth required pam_env.so
auth required pam_unix.so
-----------------------------------------------------------



root@ubuntuserver:/#vim /etc/pam.d/common-password
-----------------------------------------------------------
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
#used to change user passwords. The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.
password sufficient pam_windbind.so
password required pam_unix.so nullok obscure min=4 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required pam_cracklib.so retry=3 minlen=6 difok=3
# password required pam_unix.so use_authtok nullok md5
-----------------------------------------------------------



root@ubuntuserver:/#vim /etc/pam.d/common-session
-----------------------------------------------------------
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive). The default is pam_unix.
#
session required pam_limits.so
session required pam_unix.so
-----------------------------------------------------------

====================================================================================

Step 4: Restart services
Restart Services in this order:
root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba restart
root@ubuntuserver:/#sudo /etc/init.d/winbind start

---

