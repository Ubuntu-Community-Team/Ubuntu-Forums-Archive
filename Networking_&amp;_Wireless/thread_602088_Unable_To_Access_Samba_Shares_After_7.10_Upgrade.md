---
title: "Unable To Access Samba Shares After 7.10 Upgrade"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by TJLawJX on 2007-11-03
I'm stumped, any help or suggestions would be much appreciated.

I was running Fiesty and had Samba working perfectly. All my Windows XP machines could connect to my shares without the need for credentials just the way I wanted things set up.  was able to map drives, printers etc ... 

I upgraded the machine serving these shares and printers to 7.10 Desktop from 7.04 Desktop.....  now the shares are visible when accessing them via \\machinename  from the XP run box.  However once you try to open the 7.10 share I get a pop-up message stating "\\machinename\storage refers to a location that is unavailable. It could be  ....."

From the 7.10 machine that is serving the shares I can connect to the XP machines, mount them, read / write files with ease.  If I try to access smb://workgroup from the 7.10 machine I am returned the message "The folder contents could not be displayed. Sorry, couldn't display all the contents  of "Windows Network: workgroup" "

I have noticed in /var/log the following:


log.xpmachine >>

```

[2007/11/03 21:33:03, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User tj !
[2007/11/03 21:33:12, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User tj !
[2007/11/03 21:33:14, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User nobody !
[2007/11/03 21:33:15, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User tj !
[2007/11/03 21:33:17, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User nobody !
[2007/11/03 21:33:17, 1] smbd/service.c:make_connection_snum(1033)
  xpmachine (xxx.xxx.xxx.XXX) connect to service storage initially as user nobody (uid=65534, gid=65534) (pid 11133)
[2007/11/03 21:33:25, 1] smbd/service.c:close_cnum(1230)
  xpmachine (xxx.xxx.xxx.xxx) closed connection to service storage

```

log.machinename (7.10) >>

```

 NOTE: Service PhotoSmart-7760 is flagged unavailable.
[2007/11/02 22:17:03, 1] param/loadparm.c:service_ok(3026)
  NOTE: Service cdrom is flagged unavailable.
[2007/11/02 22:17:03, 0] param/loadparm.c:lp_do_parameter(3529)
  Global parameter guest account found in service section!
[2007/11/02 22:17:03, 1] param/loadparm.c:service_ok(3026)
  NOTE: Service PhotoSmart-7760 is flagged unavailable.
[2007/11/03 21:13:07, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User nobody !

```

Below is my smb.conf >>

```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/11/03 21:43:52

[global]
	interfaces = eth*
	security = SHARE
	encrypt passwords = No
	null passwords = Yes
	log file = /var/log/samba/log.%m
	max log size = 1000
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	hosts allow = xxx.xxx.xxx.xxx/255.255.255.0

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 
	force printername = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes

[storage]
	path = /storage
	read only = No
	guest ok = Yes

[PhotoSmart-7760]
	comment = PhotoSmart-7760
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 
	printer name = PhotoSmart-7760
	force printername = Yes
	browseable = No
	oplocks = No
	share modes = No

```

So I figure ok the user "nobody" doesn't really exist.  So I created a user named "guest" assigned the group "guest" to it.
Modified the smb.conf again using SWAT to change the guest account to said created user. Start and stopped smbd and nmbd via SWAT 

smbd: running
nmbd: running
winbindd: not running

log.xpmachine >>

```

[2007/11/03 21:51:53, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User guest !

```

removing the guest account completely from the setup results in a failed service restart:

log.smbd >>

```

[2007/11/03 21:57:06, 0] smbd/server.c:main(944)
  smbd version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2007/11/03 21:57:06, 0] passdb/pdb_interface.c:guest_user_info(256)
  guest_user_info: Unable to locate guest account []!
[2007/11/03 21:57:06, 0] smbd/server.c:main(1059)
  ERROR: failed to setup guest info.

```


Configuring using SWAT to authenticate via "USER" and setting each of the users of the 7.10 machine as valid users and then trying to access the share generates this:

log.xpmachine >>

```

[2007/11/03 21:51:53, 0] auth/pampass.c:smb_pam_passcheck(809)
  smb_pam_passcheck: PAM: smb_pam_auth failed - Rejecting User guest !

```


As I have left it for now here is my full view Samba Configuration as stated by SWAT.


```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/11/03 22:13:58

[global]
	dos charset = CP850
	unix charset = UTF-8
	display charset = LOCALE
	workgroup = WORKGROUP
	realm = 
	netbios name = machinename
	netbios aliases = 
	netbios scope = 
	server string = Samba 3.0.26a
	interfaces = eth*
	bind interfaces only = No
	security = SHARE
	auth methods = 
	encrypt passwords = No
	update encrypted = No
	client schannel = Auto
	server schannel = Auto
	allow trusted domains = Yes
	map to guest = Never
	null passwords = Yes
	obey pam restrictions = No
	password server = *
	smb passwd file = /etc/samba/smbpasswd
	private dir = /etc/samba
	passdb backend = smbpasswd
	algorithmic rid base = 1000
	root directory = 
	guest account = nobody
	enable privileges = Yes
	pam password change = No
	passwd program = 
	passwd chat = *new*password* %n\n *new*password* %n\n *changed*
	passwd chat debug = No
	passwd chat timeout = 2
	check password script = 
	username map = 
	password level = 0
	username level = 0
	unix password sync = No
	restrict anonymous = 0
	lanman auth = Yes
	ntlm auth = Yes
	client NTLMv2 auth = No
	client lanman auth = Yes
	client plaintext auth = Yes
	preload modules = 
	use kerberos keytab = No
	log level = 0
	syslog = 1
	syslog only = No
	log file = /var/log/samba/log.%m
	max log size = 1000
	debug timestamp = Yes
	debug prefix timestamp = No
	debug hires timestamp = No
	debug pid = No
	debug uid = No
	enable core files = Yes
	smb ports = 445 139
	large readwrite = Yes
	max protocol = NT1
	min protocol = CORE
	read bmpx = No
	read raw = Yes
	write raw = Yes
	disable netbios = No
	reset on zero vc = No
	acl compatibility = auto
	defer sharing violations = Yes
	nt pipe support = Yes
	nt status support = Yes
	announce version = 4.9
	announce as = NT
	max mux = 50
	max xmit = 16644
	name resolve order = lmhosts wins host bcast
	max ttl = 259200
	max wins ttl = 518400
	min wins ttl = 21600
	time server = No
	unix extensions = Yes
	use spnego = Yes
	client signing = auto
	server signing = No
	client use spnego = Yes
	enable asu support = No
	svcctl list = 
	deadtime = 0
	getwd cache = Yes
	keepalive = 300
	lpq cache time = 30
	max smbd processes = 0
	paranoid server security = Yes
	max disk size = 0
	max open files = 10000
	open files database hash size = 10007
	socket options = TCP_NODELAY
	use mmap = Yes
	hostname lookups = No
	name cache timeout = 660
	load printers = Yes
	printcap cache time = 750
	printcap name = 
	cups server = 
	iprint server = 
	disable spoolss = No
	addport command = 
	enumports command = 
	addprinter command = 
	deleteprinter command = 
	show add printer wizard = Yes
	os2 driver map = 
	mangling method = hash2
	mangle prefix = 1
	max stat cache size = 1024
	stat cache = Yes
	machine password timeout = 604800
	add user script = 
	rename user script = 
	delete user script = 
	add group script = 
	delete group script = 
	add user to group script = 
	delete user from group script = 
	set primary group script = 
	add machine script = 
	shutdown script = 
	abort shutdown script = 
	username map script = 
	logon script = 
	logon path = \\%N\%U\profile
	logon drive = 
	logon home = \\%N\%U
	domain logons = No
	os level = 20
	lm announce = Auto
	lm interval = 60
	preferred master = Auto
	local master = Yes
	domain master = Auto
	browse list = Yes
	enhanced browsing = Yes
	dns proxy = Yes
	wins proxy = No
	wins server = 
	wins support = No
	wins hook = 
	kernel oplocks = Yes
	lock spin time = 200
	oplock break wait time = 0
	ldap admin dn = 
	ldap delete dn = No
	ldap group suffix = 
	ldap idmap suffix = 
	ldap machine suffix = 
	ldap passwd sync = no
	ldap replication sleep = 1000
	ldap suffix = 
	ldap ssl = no
	ldap timeout = 15
	ldap page size = 1024
	ldap user suffix = 
	add share command = 
	change share command = 
	delete share command = 
	eventlog list = 
	config file = 
	preload = 
	lock directory = 
	pid directory = /var/run/samba
	utmp directory = 
	wtmp directory = 
	utmp = No
	default service = 
	message command = 
	get quota command = 
	set quota command = 
	remote announce = 
	remote browse sync = 
	socket address = 0.0.0.0
	homedir map = auto.home
	afs username map = 
	afs token lifetime = 604800
	log nt token command = 
	time offset = 0
	NIS homedir = No
	usershare allow guests = No
	usershare max shares = 0
	usershare owner only = Yes
	usershare path = /var/run/samba/usershares
	usershare prefix allow list = 
	usershare prefix deny list = 
	usershare template share = 
	panic action = /usr/share/samba/panic-action %d
	host msdfs = Yes
	passdb expand explicit = No
	idmap domains = 
	idmap backend = 
	idmap alloc backend = 
	idmap cache time = 900
	idmap negative cache time = 120
	idmap uid = 
	idmap gid = 
	template homedir = /home/%D/%U
	template shell = /bin/false
	winbind separator = \
	winbind cache time = 300
	winbind enum users = No
	winbind enum groups = No
	winbind use default domain = No
	winbind trusted domains only = No
	winbind nested groups = Yes
	winbind nss info = template
	winbind refresh tickets = No
	winbind offline logon = No
	winbind normalize names = No
	comment = 
	path = 
	username = 
	invalid users = root
	valid users = 
	admin users = 
	read list = 
	write list = 
	printer admin = 
	force user = 
	force group = 
	read only = Yes
	acl check permissions = Yes
	acl group control = No
	acl map full control = Yes
	create mask = 0744
	force create mode = 00
	security mask = 0777
	force security mode = 00
	directory mask = 0755
	force directory mode = 00
	directory security mask = 0777
	force directory security mode = 00
	force unknown acl user = No
	inherit permissions = No
	inherit acls = No
	inherit owner = No
	guest only = No
	guest ok = No
	only user = No
	hosts allow = xxx.xxx.xxx.xxx/255.255.255.0
	hosts deny = 
	allocation roundup size = 1048576
	aio read size = 0
	aio write size = 0
	aio write behind = 
	ea support = No
	nt acl support = Yes
	profile acls = No
	map acl inherit = No
	afs share = No
	block size = 1024
	change notify = Yes
	directory name cache size = 100
	kernel change notify = Yes
	max connections = 0
	min print space = 0
	strict allocate = No
	strict sync = No
	sync always = No
	use sendfile = No
	write cache size = 0
	max reported print jobs = 0
	max print jobs = 1000
	printable = No
	printing = bsd
	cups options = 
	print command = lpr -r -P'%p' %s
	lpq command = lpq -P'%p'
	lprm command = lprm -P'%p' %j
	lppause command = 
	lpresume command = 
	queuepause command = 
	queueresume command = 
	printer name = 
	use client driver = No
	default devmode = Yes
	force printername = No
	printjob username = %U
	default case = lower
	case sensitive = Auto
	preserve case = Yes
	short preserve case = Yes
	mangling char = ~
	hide dot files = Yes
	hide special files = No
	hide unreadable = No
	hide unwriteable files = No
	delete veto files = No
	veto files = 
	hide files = 
	veto oplock files = 
	map archive = Yes
	map hidden = No
	map system = No
	map readonly = yes
	mangled names = Yes
	mangled map = 
	store dos attributes = No
	dmapi support = No
	browseable = Yes
	blocking locks = Yes
	csc policy = manual
	fake oplocks = No
	locking = Yes
	oplocks = Yes
	level2 oplocks = Yes
	oplock contention limit = 2
	posix locking = Yes
	strict locking = Auto
	share modes = Yes
	dfree cache time = 0
	dfree command = 
	copy = 
	include = 
	preexec = 
	preexec close = No
	postexec = 
	root preexec = 
	root preexec close = No
	root postexec = 
	available = Yes
	volume = 
	fstype = NTFS
	set directory = No
	wide links = Yes
	follow symlinks = Yes
	dont descend = 
	magic script = 
	magic output = 
	delete readonly = No
	dos filemode = No
	dos filetimes = Yes
	dos filetime resolution = No
	fake directory create times = No
	vfs objects = 
	msdfs root = No
	msdfs proxy = 

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 
	force printername = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes

[storage]
	path = /storage
	read list = tj, jen, guest
	write list = tj, jen, guest
	read only = No
	guest ok = Yes

[PhotoSmart-7760]
	comment = PhotoSmart-7760
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 
	printer name = PhotoSmart-7760
	force printername = Yes
	browseable = No
	oplocks = No
	share modes = No

```

---

### Post by homerj742 on 2007-11-05
I'm having issues as well. Any help would be greatly appreciated.

---

### Post by mikexstudios on 2007-11-06
Try changing:
encrypt passwords = No
to:
encrypt passwords = yes

Although I didn't have the same problem as you did, it was somewhat similar, and changing that line fixed it.

---

### Post by TJLawJX on 2007-11-06
OMG, now that is just goofy, that worked perfectly, no other changes were needed to fix the problem.  Mike Thank You bud!!

---

### Post by pacohc on 2008-05-19
I had this problem too still not 100% solved

"encrypt passwords = Yes" allows windows 2000 and Xp machines to connect to samba, BUT NOT WINDOWS 98 SE !!

to allow windows 98 to connect I needed to change 2 things:
"encrypt passwords = No" in ubuntu samba and add the regitry key
"[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\VNETSUP]
"EnablePlainTextPassword"=dword:00000001"
in W98 SE (got from microsoft support web)
but then w2000 and wXP DON'T WORK anymore !!!

does anybody have an idea how to get both 98, 2000 and Xp connect together to samba on gutsy 7.1 ?

---

### Post by pacohc on 2008-05-20
Finally, after some "googling", I found the way how to connect at the same time windows 98, 2000 and XP machines to the ubuntu 7.1 gutsy samba shares. I had to use plain text passwords, it is not the best for security, but at the moment I have all working again

if anybody is interested:

SAMBA SHARES WITH NO PASSWORD ENCRYPTION

[global] section in /etc/samba/smb.conf file:

	encrypt password = no

Then add the following register configurations
on the windows machines:

In Windows 95 or 98
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\VNETSUP
"EnablePlainTextPassword"=dword:00000001

Windows NT
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Rdr\Parameters
"EnablePlainTextPassword"=dword:00000001

Windows 2000
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkStation\Parameters
"EnablePlainTextPassword"=dword:00000001

Windows XP
   1. Click on Start>Programs>Administrative Tools
      If Administrative Tools is not there then go to 
      Start>Settings>Control Panel and select "Administrative Tools".
   2. Double-click Local Security Policy.
   3. Click the plus sign next to "Local Policies".
   4. Double-click "Security Options".
   5. Scroll down to near the bottom of the list.
   6. Right-Click->Properties on 'Microsoft network client: 
      'Send unencrypted passwords to connect to third-party SMB servers'
   7. Click the Enabled radio button.
   8. Click OK.
   9. Close the Local Security Settings Window.
  10. Reboot Windows XP.

---

### Post by pacohc on 2008-07-01
today the automatic security update solved the problem, all seems to works fine now again, both plain text and encrypted passwords

---

