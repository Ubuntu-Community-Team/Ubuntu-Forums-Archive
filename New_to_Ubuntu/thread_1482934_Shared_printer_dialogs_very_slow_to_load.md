---
title: "Shared printer dialogs very slow to load"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by the_travis_s on 2010-05-14
Hello,

I'm running 10.04 with a Deskjet D7260 connected and shared (possibly multiple times in multiple ways...) via both samba and the "shared" menu item on the printers applet, whatever it is that actually does.

I am able to connect to and print just fine via my Vista machine, however the print dialogs take absolutely forever to show up.
File -> Print takes approx 10 sec.
From here printer preferences for the shared printer take 25+ seconds to appear (dialog goes Not Responding while waiting).

Here's notable pieces from my smb.conf file

[global]
	workgroup = mshome
	server string = %h server (Samba, Ubuntu)
#   wins support = no
;   wins server = w.x.y.z
	dns proxy = no
;   name resolve order = lmhosts host wins bcast
#   syslog only = no



####### Authentication #######

#   security = user
;	encrypt passwords = yes
;	passdb backend = tdbsam

	obey pam restrictions = yes
	unix password sync = yes
	map to guest = bad user

########## Domains ###########
;   domain logons = yes


########## Printing ##########
#   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap

;	printing = cups
;   printcap name = cups


############ Misc ############

         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY
;   winbind enum groups = yes
;   winbind enum users = yes

	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = yes 
;	guest account = nobody

#======================= Share Definitions =======================


;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = yes
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700
	use client driver = yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = yes
	use client driver = yes
;   write list = root, @lpadmin

---

