---
title: "Help with SADMS"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by langelo91 on 2008-04-06
Im getting this problem:

----------------------------------------------------------------------------
 ---
S A D M S  2.0.12
Samba as Active Directory Member Server
[email]bbou@ac-toulouse.fr[/email]
 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
 - -
install
 ----------------------------------------------------------------------------
 ---
[BEGIN]
[1]
+fix bugs/incompatibilities
disable avahi-daemon automatic startup
disable fam automatic startup
[2]
+customize krb5.conf
install new krb5.conf to /etc
[3]
+get current samba version for smb.conf syntax
samba minor version is 24
+samba config switches
map id from rids using old syntax
include sample shares
+customize smb.conf
install new smb.conf to /etc/samba
+customize user.map
install new user.map to /etc/samba
+creating sample data folder in /data shared as data
[4]
+ping kdc server
ok
[5]
+sync clocks with kdc
local time was: 2008-04-06 10:09.09
synchronizing with server
net time is now:2008-04-06 10:09.10
local time is now:2008-04-06 10:09.10
[6]
+get Kerberos ticket-granting ticket for principal
[email]Administrator@LCOMPUTER.HOME[/email]
got ticket-granting ticket for principal krbtgt/LCOMPUTER.HOME@LCOMPUTER.HOME
[7]
+get current samba version for join domain syntax
samba minor version is 24
+join domain to Computers
join failed and returned 255
[7>] with error
log extract
vvvvv
Apr  6 10:08:52 linux sadms: sadms start Apr  6 10:09:25 linux sadms: sadms finish error 7 join domain ^^^^^ [END] 

Failed to set servicePrincipalNames. Please ensure that the DNS domain of this server matches the AD domain, Or rejoin with using Domain Admin credentials.
[ERROR]
returned error code 7
command line was <./_install.sh   'LCOMPUTER.HOME' 'lcomputer.home' 'server' 
'LCOMPUTER' 'linux' 'Computers' 'Administrator' '*****' 'Administrators' 
'192.168.1.0/255.255.255.0' ''>
---------------------------------------------------------------

What should I do?

---

### Post by vitalsignstechnology on 2008-04-08
Take a look at the nsswitch.conf file.

Verify that the "winbind" is on the passwd: and group: line

Also verify the configuration of pam.d. SAMDS puts the actual config files in /tmp/pam.d

you need to copy those files into /etc/pam.d/

MAKE SURE you backup the files that will be modified. If you mis-edit the nsswitch.conf you can make it impossible to login.

Patrick Wilson
pwilson at vitalsignstechnology period(aka dot) com

---

### Post by langelo91 on 2008-06-09
my nsswitch.conf:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:     compat
group:      compat
shadow:     compat

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
networks: files

protocols:     db files
services:      db files
ethers:        db files
rpc:           db files

netgroup:      nis

---

