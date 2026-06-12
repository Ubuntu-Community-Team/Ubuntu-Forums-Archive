---
title: "Samba and mpeg sharing problem - very strange"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by castalla on 2011-04-27
I am using Linux Mint and Samba3 to share mpeg files to a media player.

I have encountered a very unique problem where the player fails to play a particular mpeg2 file.

The issue is that the player CAN play the same file if it is available via XP shares AND also via an android Samba share.

Additionally, the player can play an mpeg1 file from the linux Samba without any problems.

Has anybody any tips on how to investigate this further - it surely must be a Samba issue on the linux box ....????

---

### Post by MasterTech515 on 2011-04-27
> **castalla said:**
> I am using Linux Mint and Samba3 to share mpeg files to a media player.
  
Has anybody any tips on how to investigate this further - it surely must be a Samba issue on the linux box ....????
 
[SIZE=2]I would recommend recording the IP traffic between the two. Once recorded examine and check for obvious problems.
[/SIZE]

---

### Post by castalla on 2011-04-27
Thanks.  So, is there an easy way to do what you suggest?

---

### Post by castalla on 2011-04-27
Nothing .... ???

---

### Post by castalla on 2011-04-28
I have posted previously here with a very bizarre Samba share problem.  I received only one non-specific reply.

Can somebody advise the best sub-thread or even another forum were I might get some expert help ?

This is a very specific video stream problem and almost certainly the issue lies with samba.

here's the original post: [http://ubuntuforums.org/showthread.php?t=1740808&highlight=samba](http://ubuntuforums.org/showthread.php?t=1740808&highlight=samba)

---

### Post by collisionystm on 2011-04-28
Check your permissions on samba.

---

### Post by castalla on 2011-04-28
Thanks, but .... It's nothing to do with permissions as every other video in my shared folder plays - it's some weird interaction between linux converted video and samba - it has to be.

The linux converted file will not play - if I copy it to XP shares then it plays.
Windows converted videos copied to the linux share play without problem.

---

### Post by cariboo on 2011-04-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by castalla on 2011-04-28
Thanks - hopefully there'll be some more replies.

---

### Post by crispy_420 on 2011-04-28
I just want to see if I understand this correctly.

You have a share (samba) with a video file on it, right? 

If the file is made in Windows and put into the share it plays while a video made in Linux on the same share does not, right?

But if said Linux created file is moved to a Windows share it plays, right still?

If I have that timeline down correct I would be inclined to believe it is the share level permissions and not the video. A failed play on a Linux share and the Windows share would have me leaning toward bad file.

From the folder I assume you as a user have full rights and it is not through another account. Make sure you are owner of the files (chown) and make sure all users have read and execute, leaving write for local account (0755).

Sitting on my Windows box (sorry all) but the syntax should be something like this:

chown -R username foldername/
chmod -R 0755 foldername/

Please correct me if I'm wrong in syntax.

---

### Post by castalla on 2011-04-29
Thanks for the reply.

On reflection, I think you may be right about permissions.

The videos in Shared I copied over from Windows are owned by nobody nogroup.

A linux converted file is owned by mint mint.

I don't really understand the file/folder ownership commands - think I need further explanation -

Should they be:

chown -R mint Shared/
 chmod -R 0755 Shared/


Update: Update:  seems you were correct!!!  I've messed with permissions and ownership, and a 'dead' file now plays!   Thanks a lot for the solution.

---

### Post by castalla on 2011-04-29
Okay - I need help on setting the permissions.  

I created a converted file which is saved to Videos.  I am logged in as mint in Mint linux.  I copied the file to /home/mint/Shared - this folder has user nobody and group nobody access (set via nautilus shares).  The video still refuses to play.  

Can somebody please give me the exact chown and chmod commands I need to enable the file to be accessed via the media player?

---

### Post by castalla on 2011-04-30
A tale of woe goes on.

I now have been able to get a Transmaggedon converted file to play from the shared folder.   

However, the only way to do this is to expressly chmod 777 on the file.

Transmaggedon converts the file and saves it in Videos by default with restricted permissions.  Simply copying the file to Shared preserves the restricted permission, and hence the need to use chmod.

Is there a way for the permissions to be changed automagically when the file is copied?  I've got 'force create mode = 0777' in the smb.conf - doesn't seem to make any difference.

---

### Post by Morbius1 on 2011-05-01
On whatever machine that holds this share and the file you want to play post the output of the following commands:
```
testparm -s
net userhsre info --long
```

---

### Post by castalla on 2011-05-01
Here you go:

```
mint@mint ~/Desktop $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = %h server (Samba, LinuxMint)
	security = SHARE
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	path = /home/mint/Shared
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	create mask = 0700
	guest ok = No
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes
	guest ok = No

```

```
mint@mint ~/Desktop $ net usershare info --long
[videos]
path=/home/mint/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[music]
path=/home/mint/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[shared]
path=/home/mint/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

---

### Post by Morbius1 on 2011-05-01
So if I understand the problem correctly you can play the file on the box with the share but can't from the client box. 

If I have it right and since you have nothing but guest shares then add one line to the [global] section of smb.conf:
```
force user = mint
```Add it early in the [global] section - like under the workgroup line - because you have the /home/mint/Shared definition in the wrong place.
[COLOR=Blue][B]
EDIT:[/B][/COLOR] Sorry , then restart samba:
```
 sudo service smbd restart
```

---

### Post by castalla on 2011-05-01
Thanks ... I'll give it a try later today and report back.

---

### Post by castalla on 2011-05-01
Sadly, no luck.  Only doing chmod let's the player see and play the file:

```
mint@mint ~/Videos $ ls -l
total 8848
-rw-rw-rw- 1 mint mint 9042987 May  1 21:35 BBC_Weather_-_27_04_2011_b010r32t_default-213426-01052011.mpg
mint@mint ~/Videos $ ls -l
total 8848
-rwxrwxrwx 1 mint mint 9042987 May  1 21:35 BBC_Weather_-_27_04_2011_b010r32t_default-213426-01052011.mpg

```

First doesn't play ... second does.

---

