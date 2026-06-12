---
title: "VMware Player, SAMBA and Shared Files"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Steve H on 2007-05-14
I have installed an XP VMware virtual machine, which works great. I have installed SAMBA set up a share given permissions. I can navigate to \\SERVERNAME in which i can see the folder inside problem when i try and open the folder or Map the Network Drive in XP I get the following message:

> 
\\Servername\MyFiles is not accessible. You might not have permission to use the network resource. Contact the administrator of this server to find out if you have access permissions.

The specified group does not exist.

Here is a copy of my smb.conf:

> [global]
;General server settings
netbios name = SERVERNAME
workgroup = Mshome
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
 ;directory mode = 0755
;browseable = no
 ;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
 ;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
 ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
 ;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for Windows 
;[print$]
;path = /var/lib/samba/printers
;browseable = yes
;guest ok = yes
;read only = yes
;write list = root
;create mask = 0664
;directory mask = 0775

;[printers]
;path = /tmp
;printable = yes
;guest ok = yes
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[MyFiles]
path = /home/steve/SAMBA
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = Steve
force group = Steve
available = yes
public = yes
writable = no
browsable = yes
inherit permissions = yes

Any one got any ideas what is going on here? Why can I connect to the folder??

:)

---

### Post by hoggbottom59 on 2007-05-14
Hello, 
I assume it's on your own network.

If so make it as basic as possible to start off with. Turn off all your firewalls as they always cause probs and keep all the authentication as simple as possible. (you can set these up later).

Make sure you can ping between the machines otherwise nothing will work.
Make sure they are in the same workgroup.

Try setting the Guest Ok to Yes in the conf. Then work on the user problem at a later stage when it's working.

Try finding the Share through Network Places and looking into the Workgroup. I know this isn't as direct but it will give you an idea of what Windows can currently see.

For a VMware machine you have to set up the Shared Folders when you set up the Vm machine. I don't think this counts when you're using it as a client.

Oh if it's XP Home I've never got it working from XP to Linux. I think it's to do with the Simple File Sharing settings in XP Home that you can't change.

Good luck, don't change it once it's working! :) 

Leon.

---

### Post by hoggbottom59 on 2007-05-14
Hello, 
I assume it's on your own network.

If so make it as basic as possible to start off with. Turn off all your firewalls as they always cause probs and keep all the authentication as simple as possible. (you can set these up later).

Make sure you can ping between the machines otherwise nothing will work.
Make sure they are in the same workgroup.

Try setting the Guest Ok to Yes in the conf. Then work on the user problem at a later stage when it's working.

Try finding the Share through Network Places and looking into the Workgroup. I know this isn't as direct but it will give you an idea of what Windows can currently see.

For a VMware machine you have to set up the Shared Folders when you set up the Vm machine. I don't think this counts when you're using it as a client.

Oh if it's XP Home I've never got it working from XP to Linux. I think it's to do with the Simple File Sharing settings in XP Home that you can't change.

Good luck, don't change it once it's working! :) 

Leon.

---

### Post by Steve H on 2007-05-14
Cheers for the advice, but I have already tried most of that. What concerns me is the
> 
The specified group does not exist.

What ¨group¨ is it talking about??

I can navigate through Network places and see the workgroup, and the samba share, I just can´t map it or open it !!

:)

---

### Post by Steve H on 2007-05-15
**bump**

---

### Post by Steve H on 2007-05-15
I´ve sorted it, I just removed the following entry from the smb.conf file

```
force group = Steve
```

And it works like a charm now

:)

---

