---
title: "Samba problems ins 14.04"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2016-05-03
Want to make a folder visible on home wifi network.  Installed samba, followed steps in this demonstration:

[https://www.youtube.com/watch?v=-wUfzdiE4m8]("https://www.youtube.com/watch?v=-wUfzdiE4m8")

Never could see the folder from a windows  10 machine on the same network, and then samba stopped working:

> owner@WORKHOUSE:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.
owner@WORKHOUSE:~$ 

Is the line "security = share" the culprit (in /etc/samba/smb.conf)?

Tried to share a folder on a separate drive (not in /home/owner), does the shared folder need to be in /home/owner for this to work?

My wifi network has been working smoothly for some months, no difficulties there.

Struggled for several days to figure this out, have come to the conclusion that Ubuntu desktop is not the way to share a folder.  If I install Ubuntu server can these problems be surmounted?

---

### Post by Morbius1 on 2016-05-03
[1] This is just a recommendation but there are only about 4 people ( at the moment ) in this forum that know anything about Samba and none of them will watch a video to find out how you configured it. 

[2] The latest release of samba introduced a number of bugs that are being fixed and a new release in imminent. Well ... samba has a new release that they say fixed the 30 or so bugs it introduced in it's last release. When it will filter down to Ubuntu is unknown.

[3] Yes, "security = share" is a problem and was introduced by the last release referenced in [2]. Maybe. Share level security was deprecated years ... years ago ... so maybe Samba is just getting Medieval on the whole subject. Just edit smb.conf and remove the line referencing it and restart the samba services. And don't select that option in system-config-samba which is usually the application that put it there ... unless your video suggested it.

---

### Post by raymondvillain on 2016-05-03
Thank you, Morbius1.  If Samba is not so popular, what are folks using to make shares visible on small networks?  There must be another route.

I will work with editing the smb.conf file.

Thanks again for your info.

---

### Post by Morbius1 on 2016-05-03
You misinterpreted my "only 4 people" comment. There are only about 4 people who actually know anything about samba in this forum. There are 18642 members who think they do.

Samba is common on all operating systems today - Windows, OSX for which it is the default now - by another name, and Linux. It's not that it's not popular it's just that it's made way ... way ... more difficult by bad HowTo's and buggy updates like the last one.

If you are still having issues after removing "security = share" from smb.conf please post the output of the following commands so the folks here can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```
In the mean time Win10 has joined the other operating systems in that it can use mDNS to identify a host but you have to connect to the machine explicitly. So open Run ( Win Key + r ) and address the Linux machine by name with a ".local attached to the end of it:
```
\\workhouse.local
```

---

### Post by raymondvillain on 2016-05-03
Here goes:

> testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[4android]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	workgroup = WORKBENCH
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	security = USER
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = sambaguest
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[4android]
	path = /media/daddy/ext4_strg/4android
	read only = No

> net usershare info --long
mkdir failed on directory /var/run/samba/msg.lock: Permission denied
[4android]
path=/media/daddy/ext4_strg/4android
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/lnxdsk is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/android sharing is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[DIXIE_disk]
path=/media/daddy/NTFS storage1/DIXIE_disk
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y


hope this helps, beginning to think I need to have the shared folder in my /home directory, presently trying to use a directory on a separate hard drive that is not mounted at startup.

Thanks again for your help.

---

### Post by Morbius1 on 2016-05-03
Some observations:

[1] You are using two different methods to share the same folder at the same time. They are both Samba shares but created two different ways:

This is a Samba Usershare - created through the file manager:
> [4android]
path=/media/daddy/ext4_strg/4android
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y
This is a classic share - created within smb.conf itself:
> [4android]
    path = /media/daddy/ext4_strg/4android
    read only = No                      
guest ok = Yes [COLOR=#0000cd]<-- pulled in from the [global] section[/COLOR]

At the moment they are both guest accessible + writeable shares but you can see where this might get out of sync if you forget what you've done.  Best to choose one method or the other - on the same folder.

[2] But the biggest issue is your paths. They are both of the form:
> path=/media/daddy/XXXX
I presume that "daddy" is your user name and that's the problem.

Linux creates the /media/daddy folder by itself and when it does that it sets an access control list ( acl ) on that folder that allows only "daddy" to get past it. The samba "guest" user is not "daddy" so to that user the share exist but the /ext4_strg/4android and the /NTFS storage1/DIXIE_disk folders do not. You will get a "path not found" or something equivalent on the client when you try to access it.

One method - and this is certainly not the the only method - is to add a line in smb.conf: Place it under your workgroup = WORKBENCH" line:
```
force user = daddy
```
Then restart smbd:
```
sudo service smbd restart
```

When the samba client guest user connects to your samba shares he will be doing so as "daddy". This is restricted only to your shares of course not your whole box.

---

### Post by raymondvillain on 2016-05-04
Will have to rethink my plan.  Had no idea I was creating such a can of worms.

Can you recommend a hardcover book that has introductory level info on networking and file sharing in Ubuntu or Linux?

Thanks very much for your time and advice.

---

### Post by Morbius1 on 2016-05-04
All the books on Samba became outdated about 6 years ago.

What's the issue with the recommendations I gave above?

---

### Post by raymondvillain on 2016-05-04
added "force user = daddy" to smb.conf

testparm doesn't say anything is wrong

But I am confused, if I browse the network from nautilus, the windows network icon (in nautilus, on the Ubuntu machine) shows only the windows computer and not the folder on Ubuntu that I had hoped to share. 

On the windows computer, browsing the network icon (from windows file explorer) doesn't show the ubuntu machine at all, also doesn't show the folder I want to be able to see from the windows computer.

output of testparm -s:
> daddy@DIXIE:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[4android]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	workgroup = WORKBENCH
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	security = USER
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	force user = daddy


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[4android]
	path = /media/daddy/ext4_strg/4android
	read only = No
	guest ok = Yes
daddy@DIXIE:~$ 


output of net usershare info --long:

> [4android]
path=/media/daddy/ext4_strg/4android
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/lnxdsk is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/android sharing is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[DIXIE_disk]
path=/media/daddy/NTFS storage1/DIXIE_disk
comment=
usershare_acl=S-1-1-0:F,
guest_ok=y

daddy@DIXIE:~$ 

---

### Post by Morbius1 on 2016-05-05
On the Linux machine:
[1] Disable your firewall:
```
sudo ufw disable
```
[2] Edit smb.conf again and add this line right under your "force user = daddy" line:
```
name resolve order = bcast host lmhosts wins
```
[3] Then restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Now go make a nice pot of tea because Windows takes a bit to get over nmbd restarting before it comes to it's senses.

And remember there is a new way for Windows to address Linux / OSX shares. On Windows 10:

Open explorer and specify the Linux machine by name ( \\dixie.local ) - and don't forget the .local at the end - like I did on my own network: [ATTACH=CONFIG]268861[/ATTACH]

---

### Post by raymondvillain on 2016-05-05
May have solved it.  After reboot, things are much better.

Created a 2nd folder "pixbucket" to be shared on local network, this one is in my home folder (/home/daddy/pixbucket) and at least it is visible from the windows computer, but I can't write to it, says I need permission.

Still have to figure that out.

---

### Post by raymondvillain on 2016-05-05
Windows sees the folder but says I need permission to copy a file into it.

Do I use the samba GUI (Samba Server Configuration tool) to add a user?  It asks for windows  user name and password.

Was hoping to have the folder accessible by anyone on my local network.

Thanks again for your time.

P. S.  I did use \\DIXIE.local in windows file explorer, it does work, thanks for the tip.

---

### Post by Morbius1 on 2016-05-05
"force user = daddy" is making the remote user appear to be daddy and since you are sharing a folder in daddy's home folder you should have no permissions issues.

The only way for me to figure out what's going on is for you to post the output of these commands again:
```
testparm -s
```
```
net usershare info --long
```
```
ls -al /home/daddy/pixbucket
```

---

### Post by raymondvillain on 2016-05-05
O. K., here goes:

> daddy@DIXIE:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[4android]"
Processing section "[pixbucket]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	workgroup = WORKBENCH
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	security = USER
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	force user = daddy


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[4android]
	path = /media/daddy/ext4_strg/4android
	read only = No
	guest ok = Yes


[pixbucket]
	comment = pictures from phones
	path = /home/daddy/pixbucket
	read only = No
	guest ok = Yes
daddy@DIXIE:~$ 


> daddy@DIXIE:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/4android is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/lnxdsk is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/android sharing is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[DIXIE_disk]
path=/media/daddy/NTFS storage1/DIXIE_disk
comment=
usershare_acl=Everyone:F,
guest_ok=y


> daddy@DIXIE:~$ ls -al /home/daddy/pixbucket
total 8
drwxr-xr-x  2 root  root  4096 May  4 22:35 .
drwxr-xr-x 35 daddy daddy 4096 May  5 06:44 ..


Have to go to work, may not get back to this for a few hours, but many many thanks for your expertise!

---

### Post by Morbius1 on 2016-05-05
> daddy@DIXIE:~$ ls -al /home/daddy/pixbucket
total 8
**[COLOR=#0000cd]drwxr-xr-x[/COLOR]**  2 [COLOR=#0000cd]**root  root**[/COLOR]  4096 May  4 22:35 .
drwxr-xr-x 35 daddy daddy 4096 May  5 06:44 ..                      

The line with the ".." at the end represents your home folder: /home/daddy
The line with the "." at the end represents the pixbucket folder.

That folder is owned by root ( [COLOR=#0000cd]**root  root ) **[/COLOR]with read / write access to root ( [COLOR=#0000cd]**rwx**[/COLOR] ) but with read only access to everyone else ( [COLOR=#0000cd]**r-xr-x**[/COLOR] ). Notice there are no "w"'s in there.

In order for your share to work with the way it's configured you need to change ownership of that folder so that it's owned by "daddy":
```
sudo chown daddy:daddy /home/daddy/pixbucket
```

---

### Post by raymondvillain on 2016-05-05
Magic!  Can see both shares from windows computer, but I have to remember to manually mount the hard drive containing folder 4android.

Tried to add a line to fstab so that this drive would mount at startup:
#UUID=5ce8c556-a4f5-4756-a9fd-b912ac70fc0f /media/daddy    ext4  user, fmask=0111, dmask=0000  0  0

but it would not mount the folder as desired.  Found UUID by typing "sudo blkid" at the command prompt.

---

### Post by Morbius1 on 2016-05-05
>  #UUID=5ce8c556-a4f5-4756-a9fd-b912ac70fc0f /media/daddy    ext4  user, fmask=0111, dmask=0000  0  0
There's a number of problems with that line.

*** You don't want to mount a partition to /media/daddy since the system created that folder.  Make it something else like Ext4Disk:
```
sudo mkdir /media/Ext4Disk
```
*** fmask and dmask are for ntfs partitions. Those mean nothing in fstab for ext4 partitions.

So the line should look something like this:
```
UUID=5ce8c556-a4f5-4756-a9fd-b912ac70fc0f /media/Ext4Disk    ext4  defaults 0  0
```

And of course you will need to change the path in smb.conf  for that share on this partition.

---

### Post by raymondvillain on 2016-05-05
Yes, of course, and after doing so all is well, I can see both folders from the windows machine, and even from the app "ES File Explorer" on android phone, a big plus.  Thanks ever so much for your great help.  I'm marking this solved.

---

### Post by lehmanndr on 2016-05-22
> **Morbius1 said:**
> [1] This is just a recommendation but there are only about 4 people ( at the moment ) in this forum that know anything about Samba and none of them will watch a video to find out how you configured it. 

[2] The latest release of samba introduced a number of bugs that are being fixed and a new release in imminent. Well ... samba has a new release that they say fixed the 30 or so bugs it introduced in it's last release. When it will filter down to Ubuntu is unknown.

[3] Yes, "security = share" is a problem and was introduced by the last release referenced in [2]. Maybe. Share level security was deprecated years ... years ago ... so maybe Samba is just getting Medieval on the whole subject. Just edit smb.conf and remove the line referencing it and restart the samba services. And don't select that option in system-config-samba which is usually the application that put it there ... unless your video suggested it.

 I was having huge problems after recent samba update and this saved me - thanks! And I like the classic "Ubuntu pro" type 'tude in your response, too!

---

### Post by AnrDaemon on 2016-06-28
> **raymondvillain said:**
> rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)

There's an extremely easy way to get rid of this particular "problem".
Stop using testparm. Use samba-tool.
```
samba-tool testparm --suppress-prompt
```

---

