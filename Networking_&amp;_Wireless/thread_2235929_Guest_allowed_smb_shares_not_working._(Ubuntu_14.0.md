---
title: "Guest allowed smb shares not working. (Ubuntu 14.04 32 bit)"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by Luft on 2014-07-23
First let me apologize for the size of this post.  I want to give all of the information.

 My shares use to work until I re-installed Ubuntu and now only the shares on /dev/sda are working correctly.  Originally (when they all worked) I had purchased and installed the second drive after the original Ubuntu install so I had to create a mount point and tinker with the file system table.  I remember it was a bit of a pain and I don't remember exactly all the steps I took to get it done.  When I re-installed Ubuntu with both drives in place it automatically detected and setup the /dev/sdb drive but the mount point looks funny and I'm thinking that may be my problem.

Some of my smb shares that are suppose to allow guest logins without passwords are still requiring passwords.

I have a media server with two hard drives.  Ubuntu 14.04 is installed on a 2 TB drive (/dev/sda) and there is an additional 4 TB drive install (/dev/sdb).  Both are formated as ext4 file systems.  The sda drive is mounted on / and the sdb drive has a mount point of /media/<user>/0a508da2-2f26... (very long string) where <user> is the user name that I was logged on with when I installed Ubuntu.  The 4TB drive is setup as a GPT drive.

To set the shares I just used the default file window and right mouse clicked on the directories, then selected the Local Network Share tab.  I then checked the Share this folder checkbox and then the Guest access (for people without a user account) checkbox.  The first time I did this I was informed that additional software needed to be installed and was asked if I wanted to do so.  I selected yes and the software was installed.  I don't know if this is a bug but after the software installed the final window was left hanging with no buttons active.  I had to click the “x” on its window to close it.  (I think the software had finished installing at this point.)

My current fstab looks like:
```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=5b32eb0a-2844-4fa1-8943-72302ad9f58c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d1734d62-b565-4418-bbad-82d683345a49 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8debe038-2426-45c5-8545-ad5bbdd3701a none            swap    sw              0       0

```
My smb.conf file looks like:

  GNU nano 2.2.6                                                        File: smb.conf                                                                                                                       
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

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.

```

---

### Post by TheFu on 2014-07-23
First, it appears you the system isn't mounting the 4TB drive through the fstab.  I would fix that - so it is mounted where you want, not thought the automatic "media" mount that puts it under /media/ ...

google "ubuntu fstab" for a how-to.

Then, please post the output from **testparm**.

I used to share media files using NFS and CIFS like you, but about 8 months ago, I switched to using Plex Server. Wish I would have done that 2 yrs ago.  It is a great DLNA server and any DLNA client can access it - that means pretty much any cheap player or smart-TV or game console.  Just a thought.

---

### Post by Luft on 2014-07-23
Thanks TheFu, If sdb isn't being mounted though fstab it must be getting mounted some other way because I have access to it.  I think I will need to stop it from being mounted at all before I mess with mounting it a different way.  Any ideas on how it might be getting mounted now?

EDIT:  The output of the mount command is:

```

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/dev/sdb1 on /media/eric/0a508da2-2f26-4fee-a730-8382aae29f8c type ext4 (rw,nosuid,nodev,uhelper=udisks2)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=eric)

```

---

### Post by TheFu on 2014-07-23
**sudo umount /media/eric/0a508da2-2f26-4fee-a730-8382aae29f8c**
will unmount it.
Then you can add the correct line to the fstab and since it is already mounted, the automatic mount into /media will not happen. After you fix the fstab with the new mount, **sudo mount -a** will mount any unmounted things.

When posting output from commands, please, please, please use "code tags" so it is easy for me to read.

---

### Post by Luft on 2014-07-23
Thanks again.  

BTW, I don't know how to use code tags. Putting <code></code> didn't seem to work.

---

### Post by TheFu on 2014-07-23
see my signature above for a how-to link.

---

### Post by Luft on 2014-07-23
Thank you.  I have gone back and placed my outputs inside of code tags.  After modifying fstab my shares appear to work!  :)

The output from testparm is:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

---

### Post by TheFu on 2014-07-24
Well, I'm surprised that sharing works, since there isn't anything in the smb.conf to share anything. Whatever. If it is working, there isn't any argument.

For media, please take a look at plex - I think you'll be amazed.

---

