---
title: "Problem with samba share"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by jh62 on 2018-09-06
Dear all
 
I’m running an Ubuntu 14.0.4 server with csf and lfd v12.06 and I’m trying to setup a samba share. I do not really care if it needs a user account to access or that it is anonymous accessible from my own network. 
I’m using 2 windows 10 machines and a printer to access the samba share’s.\
I’m however running into problems. I cannot do the following:

[LIST=1]
[*]Detect the server in the windows network sharing center
[*]Access the samba shares. When adding them to windows I do get a screen to enter my logon details which I do but those are refused and I get again the logon screen.
[/LIST]
I can do the following:

[LIST]
[*]Ping my server IP address from all devices on the network.
[/LIST]
I tried the following:

[LIST]
[*]Add samba permissions to ufw firewall.
[*]Reinstalling samba
[*]Rebooting server
[*]Sharing a folder from Nautilus
[*]Installing a samba GUI and reconfigure from there
[*]Reconfigure samba from Webmin which I have installed
[/LIST]
My internal network is configured as follow:

[LIST]
[*]Netgear router connected to external internet with wifi
[*]Second Linksys router as accesspoint for both Ethernet and wifi connected trough Ethernet to netgear router
[*]Server connected trough Ethernet to Linksys router
[*]Other computes both connected trough Ethernet and wifi.
[/LIST]
 
Please find below by settings file for samba. I tried to remove all lines starting with a # to make it more readable.
 
Does anyone has any advice on what I’m doing wrong or how to debug my system?


```
#======================= Global Settings =======================
 
[global]
 
workgroup = workgroup
 
server string = GIUN_server
 
 
;   wins server = w.x.y.z
 
 
dns proxy = no
 
#### Networking ####
 
;   interfaces = [127.0.0.0/8]("http://127.0.0.0/8") eth0
 
;   bind interfaces only = yes
 
 
 
#### Debugging/Accounting ####
 
log file = /var/log/samba/log.%m
 
max log size = 1000
 
 
syslog = 0
 
panic action = /usr/share/samba/panic-action %d
 
 
####### Authentication #######
 
server role = standalone server
 
; passdb backend = tdbsam
 
obey pam restrictions = yes
 
unix password sync = yes
 
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 
pam password change = yes
 
map to guest = bad user
 
########## Domains ###########
 
;   logon path = [\\%N\profiles\%U]("file:///\\%25N\profiles\%25U")
 
;   logon drive = H:
;   logon script = logon.cmd
 
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
 
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
 
; add group script = /usr/sbin/addgroup --force-badname %g
 
############ Misc ############
 
;   include = /home/samba/etc/smb.conf.%m
 
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
 
 
; usershare max shares = 100
 
usershare allow guests = yes
username map = /etc/samba/smbusers
security = user
; encrypt passwords = yes
; guest ok = no
; guest account = nobody
 
#======================= Share Definitions =======================
 
;[homes]
;   comment = Home Directories
;   browseable = no
 
;   read only = yes
 
;   create mask = 0700
 
;   directory mask = 0700
 
;   valid users = %S
 
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
 
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700
 
[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
; guest ok = no
; read only = yes
create mask = 0700
 
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
; browseable = yes
; read only = yes
; guest ok = no
;   write list = root, @lpadmin
 
[share]
public = yes
comment = Samba on Ubuntu
writeable = yes
valid users = samba1
path = /srv/samba/share
browsable = yes
 
[sambashare]
path = /home/giun/sambashare
writeable = yes
browseable = yes
users = giun, samba1
guest ok = yes
```

---

### Post by TheFu on 2018-09-06
I can't help with Samba, but you should be preparing to move off 14.04.  Support for it ends next April.  I'm doing the same with my remaining 14.04 servers here.

---

### Post by Morbius1 on 2018-09-06
This is like an archaeological dig.

In random order:
> I tried to remove all lines starting with a # to make it more readable.
That's why the samba gods created the "testparm" command:
```
testparm -s
```
BTW, when you run that I suspect you will notice you have a booboo in your [sambashare] definition: There is no parameter called "users" - I think you meant "valid users". But that's OK samba will just ignore it and turn it into a guest share.
> I tried the following:


[LIST]
[*]Add samba permissions to ufw firewall. 
[/LIST]

It's best to disable ufw until you fix this thing.
> Sharing a folder from Nautilus
Then you need to look at output of this command to find out how the shares created from Nautilus were defined and if they conflict with the share definitions you have in smb.conf:
```
net usershare info --long
```
> I cannot do the following:


[LIST=1]
[*]Detect the server in the windows network sharing center 
[/LIST]

Remember that Win10 - on the client side - will disable smb1 ( they will also do that on the server side ). You can re-enable it but netbios discovery and smb1 are linked. Cannot have one without the other. You can still access the server but must do so explicitly by netbios name or with a hostname.local.

General observation 1 : Linux permissions and samba permissions are two different things. You can set a share to allow write access to a folder by an anonymous user but unless the Linux permissions allow "others" to do the same access will be denied. So check Linux permissions on the folder being shared.

General observation 2: Remember to add the samba users to the samba password database:
```
sudo smbpasswd -a samba1
```

Anyhoo, I don't have any 12.04's here so I can't test things out and since I have no idea what " ... with csf and lfd v12.06" means I doubt I can be of much help/

---

