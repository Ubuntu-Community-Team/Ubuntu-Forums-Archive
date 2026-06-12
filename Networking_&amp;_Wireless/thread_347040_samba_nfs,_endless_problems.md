---
title: "samba nfs, endless problems"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-01-26
i have been having problems with samba for a long time, i have my home directory with several samba shares mounted through fstab. they often work but sometimes they stop working while accessing them not and even a sudo mount -a doesnt resolve the problem, i then get:
> Could not resolve mount point /home/matt/_matt
Could not resolve mount point /home/matt/My_Documents
Could not resolve mount point /home/matt/c
Could not resolve mount point /home/matt/r
Could not resolve mount point /home/matt/web


this problem just happens randomly and have to restart to sort it (temporarily). i have asked for support on the forum before but nobody seems to be able to help.

now today i have tried to install NFS on my server. i followed [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) but when i come to mounting on the client pc i get this:
> 
root@LINUX2:/mnt# mount 192.168.1.1:/data/storage/SHARE/_matt /media/_matt
mount: 192.168.1.1:/data/storage/SHARE/_matt failed, reason given by server: Permission denied

i have searched google and nothing seems to work. im sure i havnt missed anything out.

i need something working for me to access files from my ubuntu server from my ubuntu desktop as this is getting very annoying when i have to close everything down.

Matt

---

### Post by matt91 on 2007-01-27
anybody?

---

### Post by neill on 2007-01-27
what version of samba ?

where physically are the shares hosted ?

do you have a ubuntu server and desktop, or something different ?



also can you post your fstab and smb.conf please

neill

---

### Post by matt91 on 2007-01-27
i have an ubuntu server 6.10 with the latest version of samba installed and ubuntu 6.10 desktop with the latest version of samba and smbfs installed. on my server my smb.conf is:
> 
[global]
    ; General server settings
    netbios name = SERVER
    server string =
    workgroup = MSHOME
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
[netlogon]
    path = /var/lib/samba/netlogon
    admin users = Administrator
    valid users = %U
    read only = no

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
    read only = no
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

[_matt]
    path = /data/storage/SHARE/_matt
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root
[My_Documents]
    path = /data/storage/SHARE/_matt/MATT/My_Documents
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root
[r]
    path = /data/storage
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root
[web]
    path = /data/storage/SHARE/web
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root
[_home]
    path = /data/storage/SHARE/_home
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root
[c]
    path = /
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = root
    force group = root


my fstab on my desktop is like this for the shares:
> 
//192.168.1.1/_matt    /home/matt/_matt smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//192.168.1.1/My_Documents    /home/matt/My_Documents smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//192.168.1.1/c    /home/matt/c smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//192.168.1.1/r    /home/matt/r smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//192.168.1.1/web    /home/matt/web smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0


the shares work perfectly until they just stop working, at the same time on my windows pc can connect to the shares.

---

### Post by neill on 2007-01-27
that all seems perfectly OK to me - and it clearly is if you're getting intermittent functionality

have you tried it with the socket options commented out ?

also if you're not running a PDC, try commenting out all the netlogon stuff

---

### Post by matt91 on 2007-01-27
ok, i have tried that, dont know if it works but it hasnt stopped yet. thank you for your help.

---

### Post by neill on 2007-01-27
let me know how it goes please

ta

---

### Post by jongkind on 2007-01-27
I prefer NFS. This document was of great help for me:
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

With respect to samba: this works for me (I never made smbfs mount points in fstab, though):
[http://www.ubuntuforums.org/showthread.php?t=76647]("http://www.ubuntuforums.org/showthread.php?t=76647")

---

### Post by neill on 2007-01-29
matt91

still working ???

---

### Post by zamphier on 2007-02-12
I get the exact same problem, also intermittently. My other linux boxes are set up the same and do not pose any problems. My windows clients also work correctly. I read an old thread about Dapper that said something about the shares being mounted too early in the boot sequence (but I cant find the post again). 
I'm thinking about scripting the mounts manually, because it does work to mount them manually if I don't first try to mount them in fstab.
:confused:

---

### Post by Rootcomputing on 2007-02-12
I too have the same problem as Matt. I posted on the forum before and it was moved to the newbies talk, but I never managed to get it answered. Like Matt I have everything configured correctloy, portmaps, exports, host table, nfs running, client on client and server on server. All permissions are allowed on every file, yet when I try to mount my storage folder I get the permission denied. I am still trying to work it out. I have searched all over and have came up with nothing. Don't let this die guys, I want to stream my music over the network!@

---

### Post by rushadrenaline on 2008-01-18
Hey matt91,,
The solution to "permission denied" problem and "cant get address" problem  is here::::

Cause in the /etc/hosts file on the client side, the client needs to know the corresponding ip of the server along with its hostname :
for instance my /etc/hosts looks like this :::

127.0.0.1                  rusha     localhost       ------>>>>> my pc's (client) hostname.Need not change this
192.168.4.25           fedora    ------->>>>       NFS server's ip and hostname 

You can change the hostname of your NFS server by running this command on the console ::
$] hostname "enter the new name here"
for instance
$] hostname nfs-fedora
Thats it.
While rest of the procedure is same as mentioned in all the how to's of nfs.

---

