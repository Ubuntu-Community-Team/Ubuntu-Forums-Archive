---
title: "Network Authentication guide"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-06-21
Hi I need to know how to set up network Authentication with ubuntu and windows machines. I have one ubuntu 1104 machine as proxy,dns,samba servers. Windows machaines need to be able to have their samba shares come up when the windows user logs on also need this for the other ubuntu boxes to. How do I do this? A gui would be good to would make thing easyer for me. also how do I use samba as a domain controler for the windows boxes? this is  a small home/office network.

computers
1 ubuntu 1104
1 lubuntu 1104
1 ubuntu 1004
1 windows 7
1 windows xp

severs on ubuntu only
proxy ip 1.2.3.7
dns ip 1.2.3.7
samba ip 1.2.3.7

samba smb.conf
# Samba config file created using SWAT
# from UNKNOWN (W)
# Date: 2010/06/13 22:20:03

[global]
	workgroup = LBERMUDEZ
	server string = %h server (Samba, Ubuntu)
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
	valid users = lance
	write list = lance

[music]
	path = /home/lance/Music
	write list = 
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[acer]
	path = /home/lance/500gb/mombackup
	read only = No
[music]
	path = /home/lance/Music
	write list = 
	guest ok = Yes

---

### Post by lance bermudez on 2011-06-21
Someone told me to set up a OpenLDAP Server would that work? again how do you do that with a gui for the user and how do i use samba as a domain controler for my ubuntu and windows hosts.

---

### Post by lance bermudez on 2011-06-24
I followed this guid at 
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)
I have samba and ldap working so how do i add windows 7 to the samba domain controler? He has a guid on how to add the other linux boxes to the pdc put not windows as far as i can tell that is. I looked at 
[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)
put do not know where to use 
sudo net groupmap add ntgroup="Domain Admins" unixgroup=sysadmin rid=512 type=d
I have admin but no sysadmin on my linux box. Could I just use a admin user say JohnDoe to add windows to the domain? Do I use this command on linux box or the windows? I get an error when i try it on linux. also what is this for

net rpc rights grant "EXAMPLE\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege \
SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
It does not work either.

---

### Post by tgm4883 on 2011-06-24
> **lance bermudez said:**
> I followed this guid at 
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)
I have samba and ldap working so how do i add windows 7 to the samba domain controler? He has a guid on how to add the other linux boxes to the pdc put not windows as far as i can tell that is. I looked at 
[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)
put do not know where to use 
sudo net groupmap add ntgroup="Domain Admins" unixgroup=sysadmin rid=512 type=d
I have admin but no sysadmin on my linux box. Could I just use a admin user say JohnDoe to add windows to the domain? Do I use this command on linux box or the windows? I get an error when i try it on linux. also what is this for

net rpc rights grant "EXAMPLE\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege \
SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
It does not work either.

I've used the second link before except on 11.04 (ultimately I switched to Samba4 so I could have a full Active Directory replacement).

IIRC, when I used the 

```
sudo net groupmap add ntgroup="Domain Admins" unixgroup=sysadmin rid=512 type=d
```

I replaced sysadmin with my own users group. This could likely be replaced with the admin group and any user part of that group could manage it.

---

### Post by lance bermudez on 2011-06-26
I have a user lets say JohnDoe with admin rights so it would look like this right?

sudo net groupmap add ntgroup="Domain Admins" unixgroup=JohnDoe rid=512 type=d

really dumb question  time do i enter this in linux or windows? In windows don't i just go to where you set the domain under system settings like you would in the windows world then use my linux user to add computer to the domain?

---

### Post by lance bermudez on 2011-06-26
sudo net groupmap add ntgroup="Domain Admins" unixgroup=sysadmin rid=512 type=d

I do not have unixgroup or sysadmin on my linux box does it matter?

---

### Post by lance bermudez on 2011-06-27
Have tried this two ways below is what i get

lance@Therese:/etc$ net groupmap add ntgroup="Domain Admins" unixgroup=lance rid=512 type=d
[2011/06/26 21:45:00.273811,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:00.273885,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:00.273898,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:00.273909,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:01.274059,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:01.274125,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:01.274152,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:01.274175,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:02.274339,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:02.274397,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:02.274423,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:02.274447,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:03.274623,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:03.274687,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:03.274713,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:03.274738,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:04.274899,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:04.274956,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:04.274983,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:04.275006,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:05.275159,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:05.275213,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:05.275239,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:05.275263,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:06.275412,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:06.275467,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:06.275494,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:06.275517,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:07.275685,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:07.275744,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:07.275770,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:07.275794,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:08.275972,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:08.276031,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:08.276057,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:08.276081,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:09.276238,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:09.276293,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:09.276319,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:09.276343,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:10.276514,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:10.276583,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:10.276610,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:10.276634,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:11.276791,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:11.276847,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:11.276873,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:11.276897,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:12.277060,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:12.277117,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:12.277143,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:12.277167,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:13.277327,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:13.277383,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:13.277409,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:13.277432,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:14.277615,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:14.277680,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:14.277707,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:14.277731,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:15.277946,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278002,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278028,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:15.278052,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:15.278108,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278146,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 10604): could not open secrets db
[2011/06/26 21:45:15.282464,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 14 stack frames:
   #0 net(log_stack_trace+0x2d) [0x3f5c7d]
   #1 net(smb_panic+0x2d) [0x3f5d9d]
   #2 net(get_global_sam_sid+0x6c1) [0x2fa481]
   #3 net(pdb_init_ldapsam+0x7a2) [0x3a1ac2]
   #4 net(make_pdb_method_name+0xf3) [0x394fc3]
   #5 net(+0x1da44d) [0x39544d]
   #6 net(pdb_getgrgid+0xb) [0x396d6b]
   #7 net(+0xb94c0) [0x2744c0]
   #8 net(net_run_function+0x75) [0x28e125]
   #9 net(net_groupmap+0x5d) [0x274c0d]
   #10 net(net_run_function+0x75) [0x28e125]
   #11 net(main+0x819) [0x252be9]
   #12 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0xb58e37]
   #13 net(+0x96271) [0x251271]
[2011/06/26 21:45:15.282611,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 10604]
[2011/06/26 21:45:15.295019,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/06/26 21:45:15.295103,  0] lib/fault.c:312(dump_core)
  Can not dump core: corepath not set up


lance@Therese:/etc$ sudo net groupmap add ntgroup="Domain Admins" unixgroup=lance rid=512 type=d
adding entry for group Domain Admins failed!

---

### Post by tgm4883 on 2011-06-27
> **lance bermudez said:**
> Have tried this two ways below is what i get

lance@Therese:/etc$ net groupmap add ntgroup="Domain Admins" unixgroup=lance rid=512 type=d
[2011/06/26 21:45:00.273811,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:00.273885,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:00.273898,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:00.273909,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:01.274059,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:01.274125,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:01.274152,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:01.274175,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:02.274339,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:02.274397,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:02.274423,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:02.274447,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:03.274623,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:03.274687,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:03.274713,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:03.274738,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:04.274899,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:04.274956,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:04.274983,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:04.275006,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:05.275159,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:05.275213,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:05.275239,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:05.275263,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:06.275412,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:06.275467,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:06.275494,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:06.275517,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:07.275685,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:07.275744,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:07.275770,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:07.275794,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:08.275972,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:08.276031,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:08.276057,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:08.276081,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:09.276238,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:09.276293,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:09.276319,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:09.276343,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:10.276514,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:10.276583,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:10.276610,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:10.276634,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:11.276791,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:11.276847,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:11.276873,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:11.276897,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:12.277060,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:12.277117,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:12.277143,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:12.277167,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:13.277327,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:13.277383,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:13.277409,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:13.277432,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:14.277615,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:14.277680,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:14.277707,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:14.277731,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:15.277946,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278002,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278028,  0] passdb/secrets.c:806(fetch_ldap_pw)
  fetch_ldap_pw: neither ldap secret retrieved!
[2011/06/26 21:45:15.278052,  0] lib/smbldap.c:1107(smbldap_connect_system)
  ldap_connect_system: Failed to retrieve password from secrets.tdb
[2011/06/26 21:45:15.278108,  0] passdb/secrets.c:73(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2011/06/26 21:45:15.278146,  0] lib/util.c:1465(smb_panic)
  PANIC (pid 10604): could not open secrets db
[2011/06/26 21:45:15.282464,  0] lib/util.c:1569(log_stack_trace)
  BACKTRACE: 14 stack frames:
   #0 net(log_stack_trace+0x2d) [0x3f5c7d]
   #1 net(smb_panic+0x2d) [0x3f5d9d]
   #2 net(get_global_sam_sid+0x6c1) [0x2fa481]
   #3 net(pdb_init_ldapsam+0x7a2) [0x3a1ac2]
   #4 net(make_pdb_method_name+0xf3) [0x394fc3]
   #5 net(+0x1da44d) [0x39544d]
   #6 net(pdb_getgrgid+0xb) [0x396d6b]
   #7 net(+0xb94c0) [0x2744c0]
   #8 net(net_run_function+0x75) [0x28e125]
   #9 net(net_groupmap+0x5d) [0x274c0d]
   #10 net(net_run_function+0x75) [0x28e125]
   #11 net(main+0x819) [0x252be9]
   #12 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0xb58e37]
   #13 net(+0x96271) [0x251271]
[2011/06/26 21:45:15.282611,  0] lib/util.c:1470(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 10604]
[2011/06/26 21:45:15.295019,  0] lib/util.c:1478(smb_panic)
  smb_panic(): action returned status 0
[2011/06/26 21:45:15.295103,  0] lib/fault.c:312(dump_core)
  Can not dump core: corepath not set up


lance@Therese:/etc$ sudo net groupmap add ntgroup="Domain Admins" unixgroup=lance rid=512 type=d
adding entry for group Domain Admins failed!

The second way is the correct way, but you will need to post some relevant logs to show any error messages.  Likely these are in /var/log/samba/

---

### Post by lance bermudez on 2011-06-28
which one do you need to see?
lance@Therese:/var/log/samba$ ls
cores                 log.__ffff_10.0.0.11  log.__ffff_10.0.0.9     log.mysambaserver  log.swat
log.10.0.0.3          log.__ffff_10.0.0.2   log.__ffff_127.0.1.1    log.nmbd           log.therese
log.127.0.0.1         log.__ffff_10.0.0.3   log.__ffff_192.168.2.3  log.nmbd.1.gz      log.wilkins
log.192.168.2.3       log.__ffff_10.0.0.4   log.lbermudez           log.perkinsr       log.xpmedia
log.acer              log.__ffff_10.0.0.5   log.linux-ukd8          log.smbd
log.bermudezl         log.__ffff_10.0.0.6   log.momhp               log.smbd.1.gz
log.__ffff_10.0.0.10  log.__ffff_10.0.0.8   log.momhp.old           log.stfrance1

lance@Therese:/var/log/samba$ cat log.mysambaserver
[2011/06/23 23:29:09.840659,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 1 try!
[2011/06/23 23:29:10.845874,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 2 try!
[2011/06/23 23:29:11.846760,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 3 try!
[2011/06/23 23:29:12.847532,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 4 try!
[2011/06/23 23:29:13.848304,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 5 try!
[2011/06/23 23:29:14.849141,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 6 try!
[2011/06/23 23:29:15.849956,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 7 try!
[2011/06/23 23:29:16.850713,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 8 try!
[2011/06/23 23:29:17.851613,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 9 try!
[2011/06/23 23:29:18.852422,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 10 try!
[2011/06/23 23:29:19.853234,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 11 try!
[2011/06/23 23:29:20.854027,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 12 try!
[2011/06/23 23:29:21.854785,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 13 try!
[2011/06/23 23:29:22.855540,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 14 try!
[2011/06/23 23:29:23.856326,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 15 try!

---

### Post by tgm4883 on 2011-06-28
> **lance bermudez said:**
> which one do you need to see?
lance@Therese:/var/log/samba$ ls
cores                 log.__ffff_10.0.0.11  log.__ffff_10.0.0.9     log.mysambaserver  log.swat
log.10.0.0.3          log.__ffff_10.0.0.2   log.__ffff_127.0.1.1    log.nmbd           log.therese
log.127.0.0.1         log.__ffff_10.0.0.3   log.__ffff_192.168.2.3  log.nmbd.1.gz      log.wilkins
log.192.168.2.3       log.__ffff_10.0.0.4   log.lbermudez           log.perkinsr       log.xpmedia
log.acer              log.__ffff_10.0.0.5   log.linux-ukd8          log.smbd
log.bermudezl         log.__ffff_10.0.0.6   log.momhp               log.smbd.1.gz
log.__ffff_10.0.0.10  log.__ffff_10.0.0.8   log.momhp.old           log.stfrance1

lance@Therese:/var/log/samba$ cat log.mysambaserver
[2011/06/23 23:29:09.840659,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 1 try!
[2011/06/23 23:29:10.845874,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 2 try!
[2011/06/23 23:29:11.846760,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 3 try!
[2011/06/23 23:29:12.847532,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 4 try!
[2011/06/23 23:29:13.848304,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 5 try!
[2011/06/23 23:29:14.849141,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 6 try!
[2011/06/23 23:29:15.849956,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 7 try!
[2011/06/23 23:29:16.850713,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 8 try!
[2011/06/23 23:29:17.851613,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 9 try!
[2011/06/23 23:29:18.852422,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 10 try!
[2011/06/23 23:29:19.853234,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 11 try!
[2011/06/23 23:29:20.854027,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 12 try!
[2011/06/23 23:29:21.854785,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 13 try!
[2011/06/23 23:29:22.855540,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 14 try!
[2011/06/23 23:29:23.856326,  1] lib/smbldap.c:1330(another_ldap_try)
  Connection to LDAP server failed for the 15 try!

Are you running an LDAP server? Did you follow any guides to get this setup?

---

### Post by lance bermudez on 2011-06-28
I followed this guid at
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

lance@Therese:$ ldapsearch -xLLL -b "dc=lbermudez,dc=net" uid=leanne
dn: uid=leanne,ou=Users,dc=lbermudez,dc=net
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: sambaSamAccount
cn: leanne
sn: leanne
givenName: leanne
uid: leanne
uidNumber: 1002
gidNumber: 513
homeDirectory: /home/leanne
loginShell: /bin/bash
gecos: System User
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
displayName: leanne
sambaSID: S-1-5-21-309243541-3266719748-2493639525-3004
sambaPrimaryGroupSID: S-1-5-21-309243541-3266719748-2493639525-513
sambaLogonScript: allusers.bat
sambaProfilePath: "."
sambaHomePath: "."
sambaHomeDrive: ".":
sambaLMPassword: 83BBB23C5A82EEA27A1555FFAFE3FA0A
sambaAcctFlags: [U]
sambaNTPassword: B329C5D4F278EC8752336F65E99F6DE0
sambaPwdLastSet: 1308897542
sambaPwdMustChange: 1312785542
shadowLastChange: 15149
shadowMax: 45

---

### Post by tgm4883 on 2011-06-28
> **lance bermudez said:**
> I followed this guid at
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

lance@Therese:$ ldapsearch -xLLL -b "dc=lbermudez,dc=net" uid=leanne
dn: uid=leanne,ou=Users,dc=lbermudez,dc=net
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
objectClass: sambaSamAccount
cn: leanne
sn: leanne
givenName: leanne
uid: leanne
uidNumber: 1002
gidNumber: 513
homeDirectory: /home/leanne
loginShell: /bin/bash
gecos: System User
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaPwdCanChange: 0
displayName: leanne
sambaSID: S-1-5-21-309243541-3266719748-2493639525-3004
sambaPrimaryGroupSID: S-1-5-21-309243541-3266719748-2493639525-513
sambaLogonScript: allusers.bat
sambaProfilePath: "."
sambaHomePath: "."
sambaHomeDrive: ".":
sambaLMPassword: 83BBB23C5A82EEA27A1555FFAFE3FA0A
sambaAcctFlags: [U]
sambaNTPassword: B329C5D4F278EC8752336F65E99F6DE0
sambaPwdLastSet: 1308897542
sambaPwdMustChange: 1312785542
shadowLastChange: 15149
shadowMax: 45

Did you install the ldap server? Is slapd running? Are there any errors in the slapd logs?

---

### Post by lance bermudez on 2011-06-28
lance@Therese:/var/log$ sudo /etc/init.d/slapd status
 * slapd is running

I followed the [http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)
guid so if it said to intall I installed it. and it said to install 
sudo apt-get install slapd ldap-utils libpam-smbpass smbldap-tools ldap-auth-client

I installed them when the guid told me to install them. any idea as to why this is being a pain? I don't get why they are not talking to one another. I have the firewall turned off tell i can get this working.

---

### Post by lance bermudez on 2011-06-28
I have attached the slapd log from from the
cat syslog | grep slapd > /tmp/slapd-log.txt
command

---

### Post by tgm4883 on 2011-06-28
> **lance bermudez said:**
> I have attached the slapd log from from the
cat syslog | grep slapd > /tmp/slapd-log.txt
command

Looks like you need to run recovery 

```
bdb(dc=nodomain): PANIC: fatal region error detected; run recovery
```

There are also bind permissions errors, probably due to apparmor protecting bind updates from slapd

---

### Post by lance bermudez on 2011-06-29
How do I fix apparmor and run recovery?

---

### Post by lance bermudez on 2011-06-29
found this at [https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html) is this what you are talking about for apparmor?

The AppArmor profile for slapd will need to be adjusted for the accesslog database location. Edit /etc/apparmor.d/usr.sbin.slapd adding:

  /var/lib/ldap/accesslog/ r,
  /var/lib/ldap/accesslog/** rwk,

Then create the directory, reload the apparmor profile, and copy the DB_CONFIG file:

sudo -u openldap mkdir /var/lib/ldap/accesslog
sudo -u openldap cp /var/lib/ldap/DB_CONFIG /var/lib/ldap/accesslog/
sudo /etc/init.d/apparmor reload

---

### Post by lance bermudez on 2011-07-01
I was looking around and found this I have it in a pic for you. Is the pic what the log is talking about

Jul  1 20:24:24 Therese slapd[10953]: bdb(dc=nodomain): PANIC: fatal region error detected; run recovery

so how do i fix the error. I need a step by step for dummies.

---

