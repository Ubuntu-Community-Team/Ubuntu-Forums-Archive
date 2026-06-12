---
title: "smb mount from mac"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Hunz on 2008-08-24
hi,

i am trying to mount an xsan (apple storage), i used this command:

**mount -t smbfs -o username=user,password=password,rw,uid=0,gid=0,fmask=777,dmask=777 //ip/folder/ /mnt/san/**

and i always get this error message
[B]
5203: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed[/B]

i can ping from both machines, and the wierd thing is i can access the san using the GUI and i got read write permissions and i also accessed these files from a windows machine but with only read permissions, amd when i try to mount the san on /mnt/san it always gives the same error.
anybody has any ideas how to solve this problem???

thanks in advance[LEFT][/LEFT]

---

### Post by coffeecat on 2008-08-24
Have I got you right here? You are trying to mount a smb share on another machine using an Apple Mac? And you were able to mount the smb share using Finder in MacOS in the GUI? And you are typing that 'mount... command' in a Mac terminal? Am I correct?

Try prefacing the 'mount...' command with sudo. You are trying to mount with uid=0 (root) and gid=0 (root), and I guess you need root privileges to mount.

---

### Post by Hunz on 2008-08-24
no, im not trying this command on the mac at all, i have a san (storage area network) which i would like to mount on a linux system, and i tried another gid and uid and no difference, same results.

i can access the apple san shared files using smb://IP from the browser, and i got read and write permissions but when i try mounting the shared files i get the same error message

got it???

---

### Post by Hunz on 2008-08-24
This is exactly the worflow

on the linux machine i type this command:
[B]
mount -t smbfs -o username=admin,password=password,rw //IP/folder/ /mnt/mac/[/B]

and on the mac, this is the /var/log/samba/log.smbd :

[B][2008/08/24 08:43:05, 1] auth_ods.c:opendirectory_auth_user(204)
  User "admin" authenticated successfully with "dsAuthMethodStandard:dsAuthSMBNTKey" :)
[2008/08/24 08:43:05, 1] auth_ods.c:opendirectory_smb_pwd_check_ntlmv1(377)
  opendirectory_smb_pwd_check_ntlmv1: [0]opendirectory_auth_user
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [20]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [501]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [500]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [81]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [502]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [79]
[2008/08/24 08:43:05, 1] pdb_ods.c:odssam_getgrgid(2870)
  odssam_getgrgid: gid [80]
[2008/08/24 08:43:06, 1] /SourceCache/samba/samba-100.7/samba/source/auth/auth.c:check_ntlm_password(349)
  check_ntlm_password: check_sacl(admin, smb) failed[/B]




anybody has any ideas on how to solve this, i think its sumthing to do with the mac smb settings and the user access

---

### Post by Iowan on 2008-08-24
Forgive (and ignore) me if I'm off base (not a MAC user).  Have you tried the mount as [CIFS]("http://ubuntuforums.org/showthread.php?t=288534")?

---

