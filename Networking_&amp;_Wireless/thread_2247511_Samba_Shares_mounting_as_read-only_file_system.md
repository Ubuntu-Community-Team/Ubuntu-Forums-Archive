---
title: "Samba: Shares mounting as read-only file system"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by max61662 on 2014-10-08
I re-installed Ubuntu and now all my Samba shares are mounting as read-only file systems when accessed from my Macbook. The shares were working fine previously and my smb.conf hasn't changed. 

I have been working on this for a few days now and am completely stuck as to what to try next.

All my partitions are ext4. Both the mount directories and the contents of the mounted partitions are owned by me and have permissions of 775. 

After reinstalling Ubuntu, I recreated my user account and did chown on everything again. I also recreated my Samba account.

Below is an example of how the partitions are mounted in fstab:

```
UUID=d1511c74-8bfd-4a1e-9ab8-8f323b0efb63 /media/Storage\04004 ext4    defaults        0       2
```

Here is an example entry from my log.smbd:

```
[2014/10/08 11:54:13,  0] ../source3/smbd/server.c:1209(main)
  smbd version 4.1.11-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/10/08 11:54:13.984378,  0] ../source3/smbd/server.c:1289(main)
  standard input is not a socket, assuming -D option
[2014/10/08 11:54:14.131527,  0] ../lib/util/become_daemon.c:136(daemon_ready)
```

And here is my smb.conf:

```

[global]
   workgroup = myworkgroupname 
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
    usershare max shares = 100
   usershare allow guests = yes
   allow insecure wide links = yes
   unix extensions = yes

[homes]
    comment = Home Directories
    browseable = yes
   read only = no
   create mask = 0775
    directory mask = 0775

[sysvol]
  path = /var/lib/samba/sysvol
  read only = no

[netlogon]
  path = /var/lib/samba/sysvol/localdomain/scripts
  read only = no


[Storage 04]
path = /media/Storage 04
available = yes
valid users = mkerr
read only = no
browseable = yes
public = yes
writable = yes
follow symlinks = yes
wide links = yes

```

---

### Post by weatherman2 on 2014-10-08
I'd re-check the permissions.  Try making another test share where you set the permissions to 777 in the entire folder.  If you can write to that via Samba, then it is probably a permissions issue - wrong user mapped or something.  If you still can't write to a share with the permissions all set to 777, then it's something else.

---

### Post by max61662 on 2014-10-08
> **weatherman2 said:**
> I'd re-check the permissions.  Try making another test share where you set the permissions to 777 in the entire folder.  If you can write to that via Samba, then it is probably a permissions issue - wrong user mapped or something.  If you still can't write to a share with the permissions all set to 777, then it's something else.

Thanks weatherman2. Doing that test did provide some useful info:

1. Creating a new Samba share with permissions set to 777 does work. Actually, the share works with 755 as well.
2. Recursively applying 777 permissions to one of the pre-existing problematic "read only" shares does not work. Nor does 755.

Both the working and non-working shares have the exact same settings in smb.conf. I just copied and pasted an old entry and modified the name and path.

---

### Post by max61662 on 2014-10-08
According to the logs, Samba is logging me in as a guest instead of as my username. 

I double-checked and I do have a Samba account set up with my username, and I entered my credentials when mounting the share from my Macbook.

I noticed the following strange log entry which I think shows the case of the problem:

```
check_ntlm_password:  Checking password for unmapped user []\[]@[] with the new password interface
```

---

### Post by weatherman2 on 2014-10-08
So you ran smbpasswd -a to add a Samba user?

---

### Post by max61662 on 2014-10-08
> **weatherman2 said:**
> So you ran smbpasswd -a to add a Samba user?

I had already added the user with smbpasswd -a. I also verified the user existed with sudo pdbedit -L -v.

I deleted and re-added the user just now but it made no difference.

---

### Post by max61662 on 2014-10-10
Found the problem. It was due to the spaces in the paths in my smb.conf

---

