---
title: "Need help is configuring samba in Ubuntu - Hardy"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Avinash.Rao on 2008-08-06
Hi,

I am trying to setup samba and below are the parameters that i have used in smb.conf file. My requirement is, about 20 winxp users will have to store data on the server. Can i configure the samba server in such a way that, when each user login with their own user id on winxp machine, it should should connect to their home directory on the samba server so that they store data on the server. Also, they should NOT be able to browser other directories.

I am aware that i have to create user accounts both in WinXP and the ubuntu server. I am doing this on a ubuntu studio 8.04 - AMD 64!

I am not using any domain controller or ADS, its just a simple workgroup network where all the winxp machines are part of the same workgroup. The windows machines are configured to use DHCP server that runs on the samba server.

I have entered the samba server IP and samba hostname in the lmhosts file on the winxp machine.

# Global parameters
[global]
workgroup = workgroup name
netbios name = samba server name
security = user

[homes]
comment = Home Directories
browseable = yes

The above configuration didn't work. When i browse the network on the winxp machine, it throws me an error saying i don't have permissions to browse the workgroup. I have updated the smb passwords on the samba server (smbpasswd -a username). 

Kindly help

---

### Post by fhsm on 2008-08-06
Hope you have better luck than I'm having getting samba help.  [I posted a very similar problem yesterday.]("http://ubuntuforums.org/showthread.php?t=881316")  If you ever do figure it out please post the solution that worked for you.

---

### Post by Avinash.Rao on 2008-08-07
Lets give it a shot.. 
What do you enter in /etc/samba/smbusers ? do you have to enter the usernames who require access. Cox, this file is empty on my server.

You have commented **";	valid users = %S"** you have uncomment this if you require userlevel access.






> **fhsm said:**
> Hope you have better luck than I'm having getting samba help.  [I posted a very similar problem yesterday.]("http://ubuntuforums.org/showthread.php?t=881316")  If you ever do figure it out please post the solution that worked for you.

---

### Post by dentaku65 on 2008-08-07
I suggest to configure in this way the smb.conf

Global Part
```
[global]
workgroup = <your_workgroup>
preferred master = No
local master = No
domain master = No
;hosts allow = 192.168.1.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
```

Share part
Example on a dir/share named testsmb, of course you can put your share name
```
[testsmb]
path = /home/<yourname>/testsmb
available = yes
browsable = yes
public = yes
writable = no
create mask = 0777

```

Restart Samba
```
sudo /etc/init.d/samba restart

```

---

### Post by Avinash.Rao on 2008-08-10
thanks, the workgroup network share worked with a lot of tweaking. Now, I am in need of configuring the samba as PDC. I have read the documentation and done what i understood as correct. I am having trouble executing the netlogon scripts. I have created the user accounts both on the linux server as well as on the WInXP machine, I have updated the lmhosts file on the winxp machine, but I am not able to join the machine to the Ubuntu PDC when i try this from the WinXP My computer properties, i get a authentication box and i am not able to authenticate with any user id.

can anybody help me with this?

> **dentaku65 said:**
> I suggest to configure in this way the smb.conf

Global Part
```
[global]
workgroup = <your_workgroup>
preferred master = No
local master = No
domain master = No
;hosts allow = 192.168.1.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
```

Share part
Example on a dir/share named testsmb, of course you can put your share name
```
[testsmb]
path = /home/<yourname>/testsmb
available = yes
browsable = yes
public = yes
writable = no
create mask = 0777

```

Restart Samba
```
sudo /etc/init.d/samba restart

```

---

### Post by cariboo on 2008-08-10
This maybe of some help, it has helped me in the past:

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

The document has varying scenarios as to setting up different types of networks.

Jim

---

### Post by Avinash.Rao on 2008-08-10
I am configuring samba using this link. The current status of samba service is that, the machine is able to join the domain without any problems, but is not able to execute the netlogon script automatically. I am able to execute the script manually but it doesn't execute when the user logs in. Below is the complete smb.conf file. My requirement is, users using winXP should be able to login to the domain and connect to their home directory to store all their files.

         # Global parameters
         [global]
         workgroup = abc
         netbios name = servername
         ;interfaces = eth1, lo
         ;bind interfaces only = Yes
         passdb backend = tdbsam

hosts allow = 100.0.0.0/8
         security = domain
         smb ports = 139
         add user script = /usr/sbin/useradd -m '%u'
         delete user script = /usr/sbin/userdel -r '%u'
         add group script = /usr/sbin/groupadd '%g'
         delete group script = /usr/sbin/groupdel '%g'
         add user to group script = /usr/sbin/usermod -G '%g' '%u'
         add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
         socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

        [share]
         comment = User Home Dir
         path = /export
         read only = No

;shutdown script = /var/lib/samba/scripts/shutdown.sh
;abort shutdown script = /sbin/shutdown -c
domain logons = Yes
preferred master = Yes
domain master = yes
wins support = Yes
os level = 65
logon path = \\%N\profiles\%U
logon drive = h:
logon home = \\%N\%U

;[homes]
;comment = Home Directories
;valid users = %S
;read only = No
;browseable = No

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
logon script =  /var/lib/samba/netlogon/logon.bat
guest ok = Yes
locking = No
read only = no

[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
profile acls = Yes

username map = /etc/samba/smbusers
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
smb ports = 139
name resolve order = wins bcast hosts
time server = Yes
printcap name = CUPS
show add printer wizard = No
shutdown script = /var/lib/samba/scripts/shutdown.sh
abort shutdown script = /sbin/shutdown -c
utmp = Yes
map acl inherit = Yes
printing = cups
veto files = /*.eml/*.nws/*.{*}/
veto oplock files = /*.doc/*.xls/*.mdb/


> **cariboo907 said:**
> This maybe of some help, it has helped me in the past:

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

The document has varying scenarios as to setting up different types of networks.

Jim

---

### Post by Avinash.Rao on 2008-08-10
I figured out pdbedit command and an option -S to add the logon script in for a user. But, even after adding the logon script for the user, the logon script doesn't seem to work at all. the command is: 

pdbedit -u username -S "\\\\servername\\netlogon\\scripts\\logon.bat"

When the users login, they should be able to map a network drive to the samba server to their respective home directories!

---

### Post by Avinash.Rao on 2008-08-12
can anyone help me??:guitar:

---

