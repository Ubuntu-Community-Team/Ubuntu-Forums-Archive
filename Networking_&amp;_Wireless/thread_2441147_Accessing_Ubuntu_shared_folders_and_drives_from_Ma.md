---
title: "Accessing Ubuntu shared folders and drives from MacOS with NFS"
date: 2020-04-19
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2020-04-19
After having managed to setup a share on Ubuntu LTS 18.04 (using the GUI command "Local Network Share") and having found that shared folder by just browsing to the Ubuntu server machine on my Mac Min (running High Sierra), I was able to assess that I opened a Guest access on Ubuntu, yet the Guest access seemed to work - I was able to copy a file from my Mac to my Ubuntu, modify the file saved on Ubuntu using an app on my Mac... everything proved to work correctly.

Today I added 2 new USB drives, called Storage 1 and Storage 2. I tried sharing these the same way I did my Ubuntu Downloads folder. Didn't work at all. Somehow the Mac sees the name of the share being broadcast, but when I browse to the drive and double click to open, I get an error message on the Mac saying that I tried accessing the drive but it wasn't there anymore (well... close enough)

The username on my Mac is my full name. It's associated to my email address (as with most Apple products), but it's not using the same *USERNAME *as on my Ubuntu, hence the problem I believe. Should I try to create a new user on Ubuntu? What should I name it? how do I do this, from GUI or Terminal? Can anyone point to a step-by-step guide that has worked for you guys? 

I've looked in this forum AND I've scoured the web for this info, but everyone's got their own perspective on things. I can't find the proper info I'm looking for.

Pretty much, this is the lowdown: I run Ubuntu remotely. I have it hooked up to my TV but I access it through TeamViewer. I need to download files using my Mac, save the files on the Ubuntu, and run conversion jobs from the Mac on the files stored in Ubuntu (on the USB drives). So I know I need read-write permissions, but ownership is weird - I would need to have Ubuntu Share the ownership of all the files. Any way to set that up?

---

### Post by Morbius1 on 2020-04-20
> **couzin2000 said:**
> **[COLOR=#0000cd]After having managed to setup a share on Ubuntu LTS 18.04 (using the GUI  command "Local Network Share") [/COLOR]**and having found that shared folder by  just browsing to the Ubuntu server machine on my Mac Min (running High  Sierra),I was able to assess that I opened a Guest access on Ubuntu,  yet the Guest access seemed to work - **[COLOR=#0000cd]I was able to copy a file from my  Mac to my Ubuntu, modify the file saved on Ubuntu using an app on my  Mac... everything proved to work correctly[/COLOR].**

[COLOR=#0000cd]**Today I added 2 new USB drives, called Storage 1 and Storage 2. I tried  sharing these the same way I did my Ubuntu Downloads folder. Didn't work  at all.**[/COLOR] Somehow the Mac sees the name of the share being broadcast, but  when I browse to the drive and double click to open, I get an error  message on the Mac saying that I tried accessing the drive but it wasn't  there anymore (well... close enough) 
Open a terminal on the Ubuntu machine:

[1] Run this command:
```
whoami
```
[2] Edit a config file:
```
sudo -H gedit /etc/samba/smb.conf
```
[3] Right under the [highlight]workgroup = WORKGROUP[/highlight] line add the following:
```
force user = your-user-name
```
[COLOR=#ff0000] [I] Replace **your-user-name** with the result from step [1]

[/I][/COLOR]Then save the file.

[4] Restart a service:
```
sudo service smbd restart
```
Does your Mac connect to the usb shares?

If not On the Ubuntu machine please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by couzin2000 on 2020-04-20
Sorry... I'm not sure I follow. You're giving me instructions on how to adjust SMB server. I've not mentioned SMB ANYWHERE in my post - I'm trying to get my stuff to work over NFS.  Please try to help me out in the way I requested. I didn't ask for an alternative - I asked "how do I access Ubuntu shared folders and drives from MacOS with _NFS_?"
Thanks

---

### Post by Morbius1 on 2020-04-20
.

---

### Post by Morbius1 on 2020-04-20
> I've not mentioned SMB ANYWHERE in my post
Sure you did:

> **couzin2000 said:**
> After having managed to setup a share on Ubuntu LTS 18.04 ([COLOR=#0000cd]**using the GUI command "Local Network Share"**[/COLOR]) and having found that shared folder by just browsing to the Ubuntu server machine on my Mac Min (running High Sierra), I was able to assess that I opened a Guest access on Ubuntu, yet the Guest access seemed to work - I was able to copy a file from my Mac to my Ubuntu, modify the file saved on Ubuntu using an app on my Mac... everything proved to work correctly.
This is [B][COLOR=#0000cd]Local Network Share[/COLOR]:
[ATTACH=CONFIG]285568[/ATTACH]



[/B]That is Samba / SMB

Run the following command:
```
 net usershare info --long
```
Does it come back blank or does it list your SMB shares?

---

### Post by couzin2000 on 2020-04-21
Wait - not that I want to contradict you, but the built-in sharing process is SAMBA and not NFS? I thought NFS was the native networking protocol between Mac and Linux... am I wrong here?

---

### Post by Morbius1 on 2020-04-21
Short Answer: Yes

Long Answer:

The built in protocol - as in the samba client library allowing access to another hosts SMB shares and the ability to create a samba share for others to access - is already present in the Ubuntu file manager and has been for many many years.

If you look at the contents of /var/lib/samba/usershares you should see a file for every share you created via [COLOR=#0000cd]**Local Network Share**[/COLOR]. [highlight]net usershare info --long[/highlight] is an easy way to see how all of them are configured at once.

There is also cifs - as in mount.cifs - which can be used to mount a SMB share in a terminal or automatically in /etc/fstab. It's actually controlled by the Linux Kernel itself.

In this particular case once a samba share has been created it becomes visible to the MacOS client automatically in Finder due to Avahi in Linux. Avahi in MacOS is called Bonjour. And MacOS since Mavericks also uses Samba ( they call it SMBx ) by default.

---

### Post by TheFu on 2020-04-21
NFS is available, but it might be too much trouble from a Mac because of the different uids that OSX uses which begin at 500, not 1000, as they do in Ubuntu.  

NFS doesn't care about usernames.  it cares about the uid and gid - the numbers - as shown from the 'id' command on both platforms.  To my knowledge, there is no GUi method to connect unix systems with NFS.  There is an id-to-id mapping daemon, but I&#8217;ve never used it.  NFS storage would appear as native, local, disk storage once mounted.  it doesn't show up separately in file managers, for example.  i gave away my Mac years ago, so cannot test a setup, but NFS did work then after i changed the uid on Ubuntu to match and modified all the files owned by it.
```
man -k idmapd
idmapd.conf - configuration file for libnfsidmap
```

I&#8217;d probably use Samba unless one of the systems was brand new and there weren't many files on it already with the wrong uid/gid all over the place to be found and group/owner changed.

---

### Post by couzin2000 on 2020-04-22
So... This means my Ubuntu is already running *some* instance of Samba. And the reason why I can access it is because Windows 10 and MacOS can "see" a samba server and both access it it right out the box. 

(That means I installed NFS Client on my Win10 for nothing... ) 

SO to continue with the process of using my Mac and downloading files, then copying them over to the Ubuntu "server" I use, I have to configure Ubuntu the way Morbius suggested. 
So I'll try that and get back.
Thanks for setting me straight, I guess I was aware of a different reality!!

---

### Post by couzin2000 on 2020-04-22
Here's testparm -s:
```
couzin2000@SebUBServer1:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[sambashare]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	client min protocol = SMB3
	dns proxy = No
	log file = /var/log/samba/log.%m
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	syslog = 0
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb
	force user = couzin2000


[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[sambashare]
	browseable = No
	force create mode = 0660
	force directory mode = 02770
	path = /samba/sebshare
	read only = No
	valid users = sebshare @sadmin

```
And here's net usershare info --long:
```
couzin2000@SebUBServer1:~$ net usershare info --long
[Downloads]
path=/home/couzin2000/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Work - Copy]
path=/media/couzin2000/Storage 1/Work - Copy
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

I added /media/couzin2000/Storage1 and /media/couzin2000/Storage2. I can access them (rw) from my Mac.
Thank you for this, I would not have know where to start!

If I want to access these shares from my Windows 10 box, is it any different?
Looks like it works from there as well...

Awesome! Thanks a lot!

---

### Post by couzin2000 on 2020-06-11
Say... I just had a long-ass power outage, and now for some reason even though my Ubuntu server comes back up and I get the same output from tesparm -s and net userhare info --long, my Windows 10 machine won't let me enter. It keeps asking for credentials. even though I enter the username from my Ubuntu (couzin2000) and my full admin password, Windows is forbidden to access from its File Explorer. I've even gone as far as restarting samba as was stated above. 

What am I doing wrong here?

Is there something I haven't done on the ubuntu server to make these changes permanent?

EDIT: Ok, by changing the user name in the request to "guest" and leaving the password blank, I get access... but no way to use my admin pass.

---

### Post by Morbius1 on 2020-06-12
The only thing I can think of is that the samba password database has been corrupted somehow although I have never seen that happen. What you could try is:

** Remove yourself from the database:
```
sudo smbpasswd -x couzin2000
```
Then add yourself back:
```
sudo smbpasswd -a couzin2000
```

---

