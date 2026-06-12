---
title: "Configuring SAMBA - help!"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by SumnerBoy on 2008-02-18
Hi, I have spent the better part of the day trolling this forum and others looking for help about how to configure Samba. I am new to Linux and Ubuntu so hopefully I haven't missed anything obvious.

I have Ubuntu Server 7.10 running on a Mini-ITX box and a Dell laptop running Vista. I have a set of shares on the server;

     /home/music
     /home/photos
     /home/transfer

I want to give read access to these shares to anyone on my network - i.e. no authentication. I also want to give myself 'ben' write access. Basically I don't want people joining my network and being able to move/delete my files etc. A fairly simple requirement I thought!

When I try to access the shares from my laptop as any user, I get read-only access. This is fine except that even if I connect as 'ben' I can't seem to get write access. I have added 'ben' using smbpasswd -a and used the same password as my Vista login.

I have set the permissions on the folders/files correctly (I think). 

     drwxr-xr-x 173 root     root     4096 2008-02-19 11:54 music
     drwxr-xr-x  11 root     root     4096 2008-02-18 11:29 photos
     drwxr-xr-x  18 root     root     4096 2008-02-18 21:26 transfer

Below is an example of a sub-folder under /home/photos/...

     drwxr-xr-x  2 ben  ben  4096 2008-02-05 00:00 Stadiums

One thing I just noticed is that the parent /home/photos folder is currently owned by root - is that ok?

Below is my smb.conf file. I think I have it set up correctly, in that I have the security mode set to 'share' and have guest ok set for the shares. I then added the write list = ben to ensure I was able to make changes.

Any help would be greatly appreciated!

[global]

	### Identification ###
	workgroup = HOME

	### Authentication ###
	security = share
	encrypt passwords = yes
	passdb backend = tdbsam
	guest account = nobody

	### Logging ###
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0

	### Printing ###
	printer = MP530
	printing = CUPS
	printcap name = CUPS

	### Misc ###
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

### Printer shares ###
[print$]
	path = /var/lib/samba/printers
	browseable = yes
	guest ok = yes
	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	browseable = yes
	printable = yes
	public = yes
	create mode = 0700
	guest only = yes
	guest account = smbprint
	path = /home/smbprint

### File shares ###
[Music]
	comment = Digital Music
	path = /home/music/
	browseable = yes
	read only = yes
	guest ok = yes
	write list = ben
	create mask = 0664
	directory mask = 0775

[Photos]
	comment = Digital Photos
	path = /home/photos/
	browseable = yes
	read only = yes
	guest ok = yes
	write list = ben
	create mask = 0664
	directory mask = 0775

[Transfer]
	comment = Transfer Area
	path = /home/transfer/
	browseable = yes
	read only = yes
	guest ok = yes
	write list = ben
	create mask = 0664
	directory mask = 0775

---

### Post by SumnerBoy on 2008-02-18
I will also post some of the logs here. 

In this case I attempted to connect to the \\<Server>\Music share as 'ben' and got this in the log...

[FONT="Courier New"][2008/02/19 17:15:39, 1] smbd/service.c:make_connection_snum(1033)
  <Server> (192.168.1.2) connect to service Music initially as user ben (uid=1000, g$[/FONT]

I then tried to change the name of subfolder inside the music folder and the following was written to the log...

[FONT="Courier New"][2008/02/19 17:15:55, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 17:15:55, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 17:15:55, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 17:15:55, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users[/FONT] 

Likewise if I disconnect this mapping and try to connect using 'guest' as the user name (and no password) I get this in the logs...

[FONT="Courier New"][2008/02/19 17:21:51, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 17:21:51, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 17:21:51, 0] libsmb/ntlm_check.c:smb_pwd_check_ntlmv1(55)
  smb_pwd_check_ntlmv1: incorrect password length (64)
[2008/02/19 17:21:51, 0] libsmb/ntlm_check.c:smb_pwd_check_ntlmv1(55)
  smb_pwd_check_ntlmv1: incorrect password length (64)
[2008/02/19 17:21:51, 0] libsmb/ntlm_check.c:smb_pwd_check_ntlmv1(55)
  smb_pwd_check_ntlmv1: incorrect password length (64)
[2008/02/19 17:21:51, 0] libsmb/ntlm_check.c:smb_pwd_check_ntlmv1(55)
  smb_pwd_check_ntlmv1: incorrect password length (64)
[2008/02/19 17:21:51, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 17:21:51, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 17:21:51, 1] smbd/service.c:make_connection_snum(1033)
  tui (192.168.1.2) connect to service Music initially as user nobody (uid=6553$[/FONT]

Any help?

---

### Post by wahr on 2008-02-19
I hope someone helps you on this, this is in my interest.

does samba by chance only use the "everyone" permissions?

---

### Post by jhetrick62 on 2008-02-19
Ok, first, I don't believe that you can have the permissions on /home/music, /home/pictures and /home/transfer set to be owned by root with a group of root.  As your only write perms are for the owner of the directory and root owns the directory, loggin in as "ben" won't allow you to write to these.

Now you could change the folders to ben:ben for owner and group or you could change them to just ben as a group and then set the perms to be rwxrwxr_x (0775) and that MIGHT work for you.  I usually don't leave root as an owner of any shares that I want to write to.

Secondly, I never allow others to browse any shares that are underneath my /home/myuser directory.  That is just my preference though.  I always set pubic browsing up underneath /mnt or some other directory, although it will probably work for you.

Thirdly, you have all shares set up to "read only = yes" and you also have a write list for each.  I have never set mine up this way so I could be wrong, but I think those are contradictory statements and you may not be able to write to these shares even if all permissions are correct.  I believe that you need to delete the read only statement and add "writeable = yes".  The write list will limit the users that are able to write to the share.

Check to Man pages for smb.conf to be sure.

Goodluck,
Jeff

---

### Post by SumnerBoy on 2008-02-19
Jeff - thanks a million!! 

I did what you said (updated ownership on my shares to ben:ben and replaced the readonly flag with the writeable one) and it is now working as I wanted!!

I am new to Linux so am still getting to grips with permissions and mounts etc. Why do you not like having public shares under your user directory?

I have 2 logical partitions on my internal HDD - 20GB for the OS and the rest is partitioned off for my /home path.

Therefore I store all media (music and photos) in /home. Should I add mounts to this shares under /mnt/ and configure Samba to point to these? Any tips warmly received!

And thanks again for your prompt and very helpful response!

---

### Post by SumnerBoy on 2008-02-19
I am also still getting the following messages in my log...any ideas?

[FONT="Courier New"]  create_builtin_administrators: Failed to create Administrators
[2008/02/19 21:10:25, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 21:10:25, 1] smbd/service.c:make_connection_snum(1033)
  tui (192.168.1.2) connect to service Photos initially as user ben (uid=1000, $
[2008/02/19 21:10:47, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 21:10:47, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 21:10:47, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/02/19 21:10:47, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/02/19 21:10:47, 1] smbd/service.c:make_connection_snum(1033)
  tui (192.168.1.2) connect to service Transfer initially as user ben (uid=1000$[/FONT]

---

### Post by jhetrick62 on 2008-02-19
Ben,

It's probably just fine to share folders out of /home providing you don't ever allow the outside world access to that box!  My server occassionally is accessed from the outside world so I guard against hackinng on the ftp and ssh ports.  If anyone ever did get in, it's much more unlikely that they will get to /mnt as it is totally in a area where it's under root control and I don't allow any type of root login for ftp or ssh even with the proper password.

/home is reachable if someone ever hacked into a user's account so I don't want the off chance that they will get to any data.  That's all.  

If you arer only on the local network, it's no issue.

I'm not sure about the server logs.  Which log file are you finding them in.  I will take a look at my box, although I run a Redhat server so it's slightly as it's rpm based instead of deb based.  I use Ubuntu for my most recent workstation endeavors.

Glad it worked for you,
Jeff

---

### Post by SumnerBoy on 2008-02-19
Ok - so if I have all my shares under /mnt/ with root privileges, won't that prevent my samba links from giving my 'ben' logins write access to those folders? 

It seems that for me to be able to have write access through Samba for 'ben' then if someone hacks into my user account they will also have the same priveleges. 

Please correct me if I am wrong!

This box won't be accessible from outside my network (at the moment) but I would still like to set things up in a secure and sensible manner.

Those logs were found in /var/log/samba/log.<hostname>.

---

### Post by jhetrick62 on 2008-02-19
Ben,

You may be correct, I still have some testing to do on one share that isn't acting properly.  I really don't allow too many mounts that aren't user related honestly like you have a public viewed share.  I never really do that except for my music share and I am having a slight group write permission issue.  It allows me to write a directory or a file by any group member, but the directory will not get the group write permissions passed thus they can't put anything in that.  I only have this problem from my Ubuntu client, my FC6 client writes to the same share without an issue, go figure??

I'm not sure on the logs, hopefully someone else can help you as I don't have those types of entries, I just looked.

Jeff

---

