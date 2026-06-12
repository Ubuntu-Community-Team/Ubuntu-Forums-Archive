---
title: "Struggling with SSH to mount a remote drive"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by zcacogp on 2009-06-09
Chaps, 

I'm using the instructions here: 

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

... to try and allow me to mount a remote drive on my computer. By remote I mean on a different computer, although on the same network. 

The situation is thus: 

- I am working on my desktop computer. IP = 192.168.10.6
- I have a laptop computer, IP = 192.168.10.7
- These are connected via my broadband router, both on network cables. 

- The laptop has two drives I would like to share: /media/Ieuan and /media/Horatio

- I have created the following locations to try and share them into on the desktop machine: /x61slappie/Ieuan and /x61slappie/Horatio

- I *think* I have installed SSH Server on the laptop and SSH client on the desktop. I did something involving public and private keys on both machines, but that was a week or so ago and I can't remember what I did (great start, huh?) 

- I am ogp on both machines


If I use this command in the terminal on the desktop: 

```
sshfs -o idmap=user ogp@192.168.10.7:/media/Horatio ~/x61slappie/Horatio

```

.... then Horatio maps nicely. The same happens for Ieuan if I do this: 

```
sshfs -o idmap=user ogp@192.168.10.7:/media/Ieuan ~/x61slappie/Ieuan
```

BUT, if I put these three lines into /etc/fstab on the desktop machine

```
# Entry for x61slappie
sshfs#ogp@192.168.10.7:/media/Horatio /home/ogp/x61slappie/Horatio fuse defaults,idmap=user 0 0
sshfs#ogp@192.168.10.7:/media/Ieuan /home/ogp/x61slappie/Ieuan fuse defaults,idmap=user 0 0
```

... the drives **don't** re-mount when I reboot the desktop. Why not - what have I done wrong? 

Thinking about this, if I had these lines in fstab, the desktop machine would look for the drives on the laptop every time I booted it up, even if the laptop isn't around or turned on. So I thought about putting the code on the top panel as a button, to allow me to mount the laptop drives on the desktop at the touch of a button instead. 

So I did the following: 

Right click on top panel > Add to panel > Custom Application Launcher 

Type: Application
Name: Mount Horatio
Command: sshfs -o idmap=user ogp@192.168.10.7:/media/Horatio ~/x61slappie/Horatio
Comment: Mounts the Horatio drive from the X61s Laptop

But this doesn't work either. Why not - what have I done wrong? 

**More advanced questions**

There are other things I am also struggling with on this topic: All the instructions above work on the basis that the laptop is taking the IP address 192.168.10.7, but I am not sure that this is always the case: if I use another machine on the network that may take 192.168.10.7, and thus the laptop would take 192.168.10.8, and then the whole thing would fail to connect. Is it possible to identify the laptop (and indeed the desktop) on the network by name rather than IP address? (The laptop machine name is ogp-x61s, although trying the above commands with 'ogp-x61s' instead of '192.168.10.7' means none of them work. Also, I am not sure why my username is part of the machine name - the command line prompt on the laptop is ogp@ogp-x61s:). 

Also, Ieuan and Horatio (drives on the laptop) are intended to be mirrors of two drives on the desktop: Ianthe and Helena (girls names - names on the laptop are boys names, to tell them apart.) The idea of this is that the laptop can be taken away from the desktop machine and used at a remote location. When I bring the laptop back to the desktop, the drives can be syncronised (Ianthe with Ieuan, Helena with Horatio). With both machines running XP, I used a Microsoft Powertoy called "Synctoy" which did this automatically and very well. Presuming I can reliably access Horatio and Ieuan from desktop, is there a Ubuntu equivalent for Synctoy to do this? 

Last one: This is all presuming that I want to access the laptop drives from the desktop machine, hence I have SSH server running on the laptop and SSH client running on the desktop. Is it possible to have both the client AND the server running on both machines, thus allowing two-way access? 


What I've described above (in the whole of this post) is pretty much the set-up I had on XP. Setting it all up on XP was a very easy job, mainly done with the mouse, taking not much more than five minutes. I have now spent over an hour trying to achieve the same thing with Ubuntu, and struggle to believe that it is so much harder. I thought that Ubuntu was meant to be superior when it came to networking things? Have I missed something, or am I being thick? (I am happy to accept the latter.) 

Thanks, in advance, for any help anyone can offer. 


Oli.

---

### Post by Celauran on 2009-06-09
The first thing I'd recommend is to assign each machine a static IP.

/etc/network/interfaces:
```

auto eth0
eth0 inet static
    address 192.168.0.100
    gateway 192.168.0.1
    netmask 255.255.255.0
```

Though it won't be necessary, once this is done you can also map their names to their IPs via /etc/hosts.

What I think may be happening with the fstab entries is that the drives are trying to mount before the DHCP server has assigned an address, so there is not yet any connection to the network.

---

### Post by zcacogp on 2009-06-09
Celauran, 

Thanks. 

I don't fully understand that command you gave, but will try it. 

Before I do, how will it affect the way the laptop works on other networks? As in, it has a network cable and a wireless card, and at home I sometimes use it wirelessly. Is this relevant? 

Also, I take the laptop to a client site on a regular basis, and plug it into their network there (always on a network cable; never wirelessly.) I use a different proxy server while I am there, and have a different location set up for the client site in System > Network > Network Proxy. 

If I put the code you gave me into the /etc/network/interfaces file for the laptop, would this screw up the connection at the client site? 

Thanks for your help. 


Oli.

---

### Post by Celauran on 2009-06-09
I had overlooked that the machine in question was a laptop, so I must retract my previous recommendation. You'll need to leave it as DHCP. What you could do as an alternative, is to have your router assign specific IPs based on MAC address, so whenever you're at home, 192.168.0.100 (or whatever) will be reserved for, say, your laptop's eth0. Still only a tiny bit of a solution to your problem, I'm afraid.

---

### Post by zcacogp on 2009-06-09
Celauran, 

Thanks for your second answer. 

OK, this raises two more questions. How do I assign an IP address to a MAC address in my router, and how does this help me? I guess it means that I know I will always find my laptop at 192.168.10.100, thus I can set up the SSH commands accordingly. Can I then assign a name to the laptop rather than working on IP addresses? If so, how (and where) do I do that? 

(The question about the association of MAC address with IP address I guess I'll find in the router documentation. Or with a Google search. I appreciate that it's not one that should be asked here!) 

Thanks again for your help. 

Anyone else going to have a go at the other questions? ;)


Oli.

---

### Post by Celauran on 2009-06-09
> **zcacogp said:**
> I guess it means that I know I will always find my laptop at 192.168.10.100, thus I can set up the SSH commands accordingly.
Precisely.

> **zcacogp said:**
> Can I then assign a name to the laptop rather than working on IP addresses? If so, how (and where) do I do that?
You'd do that in your desktop's /etc/hosts file.

```
192.168.10.6    laptop-name
```

Your desktop will then know to resolve laptop-name to 192.168.10.6

---

### Post by Celauran on 2009-06-09
Have you looked at [this](http://jldugger.livejournal.com/29131.html)?

---

### Post by zcacogp on 2009-06-09
Celauran, 

Thanks again. I have assigned a static IP to both the wireless and wired connection for the lappie, but it had to be a different IP address for each. Does this mean I need to set the ssh connection twice - once for each IP address? 

Your suggestion (modifying /etc/hosts on the desktop) will therefore mean that the desktop always 'sees' the laptop as whatever name I give it, but doesn't mean the name of the machine is set *per se* - is this correct? Other machines on the network would still see it as 192.168.10.7 (or whatever). Or can I set both IP addresses (192.168.10.7 for the wired connection, 192.168.10.8 for the wireless) to resolve to the same name on /etc/hosts on the desktop? (This would clearly answer the question at the end of the paragraph above.)

No, I hadn't seen the link you sent. Thanks for it. That seems like a LOT of work to make something happen that is enormously easy in XP. Is there no easier way to do it? (That's not addressed to you Celuran - it's an open question!) 

Thanks again for your help. 


Oli.

---

### Post by bodhi.zazen on 2009-06-09
Not sure exactly what you are asking , but I shall try.

The computer should be seen on your network by it's host name.

The entry you put in /etc/hosts on the ssh client does not affect the hostname and so should not affect how either computer is seen on your network.

In terms of "easy" , no it is not easy to mount a file system on windows over sshfs, it is far easier to do that on Linux.

If you are looking for an easy way to share files, take a look at samba, it is the linux version of shared folders and works out of the box for most people.

You may or may not have problems with samba over wireless depending on your router.

---

### Post by Miljet on 2009-06-09
When I set up SSH, I didn't fool with static IP addresses (or any IP addresses for that matter).

I used the tutorial here:
[http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh](http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh)

The first time I set it up, it took about an hour mainly because I was learning as I went. The next two times I set it up it took less than ten minutes each.

The tutorial uses rsync to sync the files between the two computers. It has the advantage of only copying files that have changed since the last backup.

Although the tutorial sets up a cron job, I elected not to do that. I just wrote a script file that I can call whenever I feel a need for it.

---

### Post by zcacogp on 2009-06-14
bodi.zazen, Miljet, 

Thanks for your two answers. 

First question: bodi.zazen, you say "The computer should be seen on your network by it's host name.The entry you put in /etc/hosts on the ssh client does not affect the hostname and so should not affect how either computer is seen on your network." What is my computer's host name, and how do I ensure that it is known by this name? This is something that I haven't been able to find out, despite searching this forum for it repeatedly. 

I have now tried Samba (and have been trying it for the last two-and-a-half hours) from the link you gave me and it simply isn't working. I *think* I have the server set up right, but when I try to connect from the client it says "Failed to retrieve share list from server." I simply do not understand enough about what I am trying to do to understand what is going wrong. I can ping from one machine to the other fine. But I cannot see any of the shared folders (they are NTFS partitions, mounted on the server, if that is relevant) from the client machine. I don't know whether my earlier attempts to use SSH have scuppered things or not - as I said, I don't know enough to understand what is and isn't right, and I don't know how to remove the SSH stuff from the machines (or even if I need to.) 

Miljet, I have seen the link you posted before. I guess that's the next thing to try. 

I will confess to being frustrated with Ubuntu. I am trying it because so many people seem to rave about it. Thus far, I like the eyecandy but every single thing I have tried to do on it has been a battle. I reckon I have spent well over 100 hours playing with it on various machines over the last month or so and have nothing to show for it - well, three machines with Ubuntu installed, which exhibit less functionality than the XP installs which are also available on dual-boot. 

OK, rant over. If anyone can help with the problem with Samba, that would be great. I seem to have made the two folders on the server 'shared' (they have the little 'shared hand' showing on the icon), but they are not available on the client.  I had to insert the line "usershare owner only = false" into smb.conf on the server to enable the two folders to be shared, because I didn't own them. I have Samba and smbfs installed on the server and client respectively.


Oli.

---

### Post by bodhi.zazen on 2009-06-14
You set your hostname when you installed Ubuntu.

If you do not recall, open a terminal and enter

```
hostname
```

or simply open /etc/hosts with any editor.

In terms of mounting a remote share we need more information. You have named 2 protocols, sshfs and samba.

Tell us please, what is the server (what OS) and what is the client ?
How did you configure the server ?
What how to did you use?
Do you have a firewall on client or server ?

Hard to guess when the only information you give us is that it is not working.

---

### Post by zcacogp on 2009-06-16
Bodhi.zazen, 

Thanks for your answer and help. It's appreciated. 

Youre right - more information is necessary. Apologies for being short and grumpy in my last post, I'll try and provide more helpful symptoms here. 

The server is a desktop machine, running Ubuntu 9.04 (fully updated). Using this thread here: 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

... I installed Samba on the desktop (server) machine, using ```
sudo aptitude install samba
``` (out of interest, why is this 'aptitude' and not the usual 'apt-get'?) 

I also used this: ```
sudo aptitude install smbfs
``` to put the client software on the second machine (a laptop, also running 9.04. The two are connected using a Netgear ADSL wireless router, but both are plugged in using network cables - neither are on wireless yet.) 

It sounds like the smb.conf file is critical, and I used the default ones which were installed, but changed the workgroup to 'dgcnet'. smb.conf for the desktop (server) is like this: 

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = dgcnet

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

   usershare owner only = false

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

``` ... and I'll log on from the laptop immediately after posting this to give the smb.conf file from that (as I cannot access one machine from the other I cannot easily put both in the same post, if you see what I mean!) 

The laptop (client) is at 192.168.10.21 (fixed IP allocated to the laptop's mac address by the router), the desktop at 192.168.10.2. I can ping each machine from the other, and there is not any firewall installed on the router or either machine (that I am aware of - how would I test for this?) 

Typing "hostname" on the desktop gives ogp-desktop, and doing the same on the laptop gives ogp-x61s (the same as appear at the prompts in the respective terminals). However I thought that this was the machine name, and not the name that the machine was going to appear as on the network - I am (again) confused. 

The two folders on the desktop (server) that I am trying to share are called "Ianthe" and "Helena". I have opened them up in Nautilus, right-clicked them and marked them as "To be shared". This produced an error message, which told me to add the line ```
usershare owner only = false
``` to the smb.conf file on the desktop, which I did. This then allowed me to share these folders, which now appear with a little "shared" hand when displayed in Nautilus (similar to in XP.) 

When I try to access the drives from the laptop (client), I can see "Windows Network" under "Network" in Nautilus, but when I click on it I get the error message ```
"Unable to mount location. Failed to retrieve share list from server".
``` Which would suggest (to me, so quite probably wrongly) that the server is for some reason unaccessible, despite the pinging working OK. 

For what it's worth, both Ianthe and Helena are NTFS drives which are used in XP (the machine is dual-boot), and they are set to mount on start-up. Is this relevant? 

I simply don't know enough to proceed from here. All help welcomed. Thanks. 


Oli.

---

### Post by zcacogp on 2009-06-16
This is the smb.conf file from the laptop. 

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = dgcnet

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

As I said, I'm stuck, all help welcomed. 

Thanks in advance. 


Oli.

---

### Post by bodhi.zazen on 2009-06-16
See this guide : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

==========

Graphical configuration.

You do understand you can do this from the gui ? In a few very simple steps ?

Do not share your home folder, rather a directory inside home, say ~/share

right click the directory and share it.

[https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration)

There are several ways to connect to the share form the client.

[https://help.ubuntu.com/community/SettingUpSamba#Connect%20to%20a%20samba%20server](https://help.ubuntu.com/community/SettingUpSamba#Connect%20to%20a%20samba%20server)

Personally I manually mount my samba shares (keeps 'em nice and private).

====================

manual configuration.

You are welcome to manually configure samba if you wish, follow the manual configuration.

[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration)

1. First, you do not need the samba server on both client and server.

2. Second, on the server you need to manually add a samba user

```
sudo smbpasswd -a samba_user
```

give a password and use that samba_user and password to connect.

3. Last you need to actually add a share. In you configuration file all your shares are commented out 9lines that staart with a # or a ; are comments).

See the samba page for examples.

Again, this section will walk you through the config file.

It may be easier to use the graphical tool ;)

---

### Post by zcacogp on 2009-06-17
Bodhi.zazen, 

Thanks for your reply. 

Yes, the page you linked to is the one that I have been working from, as I mentioned in my previous post. I have been trying to use the graphical set-up (GUI), as described on that page, and am not getting anywhere. 

As said before, I have (I think) set up both ends of the connection, but when I click on "Windows Network" on the client, I get the error message ```
"Unable to mount location. Failed to retrieve share list from server".
```

As I said, the locations to be shared are /media/Ianthe and /media/Helena. Both of which are NTFS partitions on the hard disk on the server. 

You raise two new points which are not on the 'Ho To' page, but your post suggests that they are only relevant to the Manual Configuration; the setting up of a Samba User on the server, and the fact that the shares are commented out in the configuration file I posted. Do I need to concern myself with these if I am using the GUI configuration? 

If not, what else am I doing wrong? 


Oli.

---

### Post by zcacogp on 2009-06-17
Bodhi.zazen (and anyone else!) 

OK. Progress. And it's good. 

Thinking back, I did install a firewall on my desktop (server) PC when I first put Ubuntu on it. It was called firestarter. So I removed it, and - hey presto! - things started to work with samba! 

It's not quite all the way there yet tho'. If I share a drive from the server, and in the "Sharing Options" box click "Allow guest access", I can access the shares fine from the client (laptop.) If however I don't tick the "Allow Guest Access" box, I am presented with a screen on the client asking me to enter a password. More accurately, it asks for the following, with the answers in brackets already completed: 

Username: ogp
Domain: DGCNET
Password: <blank>

The username is the one that I use on both the laptop (client) and the server (desktop), and I use the same password on both machines, but if I put this into the "Password" box it comes back and asks the same question again (I presume it is therefore wrong.) 

I notice that this is referred to on the "How-To" page, thus: 
```

On the Ubuntu client using the menu at the top, go to "Places" -> "Network". You will see an icon "Windows network" and should be able to browse to your shared folder. You will be asked for a password, leave it blank. Click the "Connect button.
```

However, if I do as it suggests and leave the password blank then it also asks again. 

I am suspecting that it is looking for a samba username and password, but don't see how I put one in on the desktop (server). The idea of some kind of authentication is appealing (or, to put it another way, the idea of folders being freely available for all to see is NOT appealing.) 

I'm currently searching the forums to see where the samba username should be set up with with no joy - any ideas? 

Thanks again for your help. I'm feeling a complete fool about the firestarter problem. 


Oli.

---

### Post by bodhi.zazen on 2009-06-17
Take it one step at at time.

Start on server. Is there a firewall on the server ? If so shut it down or configure it to allow samba ports.

Next you need to make a share. If you do this from the gui it will be automatic. If you do it by manually configuring the samba file, you will need to manually add a samba user and password.

If you manually edit the samba config file and manually add a samba user and password you will then need to manually re-start samba.

Once you have done that go to the client.

enter :

```
sudo mkdir /media/samba
sudo mount -t cifs //server_ip_address/share_name /media/samba -o user=samba_user
```

You will need to change "server_ip_address_" to your actual ip address
"share_name" to the name you assigned the share
and "samba_user" to the samba user name you assigned. If you used a gui it is the log in name you use on the server.

Post any error messages you are getting (the error messages from the gui tool are not as helpful as from the command line).

Once that is working we can make adjustments on how the shares are working (ie browsable, rw, etc).

Samba is not really *that* hard. Start following the directions on the samba page and tell us what you do not understand.

---

### Post by zcacogp on 2009-06-17
Bodhi.zazen, 

Again, thanks for replying. 

I'm there. See my last post. I'm in, and it is working. 

The current snag is the samba user issue. It seems that, despite my using the GUI method of setting the share up, it hasn't set up the required samba user. 

I can do (and now have done) this manually, using instructions from here: 

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

To be precise, I typed in this: ```
sudo smbpasswd -a ogp
``` (my login being ogp on both computers), and then put in a password (a different one to the one I use to login to the machines.) 

I then added this: ```
ogp='ogp'
``` ... to the file /etc/samba/smbusers. 

Then, after having turned off 'guest access' to the drives on the server, I can still access the drives on the client by putting in the password. 

So ... all is well. Thanks for your input. 

Yes, I can now see that Samba is not that hard. However, I was foxed by it not working (as the firewall was in place). Knowing that it wasn't *meant* to be hard, and yet not being able to make it work, was very frustrating. 

Thanks for your help in talking me through it. 

(I now need to know how to mount the shared folders at a different place in the filesystem to enable them to be read by amarok, and how to synchronise local folders with remotely mounted folders ... but those sound like topics for different threads!) 

Thanks again. 


Oli.

---

### Post by SoftwareExplorer on 2009-06-17
I also occasionally have problems with samba saying failed to receive share list from the server. When this happens, the computer I am using is the only computer it sees. I have found that restarting almost always makes it work. Not sure why, but that's what works for me.

---

### Post by bodhi.zazen on 2009-06-17
> **zcacogp said:**
> I now need to know how to mount the shared folders at a different place in the filesystem to enable them to be read by amarok, and how to synchronise local folders with remotely mounted folders ... but those sound like topics for different threads!

Thanks again. 


Oli.

Well, my intent on say it it is not that hard was to encourage you, sorry if it cam acorss any other way.

Now that it is working it is easier to fine tune, as you can see.

For sync you can look at a variety of tools, such as rsync.

samba permissions are set in two ways, first on server, second at mount, in the options.

mount -t cifs //server/share /media/samba -o username=username,uid=user,gid=group.

See fstab ana mount for information.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

