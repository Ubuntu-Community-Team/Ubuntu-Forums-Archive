---
title: "Samba write issues"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by klaasth on 2008-05-22
I have a problem with running my samba server. I want to share my /home/klaasth, I already added this directory in windows via SAMBA, but I can't write anything to it or I can't delete anything, I just can read files from this folder. What can be the problem:
My smb.conf:
[global]
workgroup=Thys
netbios name=Documenten
encrypt passwords=yes
socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY
wins support=no
security=user

[homes]
comment=home directories
valid users=klaasth
browseable=no
readonly=no

Output from testparm /etc/samba/smb.conf:
klaas@klaas-server:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = THYS
	netbios name = DOCUMENTEN
	socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY

[homes]
	comment = home directories
	valid users = klaasth
	read only = No
	browseable = No

What can be the problem I also executed, sudo chown klaasth.root /home/klaasth and klaasth has write rights on his /home/klaasth
Can sombody help me?

---

### Post by Iowan on 2008-05-22
Be aware of [this]("http://ubuntuforums.org/showthread.php?t=772706") caution. There's a post around here somewhere recommending adding yourself to the usershare group.

---

### Post by dmizer on 2008-05-22
change your homes section to the following:
```
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/
```

then add your ubuntu username to the samba group with the following command:
```
sudo smbpasswd -L -a klaas
sudo smbpasswd -L -e klaas
```

restart your samba server by rebooting or by entering this command:
```
sudo /etc/init.d/samba restart
```

this may or may not work because you said you did a chown (bad idea) on your home directory.

---

### Post by Iowan on 2008-05-22
> **dmizer said:**
> ...then add your ubuntu username to the samba group...Maybe THAT'S what it was, and I misunderstood the Samba group!!!

---

### Post by klaasth on 2008-05-23
**Solved:** I was trying to delete files in /home/klaasth/Examples and klaasth didn't have rights to write here default. I deleted this folder as root, now in /home/klaasth, I can do what I want
Thank you for helping!!!!

---

