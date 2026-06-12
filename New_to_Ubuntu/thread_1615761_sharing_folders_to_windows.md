---
title: "sharing folders to windows?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by dbowlin17 on 2010-11-07
I am trying to share a folder to windows xp. I have sharing set up. the windows computer can see the folder but not access anything inside... help!! (i am running 10.10 on the desktop)

---

### Post by sikander3786 on 2010-11-07
How are you trying to share it? Via samba? If so please post your samba config file so we can have a look at it.

When you try to access does it ask for password? Or if it just throws an error, please list that.

Do you want to enable guest access to shares?

---

### Post by P4man on 2010-11-07
windows will likely prompt for username and password if you havent enabled guest access. provide the credentials for your ubuntu account and it should work.

---

### Post by dbowlin17 on 2010-11-07
I have tried using samba. I enabled guest access. Windows told me that I did not have permissions to access anything inside the folders. How do I get my samba configuration?

---

### Post by P4man on 2010-11-07
Is the folder you are trying to share on an NTFS partition ? If it is, you wont be able to share it unless you mount it in fstab I think

---

### Post by dbowlin17 on 2010-11-07
I have one partition on my desktop. it is ext4. i have my laptop on windows with ntfs. i am trying to use the windows machine to access and copy files to the laptop.

---

### Post by Morbius1 on 2010-11-07
Can we go back to sikander3786's suggestion and find out what's going on instead of just guessing. Please post the output of the following commands:
```
net usershare info --long
``````
testparm -s
```This will tell us what method of samba sharing you are using and how you are using it.

---

### Post by dbowlin17 on 2010-11-07
[emily's m]
path=/home/tim/Emily's Music
comment=
usershare_acl=Everyone:F,
guest_ok=y



Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by Morbius1 on 2010-11-07
There's actually not one thing wrong with any of that.

Please post the output of one more command please:
```
ls -al /home/tim/"Emily's Music"
```

If that directory holds a lot of files just post the first 10 lines or so.

---

### Post by dbowlin17 on 2010-11-07
total 32
drwxr-xr-x  8 tim tim 4096 2010-11-07 10:02 .
drwxr-xr-x 39 tim tim 4096 2010-11-07 18:05 ..
drwx------  3 tim tim 4096 2010-10-25 18:03 Coldplay
drwx------  6 tim tim 4096 2010-10-25 18:01 Ingrid Michaelson
drwx------  2 tim tim 4096 2010-10-25 18:01 Michael Buble - Crazy Love
drwx------  2 tim tim 4096 2010-10-25 18:00 Norah Jones
drwx------  2 tim tim 4096 2010-10-25 17:57 Train - Save Me San Francisco
drwx------  2 tim tim 4096 2010-10-25 17:57 Tyrone Wells - Hold On

---

### Post by Morbius1 on 2010-11-07
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = tim
```Save smb.conf and back in the terminal restart samba:
```
sudo service smbd restart
```The only person that can access those files is "tim". You can set samba to allow guest access and it will but it has no authority over linux file permissions. "force user" will make the remote user appear to be you - at least as far as that share is concerned.

"I've got to shut down for the day. I'm fairly certain this will work.

---

### Post by dbowlin17 on 2010-11-08
WORKS! THANKS! now how do i mark this thread solved?

---

