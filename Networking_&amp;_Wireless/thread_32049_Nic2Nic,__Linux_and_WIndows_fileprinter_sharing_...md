---
title: "Nic2Nic,  Linux and WIndows file/printer sharing ...complicated"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by registerera on 2005-05-05
Hello I just started learning to use ubuntu and so far it's awesome...not the unix type of linux I thought. I'm relying on mainly the unofficial guide but I found that this is not working for me:  

I have a nic2nic setup between a ubuntu and windows xp for file/printer sharing only, and each computer has another nic that connects to a router for broadband. Is it possible to set up this network. I have tried modifying the fstab and smb.conf by following the Unofficial guide but no go.

I'm trying to share drives on my side and also on the networked computer,
so far gedit is like so:

....
/dev/sdb2       /home/share/KEPLER_J   ntfs  umask=0222     0       0

/dev/hde5       /home/share/TEN_G       ntfs  umask=0222     0       0
/dev/hde1       /home/share/DUECE_C   ntfs  umask=0222     0       0
...

here the last two drives are on another physical drive that is connected to a promise ata controller card. if i do a remount everything here works. During boot i see a message of something as: special drive can not be mounted. I checked the locations in GPart and through fdisk -l and they are correct. 


//192.168.0.2/DIRAC (H)  /home/share/DIRAC_H  smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

//192.168.0.2/DIRAC (H)  /home/share/DIRAC_H  smbfs credentials=/root/.smbcredentials       0       0

//192.168.0.2/DIRAC (H)   /home/share/DIRAC_H   cifsexev, credentials=/etc/cifspw

but none of these has worked i can acess the drive fine through run application: smb://192.168.0.2/DIRAC (H)

---

### Post by registerera on 2005-05-05
this is what my smb.conf looks like, ubuntu is installed on *.0.1:

[global]
interfaces = 127.0.0.1, 192.168.0.1/24
bind interfaces only = yes

hosts allow = 127.0.0.1, 192.168.0.1, 192.168.0.2
hosts deny = 0.0.0.0/0
....

[LinuxDesktop]
path = /home/kh/Desktop
comment = /home/kh
available = yes
browseable = yes
public = yes
writable = yes

[TEN(G)]
path = /home/share/TEN_G
comment = BOHR
available = yes
browseable = yes
public = yes
writable = yes

[KEPLER(J)]
path = /home/share/KEPLER_J
comment = KEPLER
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by registerera on 2005-05-09
Can someone help me with this set up? Is there a another site out there??

---

