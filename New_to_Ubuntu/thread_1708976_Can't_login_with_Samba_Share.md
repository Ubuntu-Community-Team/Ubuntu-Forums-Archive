---
title: "Can't login with Samba Share"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by sderrick on 2011-03-17
I have two Unbuntu machines, one is 10.04 the other 10.10

I right clicked on my home folder in each machine, enabled sharing.

Gave each a share name, I did not enable guest access.  

I can see each machine and share from the other machine.

When I click on the share it asks for a user/password,  I typed in my user name and password(for the share machine) but it won't accept it.  I don't see any indication of an error except it clears out the password box when I press the Connect button. :(

If I enable guest access I can access the directory fine?  :o

What am I doing wrong?

thanks,  Scott

---

### Post by Morbius1 on 2011-03-17
> **sderrick said:**
> I have two Unbuntu machines, one is 10.04 the other 10.10

I right clicked on my home folder in each machine, enabled sharing.

Gave each a share name, I did not enable guest access.  

I can see each machine and share from the other machine.

When I click on the share it asks for a user/password,  [COLOR=Blue]I typed in my user name and password(for the share machine) but it won't accept it[/COLOR].  I don't see any indication of an error except it clears out the password box when I press the Connect button. :(

If I enable guest access I can access the directory fine?  :o

What am I doing wrong?

thanks,  Scott

2 different passwords in two different databases. If you actually want to use the name and password for the share machine to gain access then you need to let Samba know that:
```
sudo smbpasswd -a morbius
```Changing morbius to your own username.

---

### Post by sderrick on 2011-03-17
> **Morbius1 said:**
> 2 different passwords in two different databases. If you actually want to use the name and password for the share machine to gain access then you need to let Samba know that:
```
sudo smbpasswd -a morbius
```Changing morbius to your own username.

Its all setup to use PAM and I read that PAM will use an existing user account. That doesn't would work?

Your saying even though the smb.conf is set to use PAM authentication, thats broken?

I tried the "sudo smbpasswd -a myusername" command, 

after I enter the password, twice, for an already existing account(which seems stupid) 

it says "Failed to add entry for user myusername"

thanks,

Scott

---

### Post by pricetech on 2011-03-17
Using the smbpasswd command, even on an existing account, is a workaround for a bug that sometimes crops up with Samba.

I don't know why you're getting that error though. I've never seen it and have set up several Samba servers.

Not to change the subject, but have you considered using SSH to connect since you're sharing between Ubuntu boxen ??

---

### Post by sderrick on 2011-03-17
> **pricetech said:**
> 
Not to change the subject, but have you considered using SSH to connect since you're sharing between Ubuntu boxen ??

No I hadn't.  I just wanted to use nautilus to drag stuff back and forth. Is it possible to setup SSH to do that?  :rolleyes:

---

### Post by Morbius1 on 2011-03-18
It's easy enough to reproduce your smbpasswd error message:
> sudo smbpasswd -a phil
[sudo] password for morbius: 
New SMB password:
Retype new SMB password:
Failed to add entry for user phil.Got that error because there is no phil.

Make sure your username is spelled correctly, with the right case, and that "phil" has an actual account on your server.

[COLOR=Blue]**EDIT:**[/COLOR] You references to PAM have me a little confused. Did you do something specifically to your smb.conf or are you referring to the default PAM entries in smb.conf?

It's true that in 10.10 something was added to the default install: libpam-smbpass. It will by default create an smbpasswd which matches the login password for the local accounts. It's a very bad idea in my opinion and I uninstall it. It's a solution in search of a problem. But that package is not installed in 10.04 so you will have to add the smbpasswd manually. Not sure if that's what you are referring to.

---

### Post by sderrick on 2011-03-18
> **Morbius1 said:**
> It's easy enough to reproduce your smbpasswd error message:
Got that error because there is no phil.

Make sure your username is spelled correctly, with the right case, and that "phil" has an actual account on your server.


Both machines have one account which is the name I used with smbpasswd.  It fails.. :frown:

I tried creating a separate user "smbuser" just for smb connection, it failed too.   :frown:

---

### Post by pricetech on 2011-03-18
> **sderrick said:**
> I just wanted to use nautilus to drag stuff back and forth. Is it possible to setup SSH to do that?  :rolleyes:

Yes.

Places - Connect to Server
Choose SSH as your connection type
Fill in the IP and Port Number, username, etc.
You can even add a bookmark for it.
Browse just like you would any other folder.

---

### Post by Morbius1 on 2011-03-18
And if you are still interesting in Samba you might want to post the output of the following command:
```
testparm -s
```> I tried creating a separate user "smbuser" just for smb connection, it failed tooPost the output of this command as well:
```
sudo smbpasswd -D6 -a smbuser
```

---

### Post by sderrick on 2011-03-18
> **pricetech said:**
> Yes.

Places - Connect to Server
Choose SSH as your connection type
Fill in the IP and Port Number, username, etc.
You can even add a bookmark for it.
Browse just like you would any other folder.

Excellent! I'm doing a 30Gb copy using ftp right now, soon as that finishes I will set that up! 

thanks,

Scott

---

### Post by sderrick on 2011-03-18
> **Morbius1 said:**
> And if you are still interesting in Samba you might want to post the output of the following command:
```
testparm -s
```Post the output of this command as well:
```
sudo smbpasswd -D6 -a smbuser
```

Ok

```

sd@sd-laptop:~$ testparm -s
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

I'm not sure but it looks like this may have succeeded?
```

sudo smbpasswd -D6 -a smb_user
[sudo] password for sd: 
Netbios name list:-
my_netbios_names[0]="SD-LAPTOP"
Attempting to register passdb backend ldapsam
Successfully added passdb backend 'ldapsam'
Attempting to register passdb backend ldapsam_compat
Successfully added passdb backend 'ldapsam_compat'
Attempting to register passdb backend NDS_ldapsam
Successfully added passdb backend 'NDS_ldapsam'
Attempting to register passdb backend NDS_ldapsam_compat
Successfully added passdb backend 'NDS_ldapsam_compat'
Attempting to register passdb backend smbpasswd
Successfully added passdb backend 'smbpasswd'
Attempting to register passdb backend tdbsam
Successfully added passdb backend 'tdbsam'
Attempting to register passdb backend wbc_sam
Successfully added passdb backend 'wbc_sam'
Attempting to find a passdb backend to match tdbsam (tdbsam)
Found pdb backend tdbsam
pdb backend tdbsam has a valid init
New SMB password:
Retype new SMB password:
tdbsam_open: successfully opened /var/lib/samba/passdb.tdb
pdb_getsampwnam (TDB): error fetching database.
 Key: USER_smb_user
Finding user smb_user
Trying _Get_Pwnam(), username as lowercase is smb_user
Get_Pwnam_internals did find user [smb_user]!
Home server: sd-laptop
Home server: sd-laptop
lookup_global_sam_rid: looking up RID 1000.
pdb_getsampwrid (TDB): error looking up RID 1000 by key RID_000003e8.
Opening cache file at /var/run/samba/gencache.tdb
gid_to_sid: winbind failed to find a sid for gid 1000
Storing (new) account smb_user with RID 1000
Home server: sd-laptop
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Home server: sd-laptop
Finding user smb_user
Trying _Get_Pwnam(), username as lowercase is smb_user
Get_Pwnam_internals did find user [smb_user]!
Home server: sd-laptop
Home server: sd-laptop
lookup_global_sam_rid: looking up RID 513.
pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201.
Can't find a unix id for an unmapped group
Home server: sd-laptop
Home server: sd-laptop
Storing account smb_user with RID 1000
Added user smb_user.

```

---

### Post by Morbius1 on 2011-03-19
> **sderrick said:**
> I'm not sure but it looks like this may have succeeded?
> 
Added user smb_user.
It seems to be going through a few more steps then I'm used to seeing but it does appear to have successfully added smb_user.

---

### Post by rawlinc on 2013-03-10
I had the same issue with not being able to log into an smb share on Ubuntu 12.10. In my case, I had only installed the ***samba*** package. Once I installed ***libpam-smbpass*** in addtion to the ***samba*** package everything worked as expected.

---

