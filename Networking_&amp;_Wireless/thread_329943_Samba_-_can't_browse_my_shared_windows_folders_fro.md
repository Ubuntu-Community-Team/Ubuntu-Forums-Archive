---
title: "Samba - can't browse my shared windows folders from xubuntu"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by theadventuresofanidealist on 2007-01-02
[COLOR="Black"][COLOR="Black"][COLOR="Black"]I'm running xubuntu on my sony vaio p3 128mb, connected through a dsl router through ethernet and sharing files with a windows xp desktop, using samba. 
i can easily acess my files from windows, but not from xubuntu.
im using xffm samba to browse the network.

here is my error message from xffm:

"Looking for master browsers...
querying __MSBROWSE__ on xxx.xxx.x.xxx
xxx.xxx.x.xx __MSBROWSE__<01>
IP>xxx.xxx.x.xx
XFSAMBA> nmblookup -A xxx.xxx.x.xx
Looking up status of xxx.xxx.x.xx
	DESKTOP   <00> -         B <ACTIVE> 
	MSHOME          <00> - <GROUP> B <ACTIVE> 
	DESKTOP   <20> -         B <ACTIVE> 
	MSHOME          <1e> - <GROUP> B <ACTIVE> 
	MSHOME          <1d> -         B <ACTIVE> 
	..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 

	MAC Address = xx-xx-xx-xx-xx-xx

	DESKTOP -> MSHOME
-----------
Domain=[DESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
Domain=[DESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_OK

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
Domain=[DESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
Domain=[DESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_OK

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
"
and here is my samba.conf file:

"
[global]
    ; General server settings
netbios name = UBUNTU
    
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
    path = //Desktop/hpdeskjet
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[pictures]
path = /home/xxxx/pictures
available = yes
browsable = yes
public = yes
writable = yes

comment = my photos
[film]
path = /home/xxxx/film
available = yes
browsable = yes
public = yes
writable = yes


comment = feature films
[music]
path = /home/xxxx/music
available = yes
browsable = yes
public = yes
writable = yes



comment = my music files
[Torrents]
path = /home/xxxx/Torrents
available = yes
browsable = yes
public = yes
writable = yes

comment = torrent files
[Tv_Shows]
path = /home/xxxx/Tv_Shows
available = yes
browsable = yes
public = yes
writable = yes

comment = tv shows video files
[downloads]
path = /home/xxxx/downloads
available = yes
browsable = yes
public = yes
writable = yes

comment = temp files
[Desktop]
path = /home/xxxx/Desktop
available = yes
browsable = yes
public = yes
writable = yes
comment = xubuntu desktop
"
[/COLOR]

---

