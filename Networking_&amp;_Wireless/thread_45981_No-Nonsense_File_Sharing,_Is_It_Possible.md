---
title: "No-Nonsense File Sharing, Is It Possible?"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2005-07-02
Hi all, I've been fighting with this for a few hours today. I am not able to do it, Samba is extremely hard for me. I have two Ubuntu Hoary PC's on the same network. I want both to be completely compatible with eachother network wise.

Here is what I want to do. I want to share the following folders:

/home/jeremy/Documents/Music
and
/home/jeremy/Documents/Shared

I want to do what I call "no nonsense file sharing" with these folders. This means no password, full read/write access for absolutely every user name, without a single password needing to be entered.

I also want to set up Firestarter Firewall on each PC and have it allow access as well.

How can I pull this off?

---

### Post by crashtest on 2005-07-02
[QUOTE=jlacroix]Hi all, I've been fighting with this for a few hours today. I am not able to do it, Samba is extremely hard for me. I have two Ubuntu Hoary PC's on the same network. I want both to be completely compatible with eachother network wise.

Here is what I want to do. I want to share the following folders:

/home/jeremy/Documents/Music
and
/home/jeremy/Documents/Shared

I want to do what I call "no nonsense file sharing" with these folders. This means no password, full read/write access for absolutely every user name, without a single password needing to be entered.

I also want to set up Firestarter Firewall on each PC and have it allow access as well.

How can I pull this off?[/QUOTE]

So you only want to share to another Linux machine, not to Windows, right?  No need for Samba in that case.  As a general concept, share the directories thru NFS on the one machine, and have the other machine mount these directories.  Directories mounted across NFS will appear like local directories on the client machine.  That's about as "no nonsense" as you can get.

---

### Post by jlacroix on 2005-07-02
How do I share as NFS? I don't have the NFS option under the shared folders icon. Also can I automount directories shared that way?

---

### Post by skirkpatrick on 2005-07-02
I honestly can't remember exactly how I got NFS working but it's not in the User Guide.  Go into Synaptic and make sure nfs-common and nfs-kernel-server is installed.  I think that you'll see NFS as an option in Shared Folders after that.

---

### Post by jlacroix on 2005-07-02
You're right, I do see an NFS option in both computers shared files icons now, so I can choose to share as NFS which is great.

Now, the question is how to access the directory on the other computer.

---

### Post by crashtest on 2005-07-02
[QUOTE=jlacroix]How do I share as NFS? I don't have the NFS option under the shared folders icon. Also can I automount directories shared that way?[/QUOTE]

The client machine can have the server's NFS shares mounted in /etc/fstab, so they will be automatically mounted on boot-up.

You will have to get your hands dirty a little in setting up NFS, but once you have it going it will be very solid.  You should probably start by reading the howto [here:](https://wiki.ubuntu.com//SettingUpNFSHowTo) 

There is also a FAQ [here.](http://www.ubuntulinux.org/support/documentation/faq/nfs-server) 

Once you've done a little reading, you can post specific questions here, and no doubt get some detailed help.

---

### Post by jlacroix on 2005-07-02
NFS seems to be harder than Samba. Everything in those howto's and others I've found on the net look like japanese to me.

Is there any way I can just erase my smb.conf file, and have you guys tell me what to put in it to do what I wanted with the shared folders, nothing more, nothing less?

---

### Post by skirkpatrick on 2005-07-05
Sorry for the lateness but here's a copy of my smb.conf file:
> 
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	load printers = yes
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
	obey pam restrictions = yes
	preserve case = yes
	socket options = TCP_NODELAY
	null passwords = yes
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = **PapaBear**
	server string = **Scott's Computer**
	printing = cups
	invalid users = root
	workgroup = **CLANKIRKPATRICK**
	printcap name = cups
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	short preserve case = yes
	max log size = 1000
	wins support = no
	security = share


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
	comment = All Printers
	path = /var/spool/samba
	guest ok = Yes
	writable = yes
	printable = Yes
	use client driver = yes
	disable spoolss = yes
	browseable = no
	Print command = lpr -r -P %p %s -U %u -o raw
	lprm command = /usr/bin/lprm -P %p %j




# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[Scott]
path = /home/scott
available = yes
browseable = yes
public = yes
writable = yes


The bold items will be specific for your machine.  This config shares my printer through Samba as well as my home directory.  You should be able to add shares through System->Administration->Shared Folders once this is setup.

Now to automount another machine's share, here's a copy of my /etc/fstab file:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//Warren/Public	/mnt/Public	smbfs	username=guest,password=guest,rw,user,guest,fmask=0777,dmask=077 7 0 0

In this example, I created a directory called /mnt/Public.  Fstab will mount the directory "Public" on machine "Warren" to this directory.

---

### Post by doclivingston on 2005-07-06
nautilus-share sounds like it does what you want, making it simple to share folders (fron nautilus). They have Ubuntu packages on the web site.

[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

---

### Post by jlacroix on 2005-07-06
Looks great, I'll check that out right now. :)

---

### Post by gil-galad on 2005-07-06
Have you tried the samba gui?  It is very straight forward.  

System-Administration-Shared Folders

---

### Post by arphe_el on 2005-11-29
Dear Crashtest,

I already read the [https://wiki.ubuntu.com//SettingUpNFSHowTo](https://wiki.ubuntu.com//SettingUpNFSHowTo) for setting up NFS actually here's my current set-up I would like to share 

pc1 with ip address 192.168.1.101 (server) 
pc2 with the ip 192.168.1.102 (client)
then save

here are my following config please tell me if it's right or wrong and what to do please let me know.

server pc1 192.168.1.101 

sudo gedit /etc/netgroup

add the following lines myclients (pc1,192.168.1.101,) (pc2,192.168.1.102,) 
then save

on /etc/hosts.allow

add the following lines 
portmap: 192.168.1.101, 192.168.1.102
mountd: 192.168.1.101, 192.168.1.102
nfsd: 192.168.1.101, 192.168.1.102
statd: 192.168.1.101, 192.168.1.102
lockd: 192.168.1.101, 192.168.1.102 
then save

Edit /etc/exports and add the shares
/home @192.168.1.102(rw,sync)


client pc2 

/etc/hosts.allow
portmap pc1 192.168.1.101

In /etc/fstab, add lines for shares such as:
pc1:home /home nfs rw,hard,intr 0 0

please let me know if i have the right config because since now i can't run the nfs after trying all the options.

Thank you and GODspeed!

---

### Post by Mathboy on 2005-12-05
I've used NFS and Samba. I find NFS a nuisance, and samba pretty easy but best for sharing to Windows machines. Haven't tried nautilus.

Things don't get much easier than sshfs though!

On the server (which stores the files):
just install ssh :)

On the client:
install sshfs

Then to share the /jeremy/music folder on "myserver" just go:
sshfs myserver:/jeremy/music /jeremy/music

That's it! :)

Check out [this]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") page for some more info.

---

### Post by floyd27 on 2006-01-04
cool, i think ill check that out too..

---

