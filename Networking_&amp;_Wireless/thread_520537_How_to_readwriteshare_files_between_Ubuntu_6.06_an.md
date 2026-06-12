---
title: "How to read/write/share files between Ubuntu 6.06 and XP-Pro"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by earthling30 on 2007-08-08
Hello all,
I'm very new to Ubuntu and it seems to be very cool. I've been at WinLOOSER XP (NTFS file system) user for a while and I have networked all my Xp machines together to share/read/write files. I'm trying to get my Ubuntu machine to be able to do the same.

I done the following on my Ubuntu Machine to prepare it for this task:
1. Installed/Formatted/Mounted a 2nd hard drive with fat32 file system called dev/hdb1= /storage.

2. I've done some research from the following threads only to confuse me more.
[http://ubuntuforums.org/showthread.php?t=112051](http://ubuntuforums.org/showthread.php?t=112051)


[http://ubuntuforums.org/showthread.php?t=113652](http://ubuntuforums.org/showthread.php?t=113652)


[http://ubuntuguide.org/wiki/Ubuntu:Feisty#automountfat](http://ubuntuguide.org/wiki/Ubuntu:Feisty#automountfat)

3. My windows machines now connect to my Ubuntu machine and can only read the files. I would like to be able to add/copy/cut/paste/delete files. ](*,)

4. My Ubuntu machine can see my Windows machines on my workgroup but I can't browse any files. When I try to browse computer I get the Error "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: main"." I would like to be able to add/copy/cut/paste/delete files from this machine as well. ](*,)


Here is my smb.conf
[global]
    ; General server settings
    netbios name = Linux
    
    workgroup = Pwdn
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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


[Linux]
path = /storage
available = yes
browseable = yes
public = yes
writable = yes

Sorry for the long post but I would like to try correct this issue without having to drop my new TOY! :lolflag:

---

### Post by dfreer on 2007-08-08
Well, you shouldn't need a FAT32 partition just to share files, BTW. You can share files from any filesystem type that the host machine can fully access. 

But have you created your smbuser/password yet? It should ask you to login when you are using "security = user" on the Ubuntu machine smb.conf.

Here's a good guide for setting up some simple samba shares:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

EDIT: out of the three links you posted, the bottom two deal with sharing files from separate partitions in a dual-boot environment, not across the network using Samba. This is probably causing your confusion ;)

---

### Post by earthling30 on 2007-08-08
Thanks for the reply. I'll give it a try and keep you posted.

---

### Post by earthling30 on 2007-08-08
I'm not sure what I'm doing wrong. In the Konsole I keep getting an error!

"pd@pd-desktop:~$ sudo smbpasswd -a system_username
Password: *******
New SMB password: ****
Retype new SMB password: ****
Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_username
pd@pd-desktop:~$
"

Has anyone seen this before? ](*,)

---

### Post by earthling30 on 2007-08-08
I've made some progress. I had to do some research about the samba users on how to add. I was doing correct all along but just missed one thing. For all of you that are having the same problems as I and you like me that need the obviousl pointed out this is what you do:

> sudo smbpasswd -a "**your custom user name goes here without the quotes**"  **DUH!!**

I found this out on [http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/")

We'll see how the rest of it goes

---

### Post by dfreer on 2007-08-10
Yep, I forgot to say something about that. I should really edit that wiki, so that the command is a bit more clear. I didn't realize that the SMB username had to have a matching username in the system, that should also be added to the wiki (good catch!).

Hope you got it working!

---

