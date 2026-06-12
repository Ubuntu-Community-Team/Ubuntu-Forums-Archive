---
title: "Where is the best place to make a folder to share with SAMBA"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by .Nate22 on 2008-06-11
I have had problems with sharing my home directory in SAMBA, in fact, I think it crashed my system.  So, I re-installed Ubuntu, got my desktop the way I wanted, and now I am going to give SAMBA another try.  

Here is what I want to do:

I would like to share 1 or 2 folders to both PCs and Macs on my network.  Security is NOT a problem for our network, so I do not want to have any passwords.

I would like to share Printers over the network. 

I would like to have a file that is NOT in ANY user's profile. Rather, I would like my Ubuntu computer (name = uShotgun) to share the folder "Ubuntu Machine Share" to everyone, I will create various sub-folders as necessary.

Can I create a setup such that \\uShotgun\Ubuntu Machine Share will be the way my network works.  I have tried to create a folder in the "Filesystem" folder, but that is not allowed...only user root can do that. (I am the only user other than root, this is my computer, I just have heard that logging in as root is a bad idea)

Attached is my SAMBA config file. What changes should I make? 

Cheers, 

Nate


SMB CONFIG FILE:


#======================= Global Settings =======================

[global]
   workgroup = FREYHOME
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
;   security = user
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
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups

############ Misc ############g
;   include = /home/samba/etc/smb.conf.%m
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
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

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

---

### Post by dmizer on 2008-06-12
i've never been able to get a functioning printer share via samba.  just use the cups interface.  with that in mind, i would suggest a smb.conf like so:

```
[global]
    ; General server settings
    netbios name = uShotgun
    server string = %h server (Samba, Ubuntu)
    workgroup = FREYHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[[COLOR="Red"]Ubuntu_Machine_Share[/COLOR]]
    path = [COLOR="Red"]/local/path/to/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```
be sure to edit the red variables in the above smb.conf so it fits your specific environment.

then add your ubuntu user to the samba group with teh following commands:
```
sudo smbpasswd -L -a UBUNTU_USERNAME
sudo smbpasswd -L -e UBUNTU_USERNAME
```

restart samba:
```
sudo /etc/init.d/samba restart
```
and you should be ready to go.

if you want to share more than one directory, simply include a second entry like so:
```
[[COLOR="Red"]Share_1[/COLOR]]
    path = [COLOR="Red"]/local/path/to/first/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]

[[COLOR="Red"]Share_2[/COLOR]]
    path = [COLOR="Red"]/local/path/to/second/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```

to share your printer via cups,
go to: system > config > printer > Server Settings, and put a checkmark next to "Share published printers on the network".

---

### Post by .Nate22 on 2008-06-15
Thanks for such a great post, but I have been able to get my samba to share printers across all platforms (Windows and Mac) and then even share some files.  However, the file sharing sorta just stopped working somehow. It was really random, and then soon after, my ubuntu system crashed.  I have had to re-install everything.  However, my question is:

What does/do the lines force user =
                       force group =
do to my sharing.  Keep in mind, I would like to have my security set to 

security = share

(I do not have to worry about security on my "network" of 5 computers, and furthermore, no one can see our network or connect to it without me entering in their computers MAC address first) 

So, in short, force user? force group?  why do I need that? And what does it do?

Thanks, 
Nate

---

### Post by dmizer on 2008-06-15
> **.Nate22 said:**
> However, my question is:

What does/do the lines force user =
                       force group =
do to my sharing.  Keep in mind, I would like to have my security set to 

security = share

(I do not have to worry about security on my "network" of 5 computers, and furthermore, no one can see our network or connect to it without me entering in their computers MAC address first) 

So, in short, force user? force group?  why do I need that? And what does it do?

Thanks, 
Nate

windows, mac, and linux all handle file permissions differently.  when a computer saves or manipulates a file on your server, these two lines override your windows and mac local permissions to insure that server permissions belong to your ubuntu server user.

since you have 5 computers (likely with differing usernames, passwords, and permissions), it's important that your server has an override for these so that all computers can access the files equally.

---

### Post by Hackit on 2008-06-17
> **dmizer said:**
> i've never been able to get a functioning printer share via samba.  just use the cups interface.  with that in mind, i would suggest a smb.conf like so:

```
[global]
    ; General server settings
    netbios name = uShotgun
    server string = %h server (Samba, Ubuntu)
    workgroup = FREYHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[[COLOR="Red"]Ubuntu_Machine_Share[/COLOR]]
    path = [COLOR="Red"]/local/path/to/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```
be sure to edit the red variables in the above smb.conf so it fits your specific environment.

then add your ubuntu user to the samba group with teh following commands:
```
sudo smbpasswd -L -a UBUNTU_USERNAME
sudo smbpasswd -L -e UBUNTU_USERNAME
```

restart samba:
```
sudo /etc/init.d/samba restart
```
and you should be ready to go.

if you want to share more than one directory, simply include a second entry like so:
```
[[COLOR="Red"]Share_1[/COLOR]]
    path = [COLOR="Red"]/local/path/to/first/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]

[[COLOR="Red"]Share_2[/COLOR]]
    path = [COLOR="Red"]/local/path/to/second/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```

to share your printer via cups,
go to: system > config > printer > Server Settings, and put a checkmark next to "Share published printers on the network".

Hi Dmizer,

I followed your smb.conf file and the only thing i wanted to change was the guest access (i want to be the only one who can see it)

So i can mount and write to the folder with ubuntu, but on my vista 64 machine i'm unable to write it say you do not have permission.

I can see everything on the drive but i need to be able to have write capability on vista.

Here's my smb.conf file.

[global]
	workgroup = HACKIT
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	null passwords = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS

[Kevs Folder]
	path = /media/disk/Kevs Folder
	force user = hackitz
	force group = hackitz
	read only = No
	create mask = 0755
hackitz@Ubuntu-Server:~$ 


thanks for any help.

just so you know media/kevs folder. has read write if i run fstab

---

### Post by dmizer on 2008-06-18
> **Hackit said:**
> Hi Dmizer,
[snip]
thanks for any help.

just so you know media/kevs folder. has read write if i run fstab

posted in your other thread.

---

### Post by plewisfdx on 2008-06-24
> **.Nate22 said:**
> (I do not have to worry about security on my "network" of 5 computers, and furthermore, no one can see our network or connect to it without me entering in their computers MAC address first) 


I probably wouldn't worry about your network either, but if someone sniffs your packets they can see the mac address one of your wireless computers is sending to access your network, then just has to spoof that mac address.

Its not likely, but information is power if you ever **need** security!

---

### Post by .Nate22 on 2008-09-01
> **plewisfdx said:**
> I probably wouldn't worry about your network either, but if someone sniffs your packets they can see the mac address one of your wireless computers is sending to access your network, then just has to spoof that mac address.

Its not likely, but information is power if you ever **need** security!

It seems that after I upgraded all of my systems, and I actually did a fresh re-install of MAC OS X Leopard on my laptop, that the printers attached to the uShotgun (u=Ubuntu, Shotgun = awesome computer name) are now shared via Samba from the Ubuntu machine, and recognized as Bonjour! shared printers in MAC OS X Leopard.  It's actually not that hard to share a printer or file system between platforms now!  It's great to be able to take an old computer, put Ubuntu on it, and now have it be the central information and printer support base for my newer machines.  (Wirelessly too!) Security is taken care of for us because I do not broadcast the SSID, and use MAC filtering to determine which clients are able to access the network or not by using DD-WRT on my Linksys router.

---

