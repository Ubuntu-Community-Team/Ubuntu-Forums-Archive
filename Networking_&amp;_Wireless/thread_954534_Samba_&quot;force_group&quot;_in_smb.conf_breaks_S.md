---
title: "Samba &quot;force group&quot; in smb.conf breaks Samba"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2008-10-21
I´m having a lot of trouble getting the "force group" parameter working. I´ve tinkered with Samba a lot now, and as a final measure I went as far as to purge it and reinstall.

I have a share that looks like this:

[I][Test10]
path = /test/
comment = Testutdelning
;force group = test
;force user = test
create mask = 0660
directory mask = 0771
valid users = administrator
read only = no
guest ok = no[/I]

Works like a charm until I uncomment the "force user" line. I get:

[I]root@eduserver:/mnt# mount -t smbfs -o username=administrator \/\/192.168.2.163\/Test10 t
Password: 
mount error 5 = Input/output error
[/I]

I´m GUESSING my problems have something to do with samba not accessing the UNIX groups properly or using Winbind instead, but really I don´t know.. :confused:

Here is my smb.conf, tidied by "testparm":

[I][global]
	workgroup = SKOLAN
	server string = %h server (Samba, Ubuntu)
	interfaces = 127.0.0.0/8, eth0
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	guest account = sambaelev
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	log level = 6
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[Delad]
	comment = Läs- och skrivrättigheter för alla
	path = /home/GRUPPER/elever/Delad/
	force group = elever
	read only = No
	create mask = 0774
	directory mask = 0775
	guest only = Yes
	guest ok = Yes

[Test10]
	comment = Testutdelning
	path = /test/
	valid users = administrator
	force group = test
	read only = No
	create mask = 0660
	directory mask = 0771

[Gemensam]
	comment = Nya, kanske förbättrade Gemensam-utdelningen för lärare
	path = /home/GRUPPER/lärare/Gemensam
	valid users = johanna, gunilla, kaj, administrator, sara, birgitta
	read only = No
	create mask = 0660
	directory mask = 0771[/I]

Can anyone help me?

Here´s some, perhaps relevant, bits of the logs:

[I][2008/10/21 16:44:02, 5] auth/auth_util.c:debug_nt_user_token(448)
  NT user token: (NULL)
[2008/10/21 16:44:02, 5] auth/auth_util.c:debug_unix_user_token(474)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2008/10/21 16:44:02, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2008/10/21 16:44:02, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/reply.c(514) cmd=117 (SMBtconX) NT_STATUS_NO_SUCH_GROUP
[/I]

Has anyone else had to deal with this?

---

### Post by Iowan on 2008-10-21
The last error message suggests there is no "test" group.  Did you create one?

---

### Post by Diskdoc on 2008-10-22
You were probably right. I assumed there was a "test" group as I had created a "test" user in Ubuntu using the user administration tool. The real group I had had problems with and wanted to get things working with was "larare".

However, perhaps due to my reinstalling Samba yesterday the passdb.tdb file ..or something else in Samba had been messed up and the private share "Gemensam" wouldn´t work today. I restored the files in /var/lib/samba from a backup and..

[COLOR="Red"]..suddenly, dazed, I watched in absolute amazement as the "force group" and "valid users = @group" problem that had been bugging me for **weeks** *disappeared!* [-o< [/COLOR]

So, problem solved. It MIGHT have been earlier (few months ago) messing around with LDAP that messed up Samba, but if that´s true I never realized exactly how.

A great burden is lifted, praise to the great flying spaghetti monster!:biggrin:

---

