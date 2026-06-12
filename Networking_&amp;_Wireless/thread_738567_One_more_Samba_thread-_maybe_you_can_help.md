---
title: "One more Samba thread- maybe you can help?"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by tobydeemer on 2008-03-28
Hi all-

Well, I know it's one more samba thread (hence the title) but I've been working on it for a couple of weeks now with various configurations, and I haven't quite got it down. I've been using this Guide:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) **The smb.conf I am using is from this guide too.**

And also the official online docs, and several other sites with tutorials and sample smb.conf files.

So here's my situation:
I have three computers connected to each other via the DSL router, which then connects to the internet. 

One is an XP workstation, the second is my laptop with Ubuntu 7.10, and the third is a server that I built with Ubuntu Server 7.10 and xubuntu-desktop. The server has two hard drives- a 60GB with the OS and storage, and a second 20GB for just storage. I want to be able to use that second one as general network storage for the other two computers, as well as maintain access to the first one. 

From the XP station I can see both the laptop and the server. I can read files but not write on the laptop. I CANNOT access, even read-only, files on the server from XP. (But I can see the machine and its shares in Network Places). It says access is denied and does not ask for a password. 

I can see the server from the Ubuntu laptop, but I cannot access any of the shares I have set up, even though I've added my user accounts (both from XP and from Ubuntu) to the server accounts and server samba accounts. From the laptop, I can see, read and write to the two shares I have set up on the XP station, but not from the server. 

(Possible another point of interest that may help- if I try to RDP into the server, it refuses the connection. The firewall in the router is set up to allow it though. Does anyone know how to do that through the xubuntu desktop environment?)

I'm uploading a little JPEG of the setup to give a better picture. 

I have Apache, PHP and MySQL on the server as well, because I was planning to learn web design and hosting, and maybe mail as well. (So I also have Postfix and a couple other things.) Could this cause a break in Samba somehow? I figured getting through Samba first would be a good start to those other goals.

If you've read all this, thank you, and thank you more for any help. Ideas would be greatly appreciated. I'm subscribed to like four samba threads here, and like five web sites about it. I'm a little cross-eyed after today...

---

### Post by tobydeemer on 2008-03-28
Oh, I almost forgot-

Just incase anyone was interested, I shamelessly borrowed those icons for the network diagram from the icon set called black-white_2-neon, I from either gnome-look.org or art.gnome.org. I forget which. One of the best sets I've seen though.

---

### Post by Eiríkr on 2008-03-28
Sounds like you've got two Samba servers running on the same subnet / workgroup.  In such cases, you need to make sure that only one is the master browser, and only one has [font=courier]wins support = yes[/font], or you'll get odd conflicts.  

So to dive right in, please post the smb.conf files from your UD and UL machines, and we'll go from there.  

One other thing to check -- can you ping your Ubuntu server from the other two machines?  (Either by hostname or IP, doesn't matter -- just to check that it's accessible.)  

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-03-29
HI-

Thanks for the reply.

Here's my smb.conf, and I'm trying to remove wins support from the laptop, to see if that helps the XP station get to the server shares, and vice versa.

[HTML][global]
    ; General server settings
    netbios name = DeemerUbuntuServer
    server string = deemerubuntuserv
    workgroup = DEEMER
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = false

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = krista tobydeemer administrator
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/administrator/Server_Share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tobydeemer krista administrator
    force group = tobydeemer krista administrator

[StorageDrive]
    path = /dev/sdb1
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tobydeemer krista administrator
    force group = tobydeemer krista administrator[/HTML]


And I almost forgot- I can ping the server from the laptop and the XP station, and from the server, I can ping both of the others as well, so the connections are all good and traffic flows.

---

### Post by tobydeemer on 2008-03-29
Here's an update: from the smb.conf listed above that's on the server, I can now access the [homes] share on the server from XP, but not the Server_Share or the Storage_Drive. It sees them, but won't access them. So is that a file path thing?

---

### Post by HermanAB on 2008-03-29
Here is some Samba debug help: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by Eiríkr on 2008-03-29
No time to go into it in depth, but for starters, your [font=courier][force user]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEUSER")[/font] and [font=courier][force group]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEGROUP")[/font] lines look severely messed up, as each should list *only one* user / group.  Have a look at the man page sections linked to in the option names for details.  

Besides which, you really don't need either of these options if access is properly configured -- i.e., only certain users are allowed access, and those users have the proper filesystem permissions on the shared directory.  Looking at your [font=courier][homes][/font] share, perhaps what you mean to use is the [font=courier]valid users[/font] option instead?

Oh, and the [font=courier]announce version[/font] and [font=courier]null passwords[/font] options in your [font=courier][global][/font] section should probably also be deleted -- the former is almost *never* needed, and the latter is *only* needed if you have Samba usernames explicitly defined with no passwords (using the [font=courier]sudo smbpasswd -a USERNAME[/font] command).  

And if you're not sharing a printer via your Samba server, you're better off deleting all the printing-related options and share definitions.

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-03-29
Ok, another update. 

I did the modifications you suggested, and I used "sudo chown -R 775 /path/to/share" to make them readable (as in the troubleshooting guide suggested by HermanAB above). 

So now, from XP I can see all the shares I have on the network. I was able to write to the 20GB server storage drive from XP.

However, using the same permissions and settings, I cannot write to the laptop share from XP. 

And the laptop still does not recognize the server being on the network. I can read and write to the XP shared folders from the laptop, but I can't get to the linux server. I think this is probably because I'm looking at the Windows network in the network places, but it doesn't show up anywhere else either. Is there somewhere outside Samba that I need to go through to that server? (I know that sounds like an obvious-answer question...)

Thanks again for the help.

---

### Post by Eiríkr on 2008-03-30
So if I understand you correctly, you are also serving shares via Samba from your laptop?  If that's the case, please post *both* the updated smb.conf file from your desktop, and the one from your laptop.  

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-03-30
Ok, here's the one from the laptop:

[HTML][global]
    ; General server settings
    netbios name = toby-laptop
    server string = toby-laptop
    workgroup = DEEMER
#    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
#    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no
    wins server = 192.168.1.67/255.255.255.0

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
#[print$]
#    path = /var/lib/samba/printers
#    browseable = yes
#    guest ok = yes
#    read only = yes
#    write list = root
#    create mask = 0664
#    directory mask = 0775

#[printers]
#    path = /tmp
#    printable = yes
#    guest ok = yes
#    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/tobydeemer/laptop_share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
    valid users = tobydeemer krista administrator
#    valid groups = tobydeemer krista administrator[/HTML]

---

### Post by tobydeemer on 2008-03-30
And here's the one from the server:

[HTML][global]
    ; General server settings
    netbios name = DeemerUbuntuServer
    server string = deemerubuntuserv
    workgroup = DEEMER
#    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = false

    passdb backend = tdbsam
    security = share
#    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = krista tobydeemer administrator
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
#[print$]
#    path = /var/lib/samba/printers
#    browseable = yes
#    guest ok = yes
#    read only = yes
#    write list = root
#    create mask = 0664
#    directory mask = 0775

#[printers]
#    path = /tmp
#    printable = yes
#    guest ok = yes
#    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Server_Share]
    path = /home/administrator/Server_Share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
#    force user = tobydeemer krista administrator
#    force group = tobydeemer krista administrator
    valid users = tobydeemer krista administrator

[StorageDrive]
    path = /media/disk
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
#    force user = tobydeemer krista administrator
#    force group = tobydeemer krista administrator
    valid users = tobydeemer krista administrator[/HTML]

---

### Post by Eiríkr on 2008-03-30
Looking over the global options for both conf files, I note the following:

[b][printing](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING) = CUPS
[printcap name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME) = CUPS[/b]

Have a look at the relevant man page sections by clicking through the links in the option names.  Both of these are *only* relevant within printer share definitions, and do *not* belong in the [global] section.  Delete these lines.  


[b][syslog](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOG) = 1
[syslog only](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOGONLY) = yes[/b]

The first one is already the default value, and may thus be removed for simplicity.  The second one shunts all Samba server messages into the /var/log/syslog file, rather than using the separate /var/log/samba/log.smbd and /var/log/samba/log.nmbd files.  If that's what you want, great.  


On the laptop, then:

**[wins server](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINSSERVER) = 192.168.1.67/255.255.255.0**

Judging from what the man page section says, this option might be unnecessary unless you're working across different subnets.  The address format here is also incorrect; the examples shown in the man page don't include the subnet mask (the part starting with the **_/_** slash).  Try commenting this line out, then restart your laptop's Samba server:
```
sudo /etc/init.d/samba restart
```
... and see if the laptop can see the server.  

----------

There are some wrinkles to file / directory creation and permissions to touch upon as well, but we can go over that later after you've gotten everything to where each machine can see the others.  :)  

If the GUI doesn't work (Places -> Network in Nautilus), try clicking in the Nautilus location bar (usually hidden by default, show by hitting Ctrl+L or clicking View -> Location Bar) and type in:
```
smb://IP.ADD.RE.SS
```
Replace the caps with the IP address of the other machine.  You can try with the hostname too to test if that works.  

Let us know how it goes!  :D

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-30
> **tobydeemer said:**
> And here's the one from the server:

[HTML]
[homes]
    valid users = krista tobydeemer administrator
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/
...

[Server_Share]
    path = /home/administrator/Server_Share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
#    force user = tobydeemer krista administrator
#    force group = tobydeemer krista administrator
    valid users = tobydeemer krista administrator

[StorageDrive]
    path = /media/disk
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
#    force user = tobydeemer krista administrator
#    force group = tobydeemer krista administrator
    valid users = tobydeemer krista administrator[/HTML]
**valid users=** is (or at least was) a comma-delimited list.
Dunno if that has anything to do w/ existing problem.

---

### Post by Eiríkr on 2008-03-30
Good catch, Iowan -- it does indeed look like this should be a comma-delimited list, as shown [here in the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS").  

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-03-31
Ok, another update (thanks again for all the help) - 

I've made the tweaks you've been listiing, and things are going more smoothly. I fixed the syslog entries, commented out the print lines, and fixed the winserver IP address entry.

On the laptop, using Places> Network still doesn't show the server, but if I type smb:// IP address into the address bar, it picks it up immediately and I can see all the shares set up on the server.

So now, one way or another, all the machines can see each other. I'm liking how this is working out.

Now that I'm here, what kinds of permission issues did you pick up on, or think may be part of the issue?

---

### Post by Eiríkr on 2008-03-31
I don't think the permissions will have anything much to do with name resolution -- for that, try commenting out the [font=courier]wins server[/font] line on your laptop and restart Samba:
```
sudo /etc/init.d/samba restart
```

Name resolution aside, the [font=courier]create mask[/font] and [font=courier]directory mask[/font] options generally strike me as a bit of a cludge to get around the need to properly configure permissions on the filesystem itself, and I see numerous instances of these Samba options leading to confusion.  In your case, I note that all files created via Samba will have only read and write permissions *just for the owner*, and all directories created via Samba will have only write permissions *just for the owner*.  This is likely not an issue for the [font=courier][homes][/font] shares, as the corresponding directory should only be accessible to each specific user, but your [font=courier][Server_Share][/font] and [font=courier][StorageDrive][/font] shares appear to be communal, and in this case, having files and directories that are supposed to be communally shared but are in fact locked down to one specific user can cause no end of confusion and frustration.  

I described how to configure filesystem permissions for Samba sharing for either a single-user or multi-user setup in [post=4496702]this post[/post], which I'd strongly recommend you look over.  Once the filesystem permissions have been properly configured, the mask/mode options in the smb.conf file are completely unneeded, and should be removed.  

HTH,

Eiríkr

---

### Post by tobydeemer on 2008-03-31
Hi-

Thanks for that. The file and directory permissions issues are exactly what I had run into yesterday and today. I just wasn't 100% on how to correct it. I had written some files to the storage drive with the XP station, and I went in to access them from the laptop and it said (surprise) that I did not have access permission, even for reading. So... once I get that sorted, I'm home free. 

At least until I want to try something else, but don't know how to do it... 

I'm at work right now, but once I get home, I will try those corrections and if all goes well, I should be able to mark this one solved. 

On a semi-related note, I had the idea today after reading about the recent Pwn 2 Own competition of turning the server into a network gateway/firewall. But now that I think more about it, I think I'd run into some hardware restrictions as it's an older machine (700 mhz, 384mb RAM) and Id' have to get an expansion network card to server the other machines, so... maybe I'll do a gateway/firewall machine when I am able to get a nicer server... moving on...

---

### Post by A$h X on 2008-03-31
Hi I'm having the same problem as tobydeemer, i.e i can type smb://192.168.1.3 to access a windows machine on my network, but it doesn't show up if I go places > network. On my windows machines my ubuntu shows up in network places but I get a error if i double click 192.168.1.2 (my ubuntu machine).
Any ideas?

---

### Post by Eiríkr on 2008-03-31
> **A$h X said:**
> Any ideas?

Yes: try following the recommendations in this thread.  That means starting at the beginning and reading through the whole thing, then implementing the required changes on your own filesystem and smb.conf file.  Then, if you still have problems, post again with as exact a description as possible of your symptoms, and a copy of your smb.conf file.  

Cheers,

Eiríkr

---

### Post by A$h X on 2008-04-01
Okay I've tried then many and varied suggestions on how to fix samba, but no joy I'm afraid. Here my smb.conf (I've removed sections where the entire thing was commented out):

```

[global]

## Browsing/Identification ###
security=user

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Homenet

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
  security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

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

[Shared]
path = /home/ashish/Shared
available = yes
browsable = yes
public = yes
writable = no
```

Someone please have mercy on this tired soul, I've been trying to sort this out for hours now, and I seem to be getting nowhere.

EDIT: My symptoms are as before, can't get windows machines to show up in places > network, now they seem have disappeared from "my network places" in XP as well, but in nautilus typing "smb://192.168.1.3" will open up the shared folder on the networked machine no problem. I recently installed firestarter so i have applied a rule to open the SMB ports as well. Still no luck.

---

### Post by tobydeemer on 2008-04-01
It looks like under your global section, you do not have WINS support enabled, and there are no "valid users" entries. If you have only the one Linux machine on the network, then it's easy to have it be the WINS server to the XP machines. Your security level is set to "User" but without defined users, it (I think) defaults to not allowing access to the share.

Did you go through the process of making user accounts on the Linux box (both as Linux users and Samba user accounts) that match the ones on the XP machines? If not, you'll have trouble authenticating to it. Also, under the Share Definitions for the file share, I didn't see any valid user lines, or permission types. (Obvioulsy from this thread I'm no expert, but those are things that I've had issues with, and may help...)

(Hopefully this gives you something to go on. I'm sorry if it doesn't.)

---

### Post by A$h X on 2008-04-01
Thnaks for the advice tobydeemer, just to address your points:

1) I think that as long your windows machines aren't acting as WINS servers (which they don't as default) then wins support = no isn't a problem.
2) Security level user is fine for just browsing a shared folder (I hope). I don't intend to have them poke around furhter than that.
3)  Obviously I have a ubuntu account, and have made samba accounts corresponding to my ubuntu username. As far as making them atch the XP accounts, there is only one account on the XP machine, and  it doesn't ask for authentication when you browse it remotely. If you click on a ubuntu share form a XP machine then you have to enter the samba user/pass.
4) And the most pertinent point is that EVERYTHIGN WAS WORKING FINE UNTIL 3 THREE DAYS AGO. One of the XP machines borked on me, and I had to create a new network so they could all see the problem machine. The network consists of 2 XP machines and my own machine which is a XP/ubuntu gutsy dual boot. If I boot into XP then all the machines can see each other and everything's fine. But it's when samba comes into play the problems start. And the other two XP's can see each other fine.

Oh and a last bit of detail is the result of  smbclient -L Alpha2:
```
 smbclient -L Alpha2
Connection to Alpha2 failed (Error NT_STATUS_BAD_NETWORK_NAME)

```

yet if I use the IP address of my machine then I get:

```
 smbclient -L 192.168.1.2
Domain=[ALPHA_2] OS=[Unix] Server=[Samba 3.0.26a]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        Shared          Disk      
        IPC$            IPC       IPC Service (alpha2 server (Samba, Ubuntu))
        PSC-1400        Printer   PSC-1400
        PDF             Printer   PDF
Domain=[ALPHA_2] OS=[Unix] Server=[Samba 3.0.26a]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        HOMENET              ALPHA_2

```

Samba gods please show me the way, for I have strayed.

---

### Post by tobydeemer on 2008-04-01
I think the Linux box acting as a WINS server is for the benefit of the XP machines. It's acting as a server to them, not the other way around which falls in line with XP not acting as WINS server by default. It would look for one on the network to authenticate against.

And I'm fairly certain that if security is set to user, then the Linux/Samba users must be listed and matched to any outside (like XP) users and passwords that are trying to get in. From Ubuntu browsing into an XP shared folder is usually not a problem. I was able to do that from my laptop into the XP workstation without ever installing Samba. It's getting XP to recognize and have access to the Linux machine that requires the tricky Samba setup.

But, again, I'm no expert by any means.

---

### Post by Eiríkr on 2008-04-01
@A$h X --

Just real quick (in the midst of several other things), but glancing over your smb.conf file, I noted a few stray options in your [global] section that don't belong (likely uncommented by a GUI tool?), which will need deleting -- specifically down in the commented [homes] section, you've got stray uncommented "browseable" and "writable" option lines that should go away.  

Also, I had similar problems with no shares listing despite successful IP address-based access, which I ultimately traced to two things -- I found that "wins support = yes" is a good thing with XP machines on your subnet, and I also discovered that in the course of tracking that one down, I'd managed to set the wrong broadcast address on one of my NICs in the mistaken assumption that 192.168.255.255 was a superset of 192.168.0.255.  The broadcast address probably isn't your issue, but I would seriously consider turning wins support on, and then restarting your Samba server.  

Also, check your nmbd log and see if there are any clear indications of something going funny (/var/log/samba/log.nmbd).  

Cheers,

Eiríkr

---

### Post by A$h X on 2008-04-02
After changing wins server = yes, nmbd.log had all sorts of error messages, so I put it back to wins server = no. I have discovered that smbclient -L Alpha2.homenet works, not sure why just alpha2 wouldn't work.
Also some good news from the XP side, even though my ubuntu machine doesn't show up in "my network places", if I goto run > \\alpha2 then my shared folder pops up along with my shared printer etc! I know I'm within touching distance, it's just one little thing I can feel it.

---

### Post by Eiríkr on 2008-04-02
Yeah, getting the shares going is much easier than getting full-on GUI browsability.  

Two questions pop to mind -- 1) Do you have a local DNS server on your network, or perhaps a customized /etc/hosts file (i.e. something you've set up yourself with the "homenet" domain name)?  2) Could you post the nmbd errors you saw when you had [font=courier]wins support = yes[/font]?  They might provide clues as to what needs fixing.  

Cheers,

Eiríkr

---

### Post by A$h X on 2008-04-02
Okay here's the errors from nmbd.log when WINS SERVER = YES was enabled.

```
[2008/04/02 11:59:03, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
  process_name_refresh_request: unicast name registration request received for name BETA1<20> from IP 192.168.1.3 on subnet UNICAST_SUBNET.
[2008/04/02 11:59:03, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
  Error - should be sent to WINS server
[2008/04/02 11:59:12, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
  process_name_refresh_request: unicast name registration request received for name HOMENET<00> from IP 192.168.1.3 on subnet UNICAST_SUBNET.
[2008/04/02 11:59:12, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
  Error - should be sent to WINS server
```

Once WINS SERVER = NO was set then alpha2 became the local master browser for homenet workgroup and no more errors were thrown. Is this a case of XP wanting to act as a WINS server? (I'm sure I double checked in network connections > TCP/IP >properties>advanced>WINS and it wasn't acting as WINS server).

Also there isn't anything acting as DNS server on my network (I just specify my IP's DNS servers in my router setup).

I haven't tinkered with my etc/hosts file, but it does contain the line
```
192.168.1.2 alpha2.HOMENET
```
Any ideas?

---

### Post by Eiríkr on 2008-04-02
I'm not sure how that entry got into your /etc/hosts file if you haven't done any manual network settings tweaking, but that would be why your smbclient command only works with that -- your Samba client isn't getting any name resolution data the Samba way, so it defaults to whatever it can find via other avenues, such as DNS or the hosts files.  

I dimly recall seeing similar nmbd error messages if the following options were not also set:
```
preferred master = yes
domain master = yes
local master = yes
```

Try adding those, toggling wins support to "yes", restarting Samba, and then see if you're getting those same nmbd log error messages.  

Cheers,

Eiríkr

PS -- those are [global] section options.  :)

---

### Post by A$h X on 2008-04-03
Good news: It works!

Bad news: I'm a moron!

Basically ALL it boiled down to was the recently insatlled firestarter. I had enabled the ports for SMB, but neglected to to allow the IP addresses of my XP machines. :oops:

After creating a rule to allow connections from the two XP machines, and restoring smb.conf to what it was before I tinkered with it, after a reboot on all three machines Alpha2, Beta1 and Delta1 could all see each in nautilus/network places. 

Apologies to Eiríkr for badgering him with pointless questions, and to tobydeemer for hijacking his thread. The only reason I installed firestarter was to use NXclient/SSH; I was told it was a GUI for IPtables, so I assumed all the same rules and policies would be enforced. How wrong was I?

---

### Post by Eiríkr on 2008-04-03
No worries A$h X, I had the same thing happen to me when trying to find out why Samba browsing wasn't working on my iBook -- and it turned out it was my firewall settings.  :shock:  Doh.  Glad it works now, though!  :D

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-04-03
No problem. Sorry I wasn't much use to the problem anyway. 

As for my issues, I'm still able to see and browse all my shares, but I am having trouble getting them to be writable. The XP shares are writable by the other two machines, but the Linux shares are not writable by either of the other two machines. I tried doing a chmod -R 0777 on the shares and setting the smb.conf to 0777 as well, to no avail. What am I missing...?

---

### Post by Eiríkr on 2008-04-03
What usernames are you using to access your Samba shares from the XP machines?

Looking over your [Server_Share] and [StorageDrive] share definitions from earlier in this thread, both should be writeable by any of the three valid users, tobydeemer, krista, or administrator.  

When you find you cannot write, are you writing to the share's parent directory, or to a sub-directory created by one of your Samba users?  If the latter, the directory mask of 0700 guarantees that only the owner will be able to do anything with this directory, and the create mask of 0600 guarantees that only the owner will be able to do anything with any files created in the share.  

Properly configuring communal access is a bit complicated.  (Forgive me if I'm repeating myself. :))  Since these two shares are ostensibly for communal use, start by creating a new group for Samba.  Then add all your Samba users to the group, and change the group on your shared directories to this group.  
```
sudo addgroup smbusers
sudo moduser -aG smbusers USERNAME   # Repeat for all three of your Samba users
sudo chgrp -R smbusers /PATH/TO/SHARED/DIRECTORY   # Repeat for all communal shares
```

In your smb.conf file, you should change the create mask to 660 and the directory mask to 770 to allow group access.  Then also add the option [font=courier]force group = smbusers[/font] to all communal share definitions.  

PS -- Without this force group option, new files and directories will default to the creator's primary group, rather than the communal smbusers group.

Cheers,

Eiríkr

---

### Post by tobydeemer on 2008-04-03
Once again I'm at work while reading your latest post, but that makes perfect sense now that it's all there on the page, and I will try it as soon as I get home and hopefully be back with most excellent news. Thanks again.

---

### Post by Eiríkr on 2008-04-03
Cheers!  Hope it works.  :)

Eiríkr

---

### Post by Deb.Early on 2008-04-09
Eiríkr, thanks so much for all the truly helpful info. I had the Samba share permissions stuff working, but I never liked what I had to do to *make* it work. I spent weeks searching for what I knew had to be the "correct" way to do it, and finally found this post. Your explanation made perfect sense, your solution was elegant, I got everything cleaned up.  :)

Enter cifs (sigh).  :(

How do I hate thee, cifs, let me count the ways. My understanding, unfortunately, is that beginning with Hardy, smbfs will become a "wrapper" for cifs -- forcing all of us to use the thing no matter what. So I'm trying to learn to use it.

The problem I've run into is this: file/directory permissions on a public share on my headless Gutsy fileserver work great per your configuration when I browse to it from any of my Gutsy workstations (using smb://<servername>). However, I have applications that can only see files on mounted volumes, so I mount the share with autofs on the wireless laptop, and in fstab on the wired Gutsy desktops. When the share filesystems are mounted on the workstations using cifs, permissions work differently.

[LIST=1]
[*]when I browse the share using smb://<servername>, all files/directory permissions show me as the owner, and I can change the permissions.
[*]when I browse the share from the mount point, the file/directory permissions may or may not show me as the owner, but for some reason Nautilus (Gnome, whomever) says I am NOT the owner, and I cannot change the permissions.
[/LIST]

Either way, I can still create, rename, delete files/directories on the mounted share, but the fact that I don't "own" anything and cannot change the permissions is bothersome.  AFAIC, if it's behaving funny, I'm not doing something right, and I'm risking messing up data on the server!  :eek:

Here is my smb.conf from the file server:
```
[global]
    netbios name = ELESSAR
    server string = ""
    workgroup = EPSILON
    socket options = TCP_NODELAY IPTOS_LOWDELAY

    wins support = yes
    name resolve order = wins bcast
    local master = yes
    domain master = yes
    preferred master = yes
    dns proxy = no

    passdb backend = tdbsam
    security = user
    encrypt passwords = true
    username map = /etc/samba/user.map
    invalid users = root

    load printers = no
    printing = bsd
    printcap name = /dev/null
    disable spoolss = yes

    syslog only = yes


[public]
    path = /mnt/raid/public
    comment = Public Share
    writeable = yes
    force group = earlylan
    create mask = 660
    directory mask = 770
```

I used your instructions in the other thread to add the "earlylan" group, mod the users, and change group ownership on the share itself.

Here is the top portion of auto.smb for the automount (it's using a "credfile" with my Samba username/pass in it):
```
#!/bin/bash

# $Id: auto.smb,v 1.3 2005/04/05 13:02:09 raven Exp $

# This file must be executable to work! chmod 755!

key="$1"
mountopts="-fstype=cifs,noperm,setuids,uid=dearly"
smbopts=""
credfile="/etc/auto.smb.$key"
```

Here is fstab line used by my desktop (server's IP removed):
```
//<server's IP address>/public /home/server cifs noperm,setuids,uid=dearly,credentials=/root/.smbcredentials  0   0
```

The cifs options I got from reading this man page: [http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs). I tried various combinations of options, but nothing seemed to help -- i.e. give me "ownership" of any of the files such that I could change the permissions like I could with the smb protocol.

I sure hope you're still checking this thread, because I trust your understanding of Samba permissions and really want to figure out why this is behaving differently under cifs and/or mount points.

Thanks if you read all this!
-Deb

---

### Post by Eiríkr on 2008-04-09
Nothing obvious pops up in the code snippets you've posted, which prompts me to ask what username you're using in your credentials file, and whether that username has the required filesystem permissions on the server side?  Also, is that username included in the user.map file, and if so, does the username that maps to have the required permissions?

It'd be helpful if you could run **ls -l** on the parent directory of your share, and post the results here.

Cheers,

Eiríkr

---

### Post by Deb.Early on 2008-04-09
Wow! That was fast! Thank you!

Okay -- I lied about the desktop.  :redface:  Apparently I'd forgotten to reload its fstab after adding the "setuids" and "uid" options to the cifs mount directive for the share. Permissions are now working as expected on the mounted share for both Ubuntu desktops. I'm assuming, now, that the server-side file permissions that you asked about (and I set up a couple of months ago, so I can't remember how I did that) are okay, yes?

Besides the fact that I need autofs for mobility, the laptop may just be an all-around messy situation. It was my first Ubuntu install, and I inadvertently created a "deb" initial user, instead of my usual "dearly" user on my XP OSs (desktop and laptop are dual-boots) and the Ubuntu on the desktop. So I've been logging into the fileserver's samba service as "dearly" from the laptop. That has always caused "trash can" confusion for Nautilus, and I was happy to find your very clear explanation of how username mapping works.

```
dearly@elessar:~$ cat /etc/samba/user.map
dearly=deb
```

In /root/.smbcredentials and /etc/auto.smb.elessar (password removed to protect the innocent!):

```
username=dearly
password=<samba server password>

```

If I understood you correctly, user "deb" doesn't need to be an actual Samba or unix user on the server?

Here's the server ls:

```
dearly@elessar:~$ sudo ls -lha /mnt/raid
total 12K
drwxrwxr-x  3 root earlylan   16 Mar 22 17:29 .
drwxr-xr-x  3 root root     4.0K Mar 22 11:32 ..
drwxrwsr-x 22 root earlylan 4.0K Apr  8 22:08 public
dearly@elessar:~$
```

Actually, these ownerships bothered me when I first saw them after running "sudo chgrp -R earlylan /mnt/raid" on the server. I wasn't sure if by "/PATH/TO/SHARE" you meant just the *path* to the share (in my case /mnt/raid on the server), or to include the name of the shared *folder* on the share (/mnt/raid/public). I've been at this for weeks and am so information-overloaded -- most of it conflicting! -- that my memory isn't extending much beyond a couple of minutes anymore, but if I recall correctly, I believe I typed "sudo chgrp -R earlylan /mnt/raid". If that was wrong, I sure hope I can fix it without screwing up stuff...?

One thing that surprised me was that the "sudo chgrp -R earlylan /mnt/raid" command (from your other thread) took a looooong time to return, and when it did, all the group ownerships on the share had been changed to "earlylan". The "find" command which I executed next came back immediately, as if it found nothing to change -- which looked understandable. Again, is that an indication that I specified the wrong path?

Thanks so much for reading all this. I've been muddling around here for so long that my brain is running out my ears...  ;)

---

### Post by Eiríkr on 2008-04-09
> **Deb.Early said:**
> Wow! That was fast! Thank you!

No trouble.  I'm probably on the boards more than I really should be... :redface:

> **Deb.Early said:**
> Okay -- I lied about the desktop.  :redface:  Apparently I'd forgotten to reload its fstab after adding the "setuids" and "uid" options to the cifs mount directive for the share. Permissions are now working as expected on the mounted share for both Ubuntu desktops. I'm assuming, now, that the server-side file permissions that you asked about (and I set up a couple of months ago, so I can't remember how I did that) are okay, yes?

They should be, provided you have the expected permissions to the shares upon logging into them. 

> **Deb.Early said:**
> Besides the fact that I need autofs for mobility, the laptop may just be an all-around messy situation. It was my first Ubuntu install, and I inadvertently created a "deb" initial user, instead of my usual "dearly" user on my XP OSs (desktop and laptop are dual-boots) and the Ubuntu on the desktop. So I've been logging into the fileserver's samba service as "dearly" from the laptop. That has always caused "trash can" confusion for Nautilus, and I was happy to find your very clear explanation of how username mapping works.

Glad that came in handy.  :)

> **Deb.Early said:**
> ```
dearly@elessar:~$ cat /etc/samba/user.map
dearly=deb
```

In /root/.smbcredentials and /etc/auto.smb.elessar (password removed to protect the innocent!):

```
username=dearly
password=<samba server password>

```

If I understood you correctly, user "deb" doesn't need to be an actual Samba or unix user on the server?

Provided that user "deb" is indeed the remote username (which it should be looking at your mapping file), then yes, it does not need to be an actual Samba or Unix user on the server machine.  In your case here, user "dearly" *does* have to be a valid user on the server, but it sounds like it is, so you should be fine.  

> **Deb.Early said:**
> Here's the server ls:

```
dearly@elessar:~$ sudo ls -lha /mnt/raid
total 12K
drwxrwxr-x  3 root earlylan   16 Mar 22 17:29 .
drwxr-xr-x  3 root root     4.0K Mar 22 11:32 ..
drwxrwsr-x 22 root earlylan 4.0K Apr  8 22:08 public
dearly@elessar:~$
```

Actually, these ownerships bothered me when I first saw them after running "sudo chgrp -R earlylan /mnt/raid" on the server. I wasn't sure if by "/PATH/TO/SHARE" you meant just the *path* to the share (in my case /mnt/raid on the server), or to include the name of the shared *folder* on the share (/mnt/raid/public). I've been at this for weeks and am so information-overloaded -- most of it conflicting! -- that my memory isn't extending much beyond a couple of minutes anymore, but if I recall correctly, I believe I typed "sudo chgrp -R earlylan /mnt/raid". If that was wrong, I sure hope I can fix it without screwing up stuff...?

It looks like /mnt/raid and everything currently in it has the primary group of "earlylan", and the /mnt/raid/public directory also has the setgid bit set.  This sounds good for what you've described.  

> **Deb.Early said:**
> One thing that surprised me was that the "sudo chgrp -R earlylan /mnt/raid" command (from your other thread) took a looooong time to return, and when it did, all the group ownerships on the share had been changed to "earlylan". The "find" command which I executed next came back immediately, as if it found nothing to change -- which looked understandable. Again, is that an indication that I specified the wrong path?

Not necessarily; for one, your path looks right to me, and for two, chgrp and chown and chmod can all take a while to return if using the **-R** recursive option on directory trees that contain lots of files.  The "find" command only deals with the directories, of which there are fewer, so it makes sense that it wouldn't take as long.

> **Deb.Early said:**
> Thanks so much for reading all this. I've been muddling around here for so long that my brain is running out my ears...  ;)

It happens.  ;)  But as you go, the learning curve gradually gets easier.  

Cheers,

Eiríkr

---

### Post by Deb.Early on 2008-04-09
Update: share ownership is now straightened out on the laptop.

It was ugly. The clue was in [this bug report]("https://bugs.launchpad.net/samba/+bug/106146"). Since my laptop username is "deb", of *course* I didn't own anything owned by "dearly". What freaks me out is that I was able to change, rename, and delete stuff that was "owned" by "dearly", given how utterly unforgiving cifs is about pretty much everything.

So just to be silly, I changed the uid option in /etc/auto.smb from "dearly" to "deb", restarted the automounter -- and problem solved. All server share folders/files are owned by "deb". Like I said, freaky. With any luck, I may yet figure out who owns what where, and if they really do.  :shock:

In any case, it looks like mounting Samba shares using cifs in fstab/autofs is a rather different animal than browsing to the share using smb. To get cifs mounts to work with the reconfigured server permissions, I had to use both the "setuids" and "uid" options -- even though the man page for mount.cifs states:

> uid=arg

sets the uid that will own all files on the mounted filesystem. It may be specified as either a username or a numeric uid. This parameter is ignored when the target server supports the CIFS Unix extensions.

I'm guessing that the "noperm" option/bug makes the uid option necessary (even when the uid on the client machine is the same as that of the Samba user on the server; i.e. "dearly" on the desktop, which still needs to set uid=dearly), and my experience was that the uid option really is ignored unless you also include the setuids option. It's a house of cards, and the terminology on that man page is inconsistent and unclear. No wonder folks are getting migraines over cifs.  :(

Anyway, thanks tons and tons for straightening me out with Samba! Do let me know if I messed up and did something Really Dumb with the share permissions on the server, however...

Cheers back!
-Deb

---

### Post by Deb.Early on 2008-04-09
> Do let me know if I messed up and did something Really Dumb with the share permissions on the server, however...

Looks like we were writing posts simultaneously! Thanks for putting my mind at rest.

Hopefully my flopping around will help others wrestling with mounts/cifs/multiple userids -- now that you've set all of us right with Samba share permissions!

---

### Post by Deb.Early on 2008-04-09
> What freaks me out is that I was able to change, rename, and delete stuff that was "owned" by "dearly", given how utterly unforgiving cifs is about pretty much everything

You know, the more I look at that statement, the more it seems like there should be a bug filed against something somewhere. I mean; I could change, rename, heck -- even *delete* something I didn't own, but Nautilus sure as shootin' wasn't going to let me change those permissions!   :lolflag:

---

### Post by Eiríkr on 2008-04-10
I must admit that at a remove, it's quite confusing trying to sort through all the details, so I'm glad you sorted things out.  

Incidentally, looking back over your **ls -l** results, the reason you could do all that even though "deb" was not the owner was because "deb" was apparently still a member of the "earlylan" group, and group members are allowed to do just about everything to a file or directory with rwx group perms -- except for change the perms.  This is normal filesystem security behaviour, actually, and it has nothing to do with CIFS.  

As an experiment, open a terminal and try the following.  You'll see what I mean.  Log in first as "user_a".  (Replace "user_a" and "user_b" with any two users actually on your system.  Assumes that both are members of the "earlylan" group.)
```
cd
touch TEST                  # Create test file
ls -l                       # Will show owner as "user_a" and group as "user_a"
chmod g+rwx ./TEST          # Grants group members total control
sudo chgrp earlylan ./TEST  # Changes file group to "earlylan" -- owner is still "user_a"
sudo chown user_b ./TEST    # Changes file owner to "user_b" -- group is still "earlylan"
```
At this point, "user_a", as a member of the "earlylan" group, will be able to do anything to file TEST -- **except** for change the permissions.  Any non-sudo attempt at chmod will fail, even though the file itself can be deleted or overwritten.  

Here's a wrinkle actually explained on [a good page about Unixy permissions for Mac users]("http://www.osxfaq.com/tutorials/learningcenter/AdvancedUnix/ugp2/index.ws"), but still applicable for us:
> Having write permission for a directory means you can change it - i.e. create and remove files within that directory. **The point being that having write access to a directory allows one to delete a file from the directory no matter what the permissions for the file.**

If you're interested in learning more about Unixy filesystem perms, I'd actually recommend you read over the "Advanced Mac OS X Unix" section towards the bottom of [this page](http://www.osxfaq.com/tutorials/learningcenter/index.ws), where I got the quote above.  Just note that "chflags" in Mac and BSD terms is "chattr" on Linux systems, and most else is the same.  

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-04-10
@Deb.Early --

As a belated addendum, I was looking again at your [global] options and noted the following that can (should?) be removed:
```
printing = bsd
printcap name = /dev/null
```
Both of these options are *only* relevant within a printer share definition, and do not belong in the [global] section.  

Cheers,

Eiríkr

---

### Post by Phulerock on 2008-04-10
remember run smbpasswd 2 user "tobydeemer" "krista" "administrator" on you latop
I thinks you should set 0777 you sharing folder, its safe because you have the option valid user , dont worry about 0777 can be a security risk or vulnerability.
so :

[MyFiles]
    path = /home/tobydeemer/laptop_share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0755
    valid users = tobydeemer krista administrator

and 
smbpasswd *your_smb_user* 
and.. try again 

Hope this help

---

### Post by Phulerock on 2008-04-10
@ tobydeemer: what diagram software you using ? is it work in Linux, your diagram very kool, I only know DIA

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> Incidentally, looking back over your **ls -l** results, the reason you could do all that even though "deb" was not the owner was because "deb" was apparently still a member of the "earlylan" group, and group members are allowed to do just about everything to a file or directory with rwx group perms -- except for change the perms.  This is normal filesystem security behaviour, actually, and it has nothing to do with CIFS.

The fog really is beginning to clear as a result of this exercise, and for that I am grateful to you. Clearly it was indeed due to the fact that user "deb" maps to user "dearly", who is a member of the "earlylan" group on the server.

I did actually play around with the users and systems like you suggested and observed the behavior. Interesting how that works. 

The "setuids" and "uid" options in the CIFS mount directive, however, did appear to affect how the permission bits were set on new files. For example; when the directive on my husband's desktop is (and jearly is a member of "earlylan" on the server):
```
//<server IP>/public /home/server cifs noperm,credentials=/root/.smbcredentials  0   0
```
...files are created on the server like so:
```
dearly@elessar:~$ ls -la /mnt/raid/public/dropbox/jimNoPermOnly.txt
0 -rw-r--r-- 1 jearly earlylan 0 Apr 10 11:26 /mnt/raid/public/dropbox/jimNoPermOnly.txt
```
If I'm understanding this correctly, all "earlylan" group members can change/rename/delete the file (parent folder permissions drwxrwsr-x), only jearly (or root) can change the permissions, and the file is world-readable.

When the "setuids" and "uid" options are included in the mount directive (and fstab reloaded!):
```
//<server IP>/public /home/server cifs noperm,setuids,uid=jearly,credentials=/root/.smbcredentials  0   0
```
...permission bits for new files are set like so:
```
dearly@elessar:~$ ls -la /mnt/raid/public/dropbox/jimtext.txt
4 -rw-rw---- 1 jearly earlylan 13 Apr 10 09:35 /mnt/raid/public/dropbox/jimtext.txt
```
Then a newly-created file is *not* world-readable. 

I'm not sure I'm understanding why a file is created world-readable without those 2 options, and no world bits set at all *with* the options. Make any sense to you? (if that's a dumb question, gets too involved, or starts diverting the thread, don't bother...)

But overall, the "lights are coming on" and it looks like everything is pretty much working as designed.

Thanks so much for the link. The material is wonderfully written. In fact, I would heartily encourage anyone seeking help from this thread to check out the [entire tutorial set]("http://www.osxfaq.com/tutorials/learningcenter/index.ws"). I was a senior technical writer for IBM (API documentation, among other things) for several years, and was regarded there as something of a "black sheep" due to my very firm belief that even the most complex subject can be explained in simple, clear terms!  :)

Ciao for now!
-Deb

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> As a belated addendum, I was looking again at your [global] options and noted the following that can (should?) be removed:
```
printing = bsd
printcap name = /dev/null
```
Both of these options are *only* relevant within a printer share definition, and do not belong in the [global] section.

Ah, gotcha. I see that now in the man page. Another example of conflicting information and going with "whatever worked" to shut Samba up!

Thanks!

---

### Post by Eiríkr on 2008-04-10
I'm not really familiar with the **noperm** mount option for cifs and how that might affect things, but I suspect that this option is a key component of what you're seeing.  

In the first **ls -l** example you give, the permissions show up as:
```
-rw-r--r--
```
This indicates that the file is actually *not* fully accessible by group members -- the second triple of **r--** shows that group members can only read the file.  (Whether or not they can delete it depends on whether they have write permission on the directory, per the note from the Mac Unix site.)  Oddly, it looks like new files created via this mount are ignoring the conf file **create mask** setting, which specifies that new files should be readable *and* writable for group members::

```
create mask = 660
directory mask = 770
```

The second **mount** and **ls -l** example above shows the expected 660 permissions, with rw- for both the first (owner) and second (group) triples, but no perms at all for the third (others) triple.  

What kind of results do you get with this line instead in your /etc/fstab file?
```
//<server IP>/public /home/server cifs credentials=/root/.smbcredentials  0   0
```

Cheers,

Eiríkr

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> I'm not really familiar with the **noperm** mount option for cifs and how that might affect things, but I suspect that this option is a key component of what you're seeing.

Me too.  

> Oddly, it looks like new files created via this mount are ignoring the conf file **create mask** setting, which specifies that new files should be readable *and* writable for group members::

```
create mask = 660
directory mask = 770
```

I noticed that myself. Head scratcher. Glad to see I'm not alone -- maybe I'm learning!  ;)

> What kind of results do you get with this line instead in your /etc/fstab file?
```
//<server IP>/public /home/server cifs credentials=/root/.smbcredentials  0   0
```

All kinds of "permission denied"s because the numeric user IDs do not match up between the client and server Ubuntu machines. Re [this documentation]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"), bottom of the page, and numerous BB posts such as [this one]("http://help.lockergnome.com/linux/smbmount-Permission-Denied-ftopict480586.html"). CIFS is not a hugely popular filesystem with newbies like myself.  :(

---

### Post by Eiríkr on 2008-04-10
This is very interesting to me -- I've been using the CIFS filesystem type for ages, but I've never run into this.  UID and GID issues are familiar from setting up NFS shares, but I was under the impression that Samba used user and group **names** instead of the numeric IDs.  The **man mount.cifs** page even suggests as much:
> **uid=_arg_**
sets the uid that will own all files on the mounted filesystem. It may be specified  as either  a  username  or a numeric uid. 
I'm booted into Win XP now so I can't check my own client fstab file, but if memory serves, it's extremely simple, something like:
```
//<server name>/share /mnt/share cifs auto,rw,credentials=/root/.smbcredentials  0   0
```

Incidentally, what versions of Ubuntu and Samba do you have on your server and client machines?

Cheers,

Eiríkr

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> This is very interesting to me -- I've been using the CIFS filesystem type for ages, but I've never run into this.  UID and GID issues are familiar from setting up NFS shares, but I was under the impression that Samba used user and group **names** instead of the numeric IDs.  The **man mount.cifs** page even suggests as much:

I messed up on that -- it's just the UID. I'm not sure, but I believe I read somewhere that if you don't explicitly set the **uid** option, it defaults to the numeric UID of the user on the client machine. The local UID for the primary user account on each of my Ubuntu desktop clients is 1000. The UIDs for the corresponding user accounts on the server machine begin at 1001 and increment for each user -- ergo nobody matches. There's a bug filed somewhere over this issue.

> Incidentally, what versions of Ubuntu and Samba do you have on your server and client machines?

They're all the i386 version of Gutsy: the server I installed from the server CD (not the alternate), the clients all from the desktop CD. The server has nothing on it but Samba, OpenSSH, mdadm (for a SATA RAID1 array in jfs format), beep, and NTP. Samba version on all machines is 3.0.26a.

---

### Post by Deb.Early on 2008-04-10
> **Deb.Early said:**
> ... I believe I read somewhere that if you don't explicitly set the **uid** option, it defaults to the numeric UID of the user on the client machine

Actually, scratch that. Before I started explicitly setting **uid** in fstab, the owner of all the server files was displayed as "1003" -- the UID of the "dearly" user on the server. So it must default to the UID of the server-side user account. Either way (and maybe it's not a "default" issue at all...), they don't match. This statement in the Ubuntu doc wrt the **noperm** option now clarifies the client-side "permission denied" messages: > Remote permissions and UIDs will still be visible, but they will not be enforced locally

---

### Post by Eiríkr on 2008-04-10
Aha!  :idea::o  (Eureka moment here.)  You're not mapping usernames between the server and the client.  If you'd like to do this, methinks you can avoid the non-matching UID problem.  If Samba can't match the usernames, it will try to match on the basis of the numeric IDs, but with your setup, "dearly" and "deb" clearly don't match, and apparently their numeric IDs don't match either.  Look over [post=4496702]this post[/post] and scroll down to the "In the [global] section" portion, where I go into username mapping.  

Cheers,

Eiríkr

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> Aha!  :idea::o  (Eureka moment here.)  You're not mapping usernames between the server and the client.

But... but... but...! Awww, now you got me all confuzzed again!  :-k

Yesterday I dutifully read through both that thread and this one, constructed a username map file on the server as shown in the top part of [this post]("http://ubuntuforums.org/showpost.php?p=4685992&postcount=37"), and added the corresponding line
```
username map = /etc/samba/user.map
```
to the Global section of the server's smb.conf. That works famously for my laptop -- which is the "deb" user that got inadvertently created instead of the "dearly" I use for all my other personal machines/OSs. But the laptop still throws "permission denied"s on server share access without that **noperm** option in its /etc/auto.smb file; presumably because "dearly" exists on the server with UID 1003 -- and both "deb" and "dearly" are "1000" on the clients.

Are you saying that I should add lines like "dearly=dearly" and "jearly=jearly", etc., to the map file? I guess I could try that...

But just to clarify, I used desktop clients -- not the laptop (which I don't trust for those sorts of tests) -- with actual server-side accounts when I got the file-creation weirdness.

---

### Post by Eiríkr on 2008-04-10
Doh!  :shock:  No, I don't mean "dearly=dearly" (though maybe that's worth a try?) -- somehow in going back over your previous posts and conf file (which does not include the usermap line), I'd missed / forgotten that you do indeed have mapping set up.  My bad.  

So for the desktop clients you used for testing, what username were you using?

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> Doh!  :shock:  No, I don't mean "dearly=dearly" (though maybe that's worth a try?)

Whew! Thought it was me, again.  As for giving that a try -- well...

First of all:
> So for the desktop clients you used for testing, what username were you using?
 I logged in as "dearly" on my own desktop, and as "jearly" on my husband's desktop. Our normal working setup, both pretty much vanilla Gutsy/XP dual-boot boxes. Those usernames are each UID 1000 on their respective Ubuntus. Usernames are the same for both OSs.

Okay.

Close your ears, cause I'm gonna swear...  ***&@%$@!!**  Now that I feel a little better, a question: does Samba cache username maps? If so, happen to know if that cache is persistent across system boots? If it is, happen to know how to *flush* the dumb thing?

The reason I ask is, I *did* try adding "dearly=dearly" (and "jearly=jearly", btw. Stupid me.) to the server's user.map file, restarted Samba on the server, and now ALL the flipping files I create on the server's share from ANY Ubuntu desktop are being created with the "odd" permissions (**-rw-r--r--**) -- no matter *what* options I use to mount the share. With and without **noperm**, with and with **uid** and **setids** (umounting/remounting the share, of course), even rebooted the desktops AND the server!  :confused:  

Bizarrely, files created from the same desktop machines booted to XP are still created with the "expected" permissions: **-rw-rw----**.
```
dearly@elessar:~$ ls -lah /mnt/raid/public/dropbox
total 9.1M
drwxrwsr-x  3 nobody earlylan 4.0K Apr 10 19:17 .
drwxrwsr-x 22 root   earlylan 4.0K Apr  8 22:08 ..
-rwxrw-rw-  1 nobody earlylan 3.7M Mar 14 12:32 Samba3-ByExample.pdf
-rwxrw-rw-  1 nobody earlylan 5.4M Mar 14 12:32 Samba3-HOWTO.pdf
-rw-r--r--  1 jearly earlylan    0 Apr 10 19:12 anotherJimTest.txt
-rw-rw----  1 jearly earlylan    0 Apr 10 19:17 anotherJimXPTest.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 14:56 desktopFileWithNPSUIDand1ServerusermapLine.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 14:45 desktopFileWithNoperm.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 14:48 desktopFileWithNopermAndSetUID.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 18:42 desktopFileWithoutNoperm.txt
-rw-r--r--  1 jearly earlylan    0 Apr 10 11:26 jimNoPermOnly.txt
drwxrws---  2 jearly earlylan    1 Apr 10 09:34 jimtest
-rw-rw----  1 jearly earlylan   13 Apr 10 09:35 jimtext.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 15:01 letsTryThatAgainAfterServerReboot.txt
-rw-r--r--  1 dearly earlylan    0 Apr 10 15:09 letsTryThatYetAgain.txt
-rw-rw----  1 dearly earlylan    0 Apr  9 22:29 winxp.txt
dearly@elessar:~$
```

Man, I dunno. Maybe I should'a just left "well enough" alone. I don't want to hog your time, so I'm going to restore the server's smb.conf and user.map files back to exactly the way they were this morning, reboot the machine, and let it quietly MARK away until tomorrow. Maybe there's a cache with a timeout somewhere that will flush between now and then. This really does smell like a cache thing to me.

---

### Post by Deb.Early on 2008-04-10
> **Eiríkr said:**
> ...going back over your previous posts and conf file (which does not include the usermap line)

"...but it does!", she said in a small voice: 
```
username map = /etc/samba/user.map
```

;)

---

### Post by Eiríkr on 2008-04-10
Oofda.  Just color me blind, as well as generally addlepated.  :redface:  

As to what's going on, I suspect that the so-called CIFS Unix extensions might be at work, since you *only* seem to get the funny perms on new files created by clients logged in from Unixy machines.  What I *think* is happening is that, rather than respecting the masks defined in the smb.conf file, the Samba server is instead basing new file (and probably directory too?) perms on the umask of the user doing the creating.  Log into one of your desktop systems and type **umask** at the prompt, and I bet you'll see something like 0022.  The umask is mostly like chmod octal permissions in reverse, and this equates to 0644 for files and 0755 for directories -- 644 equates to rw-r--r--, exactly what you're finding.  

Out of curiosity, what happens to the perms on new files if you mount manually, instead of relying on fstab, using the following?
```
sudo mount -t cifs -o rw,username=dearly,password=PASSWORD,uid=dearly,gid=dearly //<server IP>/public /home/server
```

Eiríkr

---

### Post by Deb.Early on 2008-04-11
> **Eiríkr said:**
> ...generally addlepated.  :redface:  Hey, that's my job. You're probably too young!  ;)

> **Eiríkr said:**
> As to what's going on, I suspect that the so-called CIFS Unix extensions might be at work, since you *only* seem to get the funny perms on new files created by clients logged in from Unixy machines.  What I *think* is happening is that, rather than respecting the masks defined in the smb.conf file, the Samba server is instead basing new file (and probably directory too?) perms on the umask of the user doing the creating.
But wouldn't that mean a server admin can't really enforce security on the share? Man, the implications of that are *too ugly*. And I can't believe my silly systems are so misconfigured as to break something that's been working successfully for years and years...

> Log into one of your desktop systems and type **umask** at the prompt, and I bet you'll see something like 0022.
That's exactly what I saw. But again, I shudder to think a measly client machine could be overriding an explicitly configured server.

> Out of curiosity, what happens to the perms on new files if you mount manually, instead of relying on fstab, using the following?
```
sudo mount -t cifs -o rw,username=dearly,password=PASSWORD,uid=dearly,gid=dearly //<server IP>/public /home/server
```

```
-rw-r--r--  1 dearly earlylan       0 Apr 11 05:29 testFile.txt
-rw-r--r--  1 dearly earlylan       0 Apr 11 05:33 testFile2.txt
drwxrws---  2 dearly earlylan       1 Apr 11 09:29 testFolder
drwxrws---  2 dearly earlylan       1 Apr 11 09:33 testFolder2
```
testFile and testFolder were created from the desktop on the share mounted as follows:
```
//<server IP>/public /home/server cifs noperm,setuids,uid=dearly,credentials=/root/.smbcredentials  0   0
```
I umounted the share, then mounted from the command line per your template, then created testFolder2 and testFile2. As you can see, new folders are being created as expected no matter how the share is mounted. New files, however, are still weird with both mount methods. 

Because "jearly" isn't a member of the "admin" group on the server ("dearly" is), I also tried this from my husband's desktop. Same result -- weird file permissions, good folder permissions. There's *gotta* be a clue in there somewhere.

Just to be sure my addled pate (see, *mine*!) hadn't inadvertently missed something, I went back and double-checked the [smb.conf]("http://ubuntuforums.org/showpost.php?p=4684944&postcount=35") and [username map]("http://ubuntuforums.org/showpost.php?p=4685992&postcount=37") on the server. They are both still identical to the ones in the linked posts, and I took the server down to pull a serial port last night, so I know they're in effect now.

What's driving me crazy is that at first, files were being created properly from the Unixy machines. You witnessed it yourself in [this post]("http://ubuntuforums.org/showpost.php?p=4691537&postcount=46"), and the files are still there (jimtest.txt) in the **ls** quote above. For the *LIFE* of me, I can't think of anything I changed between now and then.

](*,)

I should probably give it up since all the machines can work with the server, but it really creeps me out when things don't work as expected -- especially on a file server. It means something is just *wrong*, somewhere.

---

### Post by Deb.Early on 2008-04-11
> What I think is happening is that, rather than respecting the masks defined in the smb.conf file, the Samba server is instead basing new file (and probably directory too?) perms on the umask of the user doing the creating.
You know, the more I play around with this, the more I am convinced you hit the nail squarely on the head with that. Only now I don't think it has anything to do with CIFS (unless SMBFS is really CIFS in disguise in Gutsy, which I don't believe is the case). Switching back to using SMBFS instead of CIFS in /etc/fstab didn't change anything; files are still created using the user's mask. 

On my systems, at least, the one totally predictable common denominator is mounting the server share locally. In that case, it looks like Samba is indeed applying the user's (22) mask to all files created on the share -- *no matter what*. Scarier still, Samba *does* appear to be applying the server's mask (770) to newly created directories -- *no matter what*.

I even tried this smb.conf on the server:
> [public]
    path = /mnt/raid/public
    comment = Public Share
    writeable = yes
    force group = earlylan
    force create mode = 660
    directory mask = 770
As long as I browse to the share using SMB, new files are created with the "correct" bits set: 
```
-rw-rw----  1 dearly earlylan    0 Apr 11 12:28 laptopSMBFile.txt
```
But files created on the share at a local mount point are always **-rw-r--r--**:
```
-rw-r--r--  1 dearly earlylan    0 Apr 11 12:48 laptopForceCreateMode.txt
-rw-r--r--  1 dearly earlylan    0 Apr 11 12:51 laptopUsingSMBFS.txt
-rw-r--r--  1 dearly earlylan    0 Apr 11 12:34 laptopWithCreatemaskInGlobal.txt
-rw-r--r--  1 dearly earlylan    0 Apr 11 12:32 laptopwithUID.txt
```

This is making my hair stand on end. As long as their servers are allowing clients to work with permanently mounted public shares, I wonder if folks are actually bothering to check to see if the server is applying the masks specified in its smb.conf?

---

### Post by Deb.Early on 2008-04-11
I did some more looking around on the forums and came up with [this post]("http://ubuntuforums.org/showpost.php?p=3989586&postcount=4"), which "fixed" everything. Even though the security mode/mask options are targetted to Windows clients, they seem also to be required for Samba to enforce file creation masks for an Ubuntu client that permanently mounts a share to the local filesystem:
```
[public]
    path = /mnt/raid/public
    comment = Public Share
    writeable = yes
    force group = earlylan
    security mask = 660
    force security mode = 660
    directory mask = 770
```
Not pretty, and not strictly "kosher" according to the smb.conf man page, but it works.

At least now I know there are some legitimate server-side enforcement issues with  permanent mounts, and it's not just me or something I did horribly wrong. That's a Big Relief!

---

### Post by Eiríkr on 2008-04-11
That is just completely **messed up**.  I'll have to test on my own Ubuntu -> Ubuntu share to confirm, and then I definitely think a bug report is in order.  I won't be able to test until possibly early May at the rate my schedule is going though...

Thinking things thourgh a bit more, and reading through the smb.conf man page sections on forcing security modes, I note that there are also share definition options for [force directory mode]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEDIRECTORYMODE") and [force create mode]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE").  From the **force create mode** section:

> This parameter specifies a set of UNIX mode bit permissions that will **always** be set on a file created by Samba. 

The emphasis they put on "always" makes me think that the create mode option might therefore be ignored or overridden in some circumstances, possibly *by design*.  From the [create mask]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK") section:
> When a file is created, the necessary permissions are calculated according to the mapping from DOS modes to UNIX permissions, and the resulting UNIX mode is then bit-wise 'AND'ed with this parameter. This parameter may be thought of as a bit-wise MASK for the UNIX modes of a file. Any bit *not* set here will be removed from the modes set on a file when it is created.
Reading this again, it sure sounds like the behaviour you describe is **not** what is intended, at least according to the man page.  That said, does using the **force create mode** option work, instead of using the **force security mode** option (which as you note is intended for WinNT clients)?

Befuddled,

Eiríkr

---

### Post by Deb.Early on 2008-04-11
> **Eiríkr said:**
> That is just completely **messed up**.  I'll have to test on my own Ubuntu -> Ubuntu share to confirm, and then I definitely think a bug report is in order.
Wow.
> Reading this again, it sure sounds like the behaviour you describe is **not** what is intended, at least according to the man page.  That said, does using the **force create mode** option work, instead of using the **force security mode** option (which as you note is intended for WinNT clients)?
> This parameter specifies a set of UNIX mode bit permissions that will **always** be set on a file created by Samba.
I saw that too, and **force create mode** was one of the first things I tried this morning (see smb.conf code in [this post]("http://ubuntuforums.org/showpost.php?p=4697581&postcount=60")) -- and was utterly shocked when that *also* was ignored. In fact, to get the total desired new file permissions on a permanently mounted share (i.e. the same ones you get with the SMB protocol), *both* **security mask** and **force security mode** service options were required on the server. I couldn't get away with one and not the other -- stray bits would get set/not set.

Messed up indeed.

---

### Post by tobydeemer on 2008-04-11
> **Phulerock said:**
> @ tobydeemer: what diagram software you using ? is it work in Linux, your diagram very kool, I only know DIA

Hi-

Sorry for the late reply. That diagram is actually a coddled-together piece that I made in Inkscape using some SVG icons from a set called "Black-and-White_Neon-2". I think I linked to it in one of the earlier posts. I'm glad you liked it though.

As for the Samba problems, I still have yet to get it all finalized. This week has been mad crazy since it's my daughter's first birthday so we're getting ready for that, and then there was this huge family argument with my folks, blah blah blah.... all to say, I'm still working on it, and today was the first day I've been able to touch my server this week. 

I know none of you want to hear all that, but I'm still having a go at it. To be continued...

---

### Post by Deb.Early on 2008-04-11
Just to nail down in my own mind that the issue is independent of CIFS, I did a series of SMBFS tests on my husband's desktop (a fresh, generic, Ubuntu install). To make a long story short, when the client mounted the server share in /etc/fstab, the server ignored the **create mask** *and* the **directory mask** options in its own smb.conf, using instead the client's mask (22) for all new files/folders that the client created on the share. This is totally different behavior than when the client browses to the share using **SMB//:**, and creates files/folders from there.

Only when the server's smb.conf looked like this (as per the [other post]("http://ubuntuforums.org/showpost.php?p=3989586&postcount=4")):
```
[public]
    path = /mnt/raid/public
    comment = Public Share
    writeable = yes
    force group = earlylan
    security mask = 0660
    force security mode = 0660
    directory mask = 0770
    force directory mode = 0770
    force directory security mode = 0770
```
were new files and folders **reliably** created with the expected permissions on a permanently mounted share (/etc/fstab).

Yeah, I know -- I said new folders were being created with the expected permissions "no matter what". That seems to change when you start creating folders within a folder that is actually **owned** by the user, then they get client permissions too. Or something like that. I dunno. After a week of headaches and late nights I've got something that *appears* to work (probably until somebody tries to change the permissions of a server file from an XP client using the standard Windows permissions dialog box, sigh...), and now I'm remembering Real Good why I retired from this work!

Anyway -- Eiríkr rocks!   ;-)

P.S: I don't know why this would make a difference, but the filesystem on my server's share is JFS. (of course it will all come clear to somebody after that little remark and I will have wasted hours and hours and hours of everyone's valuable time... :oops:)

---

### Post by tobydeemer on 2008-04-16
> **Eiríkr said:**
> What usernames are you using to access your Samba shares from the XP machines?

Looking over your [Server_Share] and [StorageDrive] share definitions from earlier in this thread, both should be writeable by any of the three valid users, tobydeemer, krista, or administrator.  

When you find you cannot write, are you writing to the share's parent directory, or to a sub-directory created by one of your Samba users?  If the latter, the directory mask of 0700 guarantees that only the owner will be able to do anything with this directory, and the create mask of 0600 guarantees that only the owner will be able to do anything with any files created in the share.  

Properly configuring communal access is a bit complicated.  (Forgive me if I'm repeating myself. :))  Since these two shares are ostensibly for communal use, start by creating a new group for Samba.  Then add all your Samba users to the group, and change the group on your shared directories to this group.  
```
sudo addgroup smbusers
sudo moduser -aG smbusers USERNAME   # Repeat for all three of your Samba users
sudo chgrp -R smbusers /PATH/TO/SHARED/DIRECTORY   # Repeat for all communal shares
```

In your smb.conf file, you should change the create mask to 660 and the directory mask to 770 to allow group access.  Then also add the option [font=courier]force group = smbusers[/font] to all communal share definitions.  

PS -- Without this force group option, new files and directories will default to the creator's primary group, rather than the communal smbusers group.

Cheers,

Eiríkr

Ok, so I'm late with my test and reply, but this last week was crazy at work; I'm sorry. Anyway, I did the mods you listed, and it worked great- but only on the Storage Drive. I think I am missing a detail about the file path or something with the Server_Share folder, since the permissions and now the group as well are the same. But here's my latest (relevant parts of it) modded smb.conf:

[HTML][global]
    ; General server settings
    netbios name = DeemerUbuntuServer
    server string = deemerubuntuserv
    workgroup = DEEMER
#    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = false

    passdb backend = tdbsam
    security = share
#    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

[Server_Share]
    path = /home/Server_Share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0775
#    force user = tobydeemer
#    force group = smbusers
    valid users = tobydeemer krista administrator

[StorageDrive]
    path = /media/disk
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0600
    directory mask = 0775
#    force user = tobydeemer krista administrator
#    force group = tobydeemer krista administrator
    valid users = tobydeemer krista administrator[/HTML]

But after the mods, both the XP station and the laptop can read, write, and modify files placed on Storage Drive by any of the three machines, so that's pretty much what I was going for. I still get "Access Denied" from the laptop (it can open it but not add files) and "Network Path not found" from XP (it can see it, but sends the error when I try to open the folder) when trying to get to the Server_Share.

So I'm still trying to hack at it. If you have any more ideas, that'd be awesome, but at this point you've probably burned more time than is necessary or desirable thinking about my silly little network. As always, thanks for the assist.

-toby

---

### Post by tobydeemer on 2008-04-16
Wait, nevermind. I figured it out. I inadvertently created the folder under owner:root, so... no one else could touch it. I changed it to administrator, ran a sudo chmod that matched what was in smb.conf, and it works now.

Umm... edit: only from the laptop. XP still can't get to Server_Share. So that hurts my brain. At least I know part of it was my bonehead mistake... (if not all of it.)

---

### Post by tobydeemer on 2008-04-16
Ok, another update. I've been messing with it, and now it's finally working.

I modified the permissions for Server_Share, and added the "force directory security mode" lines just to try it out, as in deb.early's last post. And that did the trick. Now XP can see, read, and write to Server_Share, as can the laptop.

So... thanks again everyone for your help.

---

