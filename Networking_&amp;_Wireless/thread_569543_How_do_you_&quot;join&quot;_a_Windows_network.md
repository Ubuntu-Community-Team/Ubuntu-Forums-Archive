---
title: "How do you &quot;join&quot; a Windows network?"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by peterv6 on 2007-10-07
I run a Windows home network.  I want to add my new Ubuntu server to that network, but I can't find where you would enter the workgroup name.  Does anyone know how I can "join" this network?

---

### Post by bubbalouie on 2007-10-07
It depends on what you are trying to achieve:

To access files using your ubuntu box:

[http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares+for+read+write+access](http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba+shares+for+read+write+access)

To share files from your ubuntu box:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=mount+samba+shares+for+read+write+access](http://ubuntuforums.org/showthread.php?t=202605&highlight=mount+samba+shares+for+read+write+access)

A final note, I use kubuntu, and I can browse files and add windows printers with less hassle than a windows machine (for one it never crashes when doing this). There is no pre-configuration involved for this, it just works, right after an install.

Enabling a Samba share for the rest of the network is not as easy as it is in Windows.... however, once the system is set up it works better, and adding new shares there after is a breeze, to be honest I recommend linux & samba over windows for a file server any day for someone who is willing to do a little work to get a good foundation (for anyone else, I recommend an external hard drive, with viruses etc windows has very high maintenance needs, familiarity is the only 'good' reason to use windows on a dedicated file server).

Goodluck :)

Ryan

*EDIT: a simple **smb.conf** seems to work best for me, mine is below for you reference (with a few minor omissions), I only share this with a VM, and it is only turned on as needed, generally sharing a whole home directory is bad news, though this version hides all configuration files (that is what the **veto files** line is for).

[global]
; General server settings
netbios name = MY_LAPTOP_NETWORK_NAME
workgroup = WORKGROUP_NAME
announce version = 5.0
SO_SNDBUF=8192
interfaces = lo, eth0, eth1
bind interfaces only = true

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
wins support = yes

syslog = 1
syslog only = yes

[home]
path = /home/ryan/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = ryan
veto files = /*.{*}/.*/mail/bin/

---

