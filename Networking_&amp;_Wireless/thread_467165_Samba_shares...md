---
title: "Samba shares.."
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by johng4 on 2007-06-07
I have a home network made up of several computer which I want to have share 1 file server.

My file server has a static IP (192.168.62.51), and has samba installed.

My workgroup is SNOHOMANET, and the server name is Mercedes (mercedes.snohomanet).

What I want...

I have a 2nd hard drive mounted as /storage (200GB), with the following directory structure...

/storage/public/  --> Public File share, with an Apache alias to allow users to access files in the directory outside the network 

/storage/private/ --> Private File share, only accessible through the network.

Then, I want each user to have their own private folder for their own files, independant of which computer they are currently using...

/home/user/share/ --> Private user folder.

There's a few other configurations that I'm fairly capable of doing, however, I'm not sure how to do this.. every time I think I have samba figured out, I prove to myself that I'm not quite there yet...


Here's the sample samba.conf that I'm following so far.. but it doesn't seem to point things where I want them....

```

[global]
   workgroup = SNOHOMANET
   netbios name = MERCEDES
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   load printers = yes
   printcap name = CUPS
   printing = CUPS
   printer admin = @lpadmin
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\mercedes\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3

[public]
   browseable = yes
   public = yes


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


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

```

---

### Post by stchman on 2007-06-07
> **johng4 said:**
> I have a home network made up of several computer which I want to have share 1 file server.

My file server has a static IP (192.168.62.51), and has samba installed.

My workgroup is SNOHOMANET, and the server name is Mercedes (mercedes.snohomanet).

What I want...

I have a 2nd hard drive mounted as /storage (200GB), with the following directory structure...

/storage/public/  --> Public File share, with an Apache alias to allow users to access files in the directory outside the network 

/storage/private/ --> Private File share, only accessible through the network.

Then, I want each user to have their own private folder for their own files, independant of which computer they are currently using...

/home/user/share/ --> Private user folder.

There's a few other configurations that I'm fairly capable of doing, however, I'm not sure how to do this.. every time I think I have samba figured out, I prove to myself that I'm not quite there yet...


Here's the sample samba.conf that I'm following so far.. but it doesn't seem to point things where I want them....

```

[global]
   workgroup = SNOHOMANET
   netbios name = MERCEDES
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   load printers = yes
   printcap name = CUPS
   printing = CUPS
   printer admin = @lpadmin
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\mercedes\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3

[public]
   browseable = yes
   public = yes


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


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

```

I struggled with this one for a while.  I finally got samba working by using this prodecure:

[http://www.stchman.com/share.html](http://www.stchman.com/share.html)

The pyNeighborhood worked like a charm.

I can now share files on all my computers.  Very easy.

---

### Post by johng4 on 2007-06-07
Not quite was I was going for.  This is going to serve as more of a centralized file server.  The instructions I've been following have it as a domain controller.. which I'm not sure that I want.

---

### Post by dmizer on 2007-06-07
have a look at the first link in my sig., and read through a good portion of the first pages of the thread.  the answers to your problems are all addressed there.

edit:
almost forgot ... do not, under any circumstances, allow a samba share to be open to the net.  if you want to allow access to your server from the net, use protocols which were designed to be accessed across the open internet, like ftp (or better yet ftps).  samba's purpose and design is targeted at internal networks only.  it is NOT secure enough to open out to the web.

---

