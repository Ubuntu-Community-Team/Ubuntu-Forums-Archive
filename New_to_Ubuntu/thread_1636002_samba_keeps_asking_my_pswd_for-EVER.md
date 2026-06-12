---
title: "samba keeps asking my pswd for-EVER"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by Salvagluque on 2010-12-02
Hello guys,
This is a extract of this thread, hope is useful:
[http://wwww.ubuntuforums.org/showthread.php?p=10187785#post10187785](http://wwww.ubuntuforums.org/showthread.php?p=10187785#post10187785)

It turns out Samba keeps asking me forever for my password, no matter how many times I write it even if is correct any time.

I don't know why this happens. One machine has the ubunu 10.10 and the other one the 9.10. I tryed installing samba4 in both but that just got it worse so I uninstalled the samba 4 relalted packages from synaptic and reinstalled the ones taken out.

Thanks in advance

Salvador


______

post the output of the following commands

Code:

```
net usershare info --long
```

Code:

```
 testparm -s
```

Morbius1 is online now 
__________



here they are:

[música]
path=/home/salvador/Música
comment=
usershare_acl=Everyone:F,
guest_ok=n

[documentos]
path=/home/salvador/Documentos
comment=
usershare_acl=Everyone:F,
guest_ok=n




Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
usershare allow guests = Yes
usershare owner only = No
panic action = /usr/share/samba/panic-action %d

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers



___________


Actually, everything looks to be in order. Both of your shares have guest access disabled ( guest_ok=n ) so you're going to have to create users and give them samba passwords in order for the remote user to gain access.

Are you sure you don't want to allow guest access? If you do then just go back into Nautilus and click on the guest access option.

If you really want to limit access to users with usernames and passwords then it's a two step process:

Let's say you have a remote user named morbius:

(1) Create a local user with no home folder and no local login capability:
Code:

```
sudo useradd -s /bin/true morbius
```

(2) Then give morbius a samba password to use to connect to the share:
Code:

```
sudo smbpasswd -a morbius
```

But the easiest way is to allow guest access

---

