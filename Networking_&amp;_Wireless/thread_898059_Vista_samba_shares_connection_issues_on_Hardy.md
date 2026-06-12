---
title: "Vista samba shares connection issues on Hardy"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by enigmik on 2008-08-22
I am having trouble sharing a ntfs hard drive from my ubuntu desktop to my vista computer. I have gotten this to work fine in the past but it stopped working after a reboot. My ubuntu desktop cannot see the vista computer at all (which is fine because I only want to access the HD from Vista with read/write permissions) and the Vista Laptop will show the Desktop computer in the network map but it takes a few refreshes to do so. If I click on it I get an error message saying something like cannot connect \\desktop.

I have read numerous post and googled until my eyes bled but nothing I do seems to work. I am using a wireless linksys  WRT54GS router. I dont know if it is a Vista setting or something in the conif file or something else. I did the regedit thing but that did not work either.

Here is the conf file:

[global]
    ; General server settings
    netbios name = desktop
    server string = 
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    usershare owner only = False
  

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




testparm results:

mike@desktop:~$ sudo testparm '/etc/samba/smb.conf' 
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = 
	null passwords = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	usershare owner only = No

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No

[MyFiles]
	comment = shares
	path = /dev/sdb
	read only = No
	create mask = 0770
	directory mask = 0770
	guest ok = Yes


Note: I am not sure if path should = /dev/sdb or /media/disk as nautillus shows.

I also set the share with nautillus as well.

Also I ran this from the ubuntu desktop just as another test:


mike@desktop:~$ sudo smbclient -L DESKTOP
Password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service ()
	MyFiles         Disk      shares
	print$          Disk      
	PDF             Printer   PDF
	Deskjet_5400_series Printer   HP Deskjet 5400 series
	shares          Disk      
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	DESKTOP              

	Workgroup            Master
	---------            -------
	WORKGROUP            DESKTOP

I am at a loss. Any suggestions?

---

### Post by enigmik on 2008-08-23
really need help... bump

---

### Post by enigmik on 2008-08-23
Well ok. I think I must have had something conflicting with samba. I have tried so many things and other programs to connect vista to my shared folders that something much have gotten corrupted. Now that I think about it everything ran fine until I tried KDE. I think I'll stick with GNOME.

Anyway, I installed Ubuntu within Visa on my laptop and still I could not connect so I reinstalled Ubuntu Hardy on my desktop. Then I logged in as root, right clicked the hard drive in nautilus and enabled sharing, waited for samba to install and BAM! My Vista machine connects with no problems and with no smb.conf file configuration.... works for now. However, I fear that Vista will not connect when I reboot my Ubuntu Desktop. We shall see.

---

