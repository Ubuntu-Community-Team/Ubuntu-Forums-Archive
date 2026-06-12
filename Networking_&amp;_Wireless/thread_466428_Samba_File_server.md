---
title: "Samba File server"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by kms254 on 2007-06-06
Ok some background. I have a 300gb drive that i have set up as a fat32. I want it like that so i can take it out of the server when i travel to gf's house or my parents, etc. I have set up a LAMP server to host my site. I have the box at work right now while i am setting it up. I have the 300gb drive set up and mounted in the server. I can read it fine from the box. When i go to access the server i can login under my test user (michelle) and i have gotten it so the all users(Common) and net login are accessible. Their location is on the 300gb fat32 drive. It has movies, music, pictures etc. For some reason and I am sure it is simple I can not access the individual folder for Michelle.
```
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro   0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/Apollo   vfat   umask=000,dmask=0000,uid=500,gid=500,use$


```

hdb1 is the external

```

[global]
   workgroup = DISNEY
   netbios name = JASON
   server string = %h server       


   passdb backend = tdbsam
   security = user   
   username map = /etc/samba/smbusers       
   name resolve order = wins bcast hosts       
   domain logons = yes
   preferred master = yes
   wins support = yes

   # Set CUPS for printing
   printcap name = CUPS   
   printing = CUPS

   # Default logon
   logon drive =K:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spasswor$
   passwd chat debug = yes
   unix password sync = yes

   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba

[netlogon]
   comment = Network Logon Service
   path = /media/Apollo/netlogon
   admin users = Administrator
   valid users = %U
   read only = no

  [profile]
   comment = User profiles
   path = /media/Apoll/profiles       
   valid users = %U       
   create mode = 0600               
   directory mode = 0600   
   writable = yes
   browsable = no

[allusers]
  comment = Common                
  path = /media/Apollo/Common   
  valid users = @users        
  force group = users
  create mask = 0600      
  directory mask = 0600
  writable = yes



```


Any suggestions?

---

### Post by kms254 on 2007-06-08
I got it fixed

---

