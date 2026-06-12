---
title: "* smbd is not running."
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by LeBurt on 2008-11-03
Hi all,

Since I upgraded to Intrepid, samba's been acting up. Essentially, the server part won't start, although the client (and nmbd) appear ok. In other words, I can see Windows from Ubuntu, but not the other way around.

I've been mainly following this [HOWTO]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html") among other sources, here's a few things I tried to get to the bottom of this:

Connecting to myself:
```
burt@ciabata:/etc/samba$ smbclient -L ciabata
Connection to ciabata failed (Error NT_STATUS_CONNECTION_REFUSED)
```

Checking status:
```
burt@ciabata:/etc/samba$ sudo /etc/init.d/samba status
 * nmbd is running.
 * smbd is not running.
```

Trying to restart:
```
burt@ciabata:/etc/samba$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons [ OK ] 
 * Starting Samba daemons [ OK ]
```

Checking status again:
```
burt@ciabata:/etc/samba$ sudo /etc/init.d/samba status
 * nmbd is running.
 * smbd is not running.
```

Checking if netbios-ssn is in liste mode (it's not even in the list!):
```
burt@ciabata:/etc/samba$ netstat -a | grep netbios
udp        0      0 ciabata.loca:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 ciabata.loc:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
```

Checking if smb.conf is ok:
```
burt@ciabata:/etc/samba$ testparm smb.conf
Load smb config files from smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[videos]"
Processing section "[music]"
Processing section "[scans]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = WIFIPITA
	interfaces = eth0, lo
	map to guest = Bad User
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	log file = /var/log/samba/log.%m
	usershare allow guests = Yes
	hosts allow = 192.168.0.0/24, 127.
	hosts deny = all

[homes]
	comment = Burt Shared
	read only = No
	create mask = 0700
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[videos]
	path = /home/burt/Videos
	valid users = burt
	read only = No
	create mask = 0700
	directory mask = 0700
	guest ok = Yes

[music]
	path = /home/burt/Music
	read only = No
	guest ok = Yes

[scans]
	path = /home/burt/Scans
	read only = No
	guest ok = Yes
```

Another way to check samba's status:
```
burt@ciabata:/etc/samba$ sudo smbstatus
sessionid.tdb not initialised

Service      pid     machine       Connected at
-------------------------------------------------------

/var/run/samba/locking.tdb not initialised
This is normal if an SMB client has never connected to your server.
```

Out of ideas, just listing smb.conf:
```
burt@ciabata:/etc/samba$ cat smb.conf
[global]
   workgroup = WIFIPITA
   hosts deny = all
   hosts allow = 192.168.0.0/24 127.
   interfaces = eth0 lo
   log file = /var/log/samba/log.%m
;   max log size = 1000
;   syslog = 0
;   panic action = /usr/share/samba/panic-action %d
;   security = user
;   encrypt passwords = true
;   passdb backend = tdbsam
;   obey pam restrictions = yes
;   guest account = nobody
;   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user


########## Printing ##########

   load printers = yes

############ Misc ############

   socket options = TCP_NODELAY
   usershare allow guests = yes

#======================= Share Definitions =======================

[homes]
   comment = Burt Shared
   browseable = yes
   read only = no
   create mask = 0700
   directory mask = 0700
;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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
   guest ok = yes
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[videos]
   path = /home/burt/Videos
   available = yes
   read only = no
   browsable = yes
   public = yes
   writable = yes
   directory mask = 0700
   create mask = 0700
   valid users = burt

[music]
   path = /home/burt/Music
   available = yes
   read only = no
   browsable = yes
   public = yes
   writable = yes

[scans]
   path = /home/burt/Scans
   available = yes
   read only = no
   browsable = yes
   public = yes
   writable = yes

```

---

### Post by cariboo on 2008-11-04
Oops, never mind

Jim

---

### Post by sgod51 on 2008-11-04
Try to reboot your system.

I had the same problem and that issue worked fine for me :

After reboot, the samba status returned "smbd is running"

---

### Post by LeBurt on 2008-11-04
sgod, 

As shameful as it is to admit this 8-[, it worked. After wasting 3 hours on the problem, just rebooting fixed it. After so many years of rebooting Windows, I should have known. I thought Linux wasn't plagued with reboot-as-a-quick-fix-to-anything. I guess I was wrong. :roll:

At least it got me slightly smarter on samba...

---

### Post by saidbakr on 2009-09-11
I restarted ubuntu but it still not running! In addition when I try to stop samba I got this error:
start-stop-daemon: warning: failed to kill 3263: No such process.

---

