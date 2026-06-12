---
title: "Registry setting for Samba in Win10?"
date: 2021-11-27
forum: Networking &amp; Wireless
---

### Post by johnzbesko on 2021-11-27
I have 2 Win10 Home laptops and 2 Kubuntu  desktop/server PC's (20.04 and 18.04.) The older Win10 laptop is able to connect to samba shares on both PC's. Sometime in the past, I had to muck around with its registry to get it to connect. I forgot what I did.

The newer laptop won't connect. I have been able to get it to "find" all the other "window" machines on my home network- the 2 servers, the other laptop and a virtual win7 machine on one of the servers. When trying to connect, the laptop keeps asking for an account/password which then never works.

The last lines of /var/log/samba/samba.log:

[2021/11/27 14:34:56.123044,  0] ../../lib/param/loadparm.c:815(lpcfg_map_parameter)
  Unknown parameter encountered: "password level"
[2021/11/27 14:34:56.123131,  0] ../../lib/param/loadparm.c:1855(lpcfg_do_global_parameter)
  Ignoring unknown parameter "password level"
[2021/11/27 14:34:56.123450,  0] ../../lib/param/loadparm.c:815(lpcfg_map_parameter)
  Unknown parameter encountered: "update encrypted"
[2021/11/27 14:34:56.123483,  0] ../../lib/param/loadparm.c:1855(lpcfg_do_global_parameter)
  Ignoring unknown parameter "update encrypted"
[2021/11/27 14:34:56.123728,  0] ../../lib/param/loadparm.c:815(lpcfg_map_parameter)
  Unknown parameter encountered: "winbind trusted domains only"
[2021/11/27 14:34:56.123760,  0] ../../lib/param/loadparm.c:1855(lpcfg_do_global_parameter)
  Ignoring unknown parameter "winbind trusted domains only"
[2021/11/27 14:34:56.124787,  0] ../../source3/param/loadparm.c:4093(lp_load_ex)
  lp_load_ex: Max protocol NT1 is less than min protocol SMB3.

My searching the internet has brought up various registry fixes involving NTLM levels, etc. and Windows Features settings, but I haven't found the missing key. BTW, the new laptop is able to connect to the virtual Win7 machine.

Any help is greatly appreciated!

---

### Post by rsteinmetz70112 on 2021-11-29
Not knowing how your Samba is set up assuming it is an NT4 style domain this link has the various settings. Perhaps you could compare the registry on the computer that works and see whihc ones you need:
[https://wiki.samba.org/index.php/Required_Settings_for_Samba_NT4_Domains](https://wiki.samba.org/index.php/Required_Settings_for_Samba_NT4_Domains)

---

### Post by johnzbesko on 2021-11-29
Thanks for your reply! I fixed the problem with the "Max protocol NT1 is less than min protocol SMB3." I thought (and tried) to compare the two registries, but they are too large and different enough that I have not been successful. The newer laptop (the one that won't connect to samba) does connect to the older laptop and to the virtual Win7 machine. Is there a simple way to monitor the communication between the two laptops and the samba server?

Here's the smb.conf

[global]
netbios name = ZAMD64
server string = Samba file and print server
workgroup = zbesko
client max protocol = SMB3
client min protocol = NT1
lanman auth = yes
ntlm auth = yes
security = user
hosts allow = 192.168.1.
interfaces = 127.0.0.1/8 192.168.1.0/24
bind interfaces only = yes
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = yes
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[Home]
path = /home
comment = No comment
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
locking = no
strict locking = no

---

### Post by johnzbesko on 2021-11-29
I did check out the link you provided. I think I already came across it before. Anyway, doing a "find" on the working laptop registry failed to bring up the keys mentioned in the link.

---

### Post by johnzbesko on 2021-12-03
To summarize:

1) Two desktops, one virtual Win7, and an older Win10 laptop are all able to connect shares with each other.
2) The new laptop detects all the other machines but cannot connect to the samba desktop machines.
3) The desktops, using dolphin and "smb://user@ipaddress" are able to connect and transfer files to the new laptop.
4) Using a verbose setting for samba.log on the ubuntu desktop, I find this relevant section:

  Got user=[pamela] domain=[.] workstation=[PDASUS] len1=24 len2=224
  Mapping user [.]\[pamela] from workstation [PDASUS]
  check_ntlm_password:  Checking password for unmapped user [.]\[pamela]@[PDASUS] with the new password interface
  check_ntlm_password:  mapped user is: [.]\[pamela]@[PDASUS]
  Auth: [SMB2,(null)] user [.]\[pamela] at [Fri, 03 Dec 2021 19:44:45.496971 CST] with [NTLMv2] status [NT_STATUS_LOGON_FAILURE] workstation [PDASUS] remote host [ipv4:192.168.1.101:56374] mapped to [.]\[pamela]. local host [ipv4:192.168.1.247:445] 
  {"timestamp": "2021-12-03T19:44:45.497062-0600", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 2}, "eventId": 4625, "logonId": "0", "logonType": 3, "status": "NT_STATUS_LOGON_FAILURE", "localAddress": "ipv4:192.168.1.247:445", "remoteAddress": "ipv4:192.168.1.101:56374", "serviceDescription": "SMB2", "authDescription": null, "clientDomain": ".", "clientAccount": "pamela", "workstation": "PDASUS", "becameAccount": null, "becameDomain": null, "becameSid": null, "mappedAccount": "pamela", "mappedDomain": ".", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": null, "passwordType": "NTLMv2", "duration": 1456}}

It doesn't matter what user I use. Can anyone tell me what's going on?

---

### Post by Morbius1 on 2021-12-04
This post is more informational than helpful but I don't think you are going to get much help with the way your server is set up since it appears you are using gadmin-samba.

There aren't many people left that remember how most of the options you are using work since they are all from Samba Version 2 / 3 days. There used to be a rather intimidating book that described some of those options but it isn't referenced anymore.

*[COLOR="#0000FF"]Fun Fact: The only reason gadmin-samba is still in the repository is because it is a reverse dependency of gadmintools which probably should not be used any more either. [https://bugs.launchpad.net/ubuntu/+source/gadmin-samba/+bug/1826458](https://bugs.launchpad.net/ubuntu/+source/gadmin-samba/+bug/1826458)[/COLOR]*

There is a backup of the original smb.conf stored at     /usr/share/samba/smb.conf which you can copy to the /etc/samba/ location should you decide to just start over with the defaults.

---

### Post by johnzbesko on 2021-12-04
Thank you for your advice. I tried using the original smb.conf, modified a little bit, and now the new laptop CAN access the ubuntu shares! I did discover, however, that, while the older Win10 laptop connect also still connect, the virtual Win7 cannot. At least, however,I have a new starting point at which to debug and configure.

---

