---
title: "Share Drives"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by gliff159 on 2010-10-05
I was wondering if its possible to allow windows to access a secondary drive in linux? I have a computer running ubuntu 64 bit and it can access all my window computes shared drives, it opens up a prompt and all I have to do is type in my windows password. Is there a way to do this so its similar in ubuntu



NOTES
I have tried google a considerable amount and I guess I'm just not hitting the right key words.  
I have almost no linux experience

---

### Post by kkaldroma on 2010-10-05
Yes there is, you are looking for a samba share.
you already have samba if you are able to access a windows share, now all you have to do is set up a share on on ubuntu for windows to see.

Under file properties there should be a share tab. Check the box and give it a name.

---

### Post by pricetech on 2010-10-05
System - Administration - Synaptic Package Manager:

Search for system-config-samba and install it.  You'll get Samba plus a GUI interface for administering it.

---

### Post by gliff159 on 2010-10-05
> **pricetech said:**
> System - Administration - Synaptic Package Manager:

Search for system-config-samba and install it.  You'll get Samba plus a GUI interface for administering it.


thanks, do i have to install samba in windows as well?

---

### Post by Morbius1 on 2010-10-05
No. Windows already has samba installed ( it's called SMB there ). That's how you were able to create a Windows share in the first place.

---

### Post by gliff159 on 2010-10-05
Oh then perhaps im doing it wrong I went into samba added media/old (old is the drive name). Added users root (my windows name) and password x2 and it says not accessible when i try to access it form windows. (the drive is mounted)

---

### Post by Morbius1 on 2010-10-05
Please post the output of the following command:
```
testparm -s
```

---

### Post by gliff159 on 2010-10-05
```
 
gliff@server-box:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[old]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[old]
    path = /media/old
    valid users = root
    read only = No

```

---

### Post by Morbius1 on 2010-10-05
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find the line:
>      encrypt passwords = NoAnd change it to this:
>      encrypt passwords = YesSave smb.conf and restart samba:
```
sudo service smbd restart
```To be honest I don't know what you're going to do with the valid users = root line. You've acutually created a user root in linux and gave it a samba password?

For the time being, just to make sure everything else is ok, go back into Administration > Samba and change the access to "allow access to everyone"

Then see if Windows can access the share.

[COLOR=Blue]EDIT: I forgot one more annoying question:[/COLOR]
Please post the output of the following command:
```
 ls -dl /media/old
```

---

### Post by gliff159 on 2010-10-05
Thanks that solved it :)

---

