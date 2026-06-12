---
title: "[SOLVED] samba password protect shares"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by xIke on 2007-08-16
I have a samba share that I can't figure out how to require a password to view it.  Right now anyone who tries to access it can get it in.  Here's the code from my /etc/samba/smb.conf:

```

[sharename]
    path = /var/www
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = worf
    force group = worf
    available = yes
    browsable = yes
    public = no
    writable = no
```

I'm sorry if this is an obvious question...I've searched and can't find a good page explaining this.

---

### Post by ihristov on 2007-08-17
I am not sure, but below is my full smb.conf and I get prompted for a password.
I actually have not touched this file by hand. I added the 2 shares at the bottom with the UI from "System -> Administration -> Share Folders"

```
$ grep -v ^$ /etc/samba/smb.conf | grep -v ^# | grep -v ^\;
[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[tmp]
path = /home/user/tmp
comment = Temporary files
available = yes
browsable = yes
public = yes
writable = yes
[dl]
path = /home/user/dl
comment = Download folder
available = yes
browsable = yes
public = yes
writable = no
```

Maybe you are missing the "obey pam restrictions = yes" in the global section

---

### Post by xIke on 2007-08-17
Hm.  I tried adding that line, but still no password is required.  This is really weird.

---

### Post by ihristov on 2007-08-19
If I were you, I would save all my configuration files for reference, then remove completely Samba (including configuration files) and would then install it again and try to only modify using the UI, not manually.

I think something like
```
sudo apt-get remove --purge samba smbfs
sudo apt-get install samba smbfs
```
should do the trick.

---

### Post by xIke on 2007-08-19
> **ihristov said:**
> If I were you, I would save all my configuration files for reference, then remove completely Samba (including configuration files) and would then install it again and try to only modify using the UI, not manually.

I think something like
```
sudo apt-get remove --purge samba smbfs
sudo apt-get install samba smbfs
```
should do the trick.

Okay...what's the UI way to modify things?  Shared Folders has practically no options, definitely none concerning passwords...

---

### Post by ihristov on 2007-08-19
This is because by default it does require passwords.

To change the Samba password for a user you need to use the Samba utility.

```
sudo smbpasswd -a USERNAME
```

should do the trick

---

### Post by modster78 on 2007-08-19
hi

im no pro but im sure there should be  ```
 security = user 
```  under [global] header.

i use gsambad easy got through  add/remove to easy manage samba with a GUI.

---

### Post by jjf on 2007-08-21
I'm having the same problem.  I need to set up samba shares that prompt for a password.  The behavior right now is that it either lets anyone in or shows a "contents cannot be displayed" error.

I've found that if the folder is set to full read/write privileges for all users (chmod 777), then I can access it remotely.

But if the folder has anything less than full privileges, I get a "contents cannot be displayed" error.

I stepped through the instructions at ubuntuguide.org under the heading "How to share public folders with read/write permissions (Authentication=Yes)."  That section has you run **smbpasswd -a USERNAME** and create a username map, but none of that seems to matter a bit.  As "jjf" on my laptop I'm able to access a samba share (without authenticating) on a computer where there is no jjf account.

I did, like ihristov's suggested, remove, reinstall, and only use the UI.  It made no difference in behavior.

---

### Post by dmizer on 2007-08-21
follow the first link in my sig.

---

