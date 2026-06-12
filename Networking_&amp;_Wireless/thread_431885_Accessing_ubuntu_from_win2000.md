---
title: "Accessing ubuntu from win2000"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-05-03
I have added a ubuntu and samba user who is on a win2000 box. But I cannot access the share from her computer via network neighborhood.

I installed NetBios on the win box. Am I missing something else?

I typed \\merlin_smb_server\ , which is specified in smb.conf, in the add new network place dialog box in network neighborhood on the win machine, but got an error message to the effect that it could not be found.  It was also not visible in workgroup in network neighborhood.

Here are the relevant sections of smb.conf:

> 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = workgroup
   netbios name = merlin_smb_server

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

#### Networking ####


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


# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY


#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
   comment = Home Directories
   browseable = yes
   writable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700



# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)

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




[xldocs]
path = /media/sda1/Docs/xldocs
available = yes
browsable = yes
public = yes
writable = yes

[diana]
path = /home/diana
available = yes
browsable = yes
public = yes
writable = yes




Many thanks...

-merlin

---

### Post by garlik42 on 2007-05-03
```
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = workgroup
netbios name = merlin_smb_server
```

I assume your workgroup on the Win2K machine is workgroup ? If it's something else, then fix the workgroup line. IE if your win2k box is in the HEINUSHEYENA workgroup,
workgroup = HEINUSHEYENA.

Netbios is unneeded, as tcpip will be used.

After changing this workgroup line, you will need to restart samba (or you could reboot)

---

### Post by merlinus on 2007-05-03
It is indeed workgroup.

If I do not use Netbios on the win box, then what should be typed into the add new network place dialog box?

Thanks.

-merlin

---

### Post by garlik42 on 2007-05-03
Try the ip address of the ubuntu box.
I have a similar setup, at work and it just works, (all windows traffic at work is over tcp/ip)
If that doesn't help you, I'm not sure what the problem is.

---

### Post by merlinus on 2007-05-03
Just so I am certain --

how can I find the IP address of my ubuntu box?

Thank!

-merlin

BTW, this is as mystifying as why ubuntu can't find my cd burner!

---

### Post by garlik42 on 2007-05-04
I am sure there is an easier way to tell, with the GUI, but I have been a command line user of linux for 14 years, and just started using gnome. Maybe one of the GUI experts can give you a GUI way ...

Open a terminal prompt (command prompt) On my system it's under the applications menu "Accessories Terminal"

Type "ifconfig" hit return
You will get all kinds of information, depending on howmany network cards etc.
Look for the lines that start "inet addr"
There will be one like 127.0.0.1, and at least one other with 4 numbers, they may start with 192.168.

---

### Post by merlinus on 2007-05-04
Thanks.  I tried all of the IP addresses that came up, but windoze could not connect.

-merlin

---

### Post by Steve H on 2007-05-15
Try adding ALL 4 IP address for your Ubuntu box to the WINS address on your Windows box. It will be somewhere like Netwroks connections --> properties --> Highlight TCP/IP --> advanced...then there is a WINS tab. Add each of the IP Addresses for Ubuntu, restart the connection after you have saved the config. You should now see the Ubuntu box in your workgroup.

Hope that helps.

:)

---

