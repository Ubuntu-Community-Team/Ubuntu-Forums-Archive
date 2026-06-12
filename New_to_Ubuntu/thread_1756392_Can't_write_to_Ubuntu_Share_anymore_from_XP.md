---
title: "Can't write to Ubuntu Share anymore from XP"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by jzli on 2011-05-12
Hello There!

I have a quite annoning problem: We have an Ubuntu PC running. Now i set up a shared folder that everyone from a Windows (XP) PC can connect to. It worked when I set it up. But now I cannot write anymore from Windows to this connected Network share. It says access denied, however, I can see the folder and I seem to have read permissions for the files.:(

Here's what I did:
[LIST]
[*]share the folder in Ubuntu
[*]create one new user with which everyone connects to this share
[*]map the network drive in Windows, copy stuff to this folder
[/LIST]

Note: when I connect with WinSCP with the same user I have no problem at all writing to this shared folder.

Has anyone experienced a similar problem? Or how would you set up a new share that can be mounted always as a Network Drive in Windows?

Many thanks for your suggestions in advance.

Best j

---

### Post by compmodder26 on 2011-05-12
Right click on the folder and select "Sharing Options".  In the dialog that shows up, is there a checkmark next to "Allow others to create and delete files in this folder"?

---

### Post by Morbius1 on 2011-05-12
An access is denied is a Linux permissions issue. What we don't know is how you created the Samba share. There are two methods one of which is the method compmodder26 posted ( called usershare ) which modifies linux permissions automatically if the shared folder is in a Linux filesystem ( ext3/4 ). What you don't want to do is use both methods at the same time. 

If you post the output of the following commands we can determine what method you are using:
```
net usershare info --long
``````
testparm -s
```Either way the only way a a remote guest who is not the owner of the shared directory can access the share is if you've done some creative permissions work or set the folder to 777.

---

### Post by jzli on 2011-05-12
Hi, thanks a lot for your answers!
If I rightclick the Folder, Folder Sharing is not even checked. It must have been done another way.

here are the outputs from:

net usershare info --long
```
[sfdocs]
path=/exports/home/SFdocs
comment=
usershare_acl=Everyone:R,
guest_ok=n
```

testparm -s
```
[global]
	workgroup = SANFRAN
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

And the folderpermissions look the following:
```
drwxr-xr-x  5 sanchez   sfgroup 4.0K 2011-05-12 13:22 SFdocs
```

where sanchez is the user with everyone should be able to connect to the folder.

Is there anything I made wrong with the whole Samba thing?
Many thanks again for your swift replies.

best j

---

### Post by Morbius1 on 2011-05-12
> If I rightclick the Folder, Folder Sharing is not even checked. It must have been done another way.No, you did do it that way because this is the share definition it created: 
> [sfdocs]
path=/exports/home/SFdocs
comment=
usershare_acl=Everyone:R,
guest_ok=nUnfortunately that specifies read only access to the share. Go back into nautilus and try it again. Then when you run "net usershare ... " again it will look like this:
> [sfdocs]
path=/exports/home/SFdocs
comment=
usershare_acl=Everyone:[COLOR=Blue]**F**[/COLOR],
guest_ok=n Of couse giving a remote user write access to the share doesn't mean you've given write access to the contents of the share ( i.e., editing a given file ) but that's another issue.

---

### Post by jzli on 2011-05-13
Hello!
Ok, id dit that again with Nautilus (as root of course).

Now its:

```

[sfdocs]
path=/exports/home/SFdocs
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

And it works, users can write to this folder again. Thank you very much!
I think this is how I set it up a long time ago and it worked as well, however after some weeks it stopped working and the ls output was very weird with some ?s in the permissions.
something like:
```
?????-??-?  5 sanchez   sfgroup
```
then we tried to fix the permissions, succeeded somehow but the share was gone.

Anyway, the folder is up again, no problems for now.

thank you all very much for the help!

Bests
j

---

