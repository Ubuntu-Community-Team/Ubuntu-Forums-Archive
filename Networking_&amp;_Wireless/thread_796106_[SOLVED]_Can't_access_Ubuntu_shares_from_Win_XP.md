---
title: "[SOLVED] Can't access Ubuntu shares from Win XP"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by TVC15 on 2008-05-16
Hello, really hope someone can help me out here.
Most people seem to have problems seeing the shares on their Windows machines, with me it's the other way around.
In XP, I go to "My network locations", my Ubuntu server shows up nicely.  When I click on the share created in Ubuntu, I am prompted for a logon and a passwd.  I'm always refused, as if the passwd wasn't correct.
Ubuntu is 8.04.  It all worked flawlessly in 7.10; apparently new isn't always better...:(

This is my smb.conf (I removed most comments)

Many thanks in advance for any help!


[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = KL44

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast






####### Authentication #######

   security = user
   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

;   logon drive = H:
;   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================
;[homes]
;   comment = Home Directories
;   browseable = no

;   read only = yes

;   create mask = 0700

;   directory mask = 0700

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

---

### Post by closeyourwindows on 2008-05-16
I have similar problem, I upgraded from 7.10 and I was able to create shares that any one in my network could access from XP.  I upgraded!!!  Now I can still access all of my shares but I cannot create new shares.  the smb.conf shows all of the shared directories but GUI does not.  If I manually create a share in the smb.conf or by using nautilus, it prompts for guest password.  I've restarted init.d samba and still not working.

---

### Post by Iowan on 2008-05-16
I'd mention Places>Connect to Server works better for me... but I'm still on 7.10 (still unsure if 8.04 will work on my machine).  I read something about tighter Samba authentication under Hardy, but I haven't seen specifics.

---

### Post by TVC15 on 2008-05-18
Hello, I was able to solve my problem!!  What a relief!
Here's what needs to be done (at least in my case):

On the computer that has the folders/file you want to share:
   1. Make sure you have the necessary packages installed for SAMBA (check in Synaptic).
In my case I installed the following: libsmbclient, nautilus-share, samba, samba-common, smb-client, smbfs, system-config-samba.
Especially this last one is very handy, most of the others are installed by default.
   
   2. Go to System -> Administration -> Samba
Here you can add shares, choose your workgroup and users.
Here's where things went wrong.
Samba creates a default password that differs from you user password.

   3. Change the default password into your user password on that machine.  DONE!

Hope this helps a few people out.


Greetings!

---

### Post by tomski on 2008-05-26
i seem to be getting this error when i try to add a new share:


'net usershare' returned error 255: [2008/05/26 15:11:30, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
net usershare add: cannot convert name "Everyone" to a SID. NT_STATUS_IO_TIMEOUT.

---

### Post by TVC15 on 2008-05-28
Hello, 
I've never seen this kind of errors.
Did you go ahead as I describrd earlier or by command line?
I suggest to reinstall the necessary packages and try again.

Regards,

Johan

---

### Post by Iowan on 2008-05-28
There's a **sambashare** (or something similar) group in Hardy's version of Samba.  In the **man** for either **smbclient,** or **smb.conf** - or in the **smb.conf** itself - is information about adding users to this group. Not quite sure where the "Everyone" came from...


Dunno if it's related to [this]("https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810") bug report. Solution basically involves logging out and back it to get user in **sambashare** group.

---

