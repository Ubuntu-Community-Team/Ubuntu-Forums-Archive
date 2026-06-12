---
title: "smb.conf"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by poordamnedfool on 2007-12-12
could you take a look at my smb.conf i am having problems with windows users accessing the network folders.  Windows machines can see the server but cannot access folders or files.  Linux users are using the server fine.

Thanks

[global]
        passwd chat debug = yes
        name resolve order = wins bcast hosts
        idmap gid = 15000-20000
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spas
sword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        netbios name = GoatServer
        writeable = yes
        printing = CUPS
        idmap uid = 15000-20000
        logon script = scripts/logon.bat
        workgroup = MSHOME
        printcap name = CUPS
        security = user
        add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody
 %u
        delete user script = /usr/sbin/userdel -r %u
        log level = 3
        load printers = yes
        add group script = /usr/sbin/groupadd %g
        delete group script = /usr/sbin/groupdel %g
        add user to group script = /usr/sbin/usernod -G %g %u
        logon drive = H:
        username map = /etc/samba/smbusers
        winbind trusted domains only = yes
        passdb backend = tdbsam
        printer admin = @lpadmin
        template shell = /bin/bash
        wins support = yes
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        logon path = \\GoatServer\profile\%U
        add user script = /usr/sbin/adduser --quiet --disabled-password --gecos 
"" %u
        preferred master = yes
        domain logons = yes

   
   
   # Set CUPS for printing
   
   # Default logon


   # Useradd scripts


   # sync smb passwords woth linux passwords
   
   # set the loglevel

[public]
   browseable = yes
   public = yes



[printers]
   comment = All Printers
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
   write list = root, @smbadmin


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no
   guest ok = yes
   writable = no
   share modes = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
   guest ok = no

[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

[Media]
        write list = 1477,@1477
        path = /media/hdd1
        comment = All House Media
        create mode = 777
        user = @users
        directory mode = 777

[Home]
        comment = Home Directories
        user = @users
        path = /home
%u

---

### Post by cptdrew on 2007-12-13
You don't seem to be shareing anything. You should have a section called [Share]...
[Shared]
path = /home/user/sharedfolder
guest ok = yes
available = yes
browsable = yes
public = yes
writable = yes

you can easily add this by gong to >SYSTEM >ADMINISTRATION >SHARED FOLDERS click on + ADD and browse to the folder you want to add.

be sured to checkout "The Official Samba 3.2.x HOWTO and Reference Guide" at [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html)

I hope this helps

---

### Post by movrshakr on 2007-12-18
Solution is in this thread

[http://ubuntuforums.org/showthread.php?t=504033&highlight=movrshakr&page=2](http://ubuntuforums.org/showthread.php?t=504033&highlight=movrshakr&page=2)

Particularly read message #13 to show a share section for smb.conf.

set security = share (insecure!!)

and do the "sudo smbpasswd -a username" thing.

That last item was the key for me.

How I was supposed to have known to do that is beyond me.

---

