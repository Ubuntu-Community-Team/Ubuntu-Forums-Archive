---
title: "Network setup issues in xp"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by rcane84 on 2007-10-20
Hello everyone,

I have Ubuntu installed on an older P3 desktop and Windows XP Pro on a P4 Laptop. I have been trying to set up a network and have had some success but it is not all the way there. From the Ubuntu desktop I am able to see the shared files on my Windows computer and am able to transfer them over no problem. The thing is I can't do it the other way. When I try to access what should be my Ubuntu shared folder (all of \home) I am unable to do so from XP machine. I have followed the following setup advice for samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I set samba and decided to go with a fixed dhcp lease. Here is the code (sudo gedit /etc/samba/smb.conf) I hopefully configured right.

[global]
; General server settings
netbios name = RICHARD


workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE
SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true

username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = no

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes


; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
valid users = %S
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
server string = richard
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
path = /home
browseable = yes
read only = no
guest ok = no
create mask = 0644

directory mask = 0755
force user = RICHARD
force group = RICHARD
available = yes
public = yes
writable = no

[samba]
path = /home/samba
available = yes
browseable = no
public = yes
writable = yes


I have tried disconnecting both the windows firewall and the Telus Internet Security firewall (internet access provider security) and it hasn’t made any difference. I seem to be doing fine until I get to this part:

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

I followed this I get a pop up window saying “Attempting to contact \\192.168.0.101\MyFiles...” then I have to enter my username and password and the same window asking me to enter my username and passoword pops up over and over. I’ve tried typing “Richard” – the computer’s name instead of the ip address with no luck. I’ve also tried varying the “MyFiles part” with \home with no luck. I’m also running AVG free edition for linux does that make a difference?

I’ve made sure that \home is a shared folder in Ubuntu under system>administration>shared folders. Please let me know if any of you have some suggestions I might try. I think I may have also done something like “ chmod 0770 \home” in the terminal. I probably shouldn’t have though I don’t know if it wrecked it. I can’t remember why I did it. It was super early.

Thanks for the help!

Richard

---

### Post by mpierce on 2007-10-20
When you try to connect from Windows to your Linux box, are you using the same name and password from Windows that you use in Linux, e.g., Linux username "roy", password "1234". You have to use the same username and password to log onto the Linux box. 

PS - I didn't go thru your smb.conf file line for line but if you need it, I post mine.

---

### Post by rcane84 on 2007-10-20
Hi,

Yep, my passwords and usernames are the same in both.  That would be great if you could post your code.

Thanks,
Richard

---

### Post by mpierce on 2007-10-20
My file below (I'm sharing 3 partitions and I've cut out everything not needed. I use cups to print and administer so printing not needed):

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

 What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = host lmhosts wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 192.168.1.0/24

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

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

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

########## Printing ##########

############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
   domain master = auto

#======================= Share Definitions =======================

#Home directory
[my name]
    comment = Home Directory
    path = /home/mpierce
    public = yes
    writeable = yes
    available = yes
    browseable = no
    guest only = no
    writable = yes
    preexec close = no
    root preexec close = no
    inherit permissions = no
    hide dot files = no

#Archived files
[archive]
    comment = DVD, MP3 and archived files
    path = /archive
    browseable = yes
    public = yes
    guest ok = yes
    writable = yes

#Storage space for hard drive backups
[backups]
    comment = Backup & image storage partition
    path = /backups
    browseable = yes
    public = yes
    guest ok = yes
    writable = yes

---

