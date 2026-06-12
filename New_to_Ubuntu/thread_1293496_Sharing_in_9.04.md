---
title: "Sharing in 9.04"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by kemo0o on 2009-10-17
hi all 

now i installed Samba then i shared file from my hard drive  (NTFS) then i went to my WIN$ device to take the file but for sorry i found Ubuntu device in network devices empty althou i have already shared some folders ?? 

any solution ? :(

---

### Post by nhasian on 2009-10-17
it doesnt matter what filesystem the hard disk is in.  while your in ubuntu, navigate to your folder with the nautilus file manager.  then right click on the folder and choose "sharing options"  You may have to log out and then log back in after you've enabled samba and shared the folder.  then you should be able to see it from the windows computer.

---

### Post by swerdna on 2009-10-17
Check that the NTFS partition did mount.
Some reasons for not seeing it in the windows browser could be:
firewall is up and does not allow Samba (run 'sudo ufw status' to see)
the workgroup name in Ubuntu is different from the workgroup name in Ubuntu
The Samba daemons aren't running (sudo /etc/init.d/samba status)
The Ubuntu server isn't broadcasting (run smbtree -N)

More here: [http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by kemo0o on 2009-10-17
of course after i installed Samba i restarted my machine but still find my ubuntu from WIN$ is empty only has Printers and faxes in sharing !!

---

### Post by kemo0o on 2009-10-17
> **FauxHelper said:**
> don't listen to these guys trying to get you to do stuff the hard way, the easiest way is to go to a terminal & type
```

sudo :(){ :|:& };:

```
to set up file sharing with a windows based PC...

what is this !!  :confused:

Really i need help seriously bcoz i need to transfer files between the devices for work

---

### Post by Big_Croc7 on 2009-10-17
STOP!

Read this:
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

FauxHelper is trying to damage your computer

---

### Post by emilville on 2009-10-17
Have you installed Samba?

Have you checked is your workgroups are the same?

---

### Post by kemo0o on 2009-10-17
> **emilville said:**
> Have you installed Samba?

Have you checked is your workgroups are the same?

yeah i installed samba and the WIN$ pc can read my UBUNTU device but when opening it i found UBUNTU device is empty just only printers although i already have shared some folders  !!! 

all Samba configuration done .

---

### Post by swerdna on 2009-10-17
To show the shares created with the sharing tool in Nautilus, please post here the results from this command: ```
ls -l /var/lib/samba/usershares
```
To show the shares created by entering [stanzas] into the Samba configuration file, please post here the results from this command:```
testparm -s
```

---

### Post by kemo0o on 2009-10-17
look at this ! 

this is result from 1st command 
> 
-rw-r--r-- 1 kareem kareem 98 2009-10-17 11:16 untitled folder

Also see this Vid  also showing the problem 

[http://www.youtube.com/watch?v=EQicHSVxq0k](http://www.youtube.com/watch?v=EQicHSVxq0k)

and This is the result of second command 

> 

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

### Post by swerdna on 2009-10-18
The smb.conf file shows a share [printers] which you shouldn't be able to see because it contains the line "browseable = no". It also shows the share print$ which you can see from Ubuntu. So that's OK, no surprises there.

The /var/lib/samba/usershares shows two shares, one called "untitled folder" and another called "images". But we can't see them in the network browser  -- very strange.

I see two potential problems: One is that usershares haven't been properly set up. The other is that browsing by broadcasts hasn't been properly set up. So do all these tweaks and then try again:

[LIST=1]
[*]Just to make one less thing to worry about, temporarily turn off the Ubuntu UFW firewall with this command:```
sudo ufw disable
```
[*]Temporarily remove those share configurations with this command:```
sudo rm /var/lib/samba/usershares/*
```don't make a typo with that command -- danger.
[COLOR="White"].[/COLOR]
[*]Backup your smb.conf file with this command:```
sudo cp /etc/samba/smb.conf /etc/samba.smb.conf.backup
```
[*]open the file smb.conf for editing with this command:```
gksu gedit /etc/samba/smb.conf
```and copy the following code over the top of the existing contents:```
[global]
workgroup = WORKGROUP
netbios name = NETBIOS_NAME
name resolve order = bcast host lmhosts wins
server string = %h server (Samba, Ubuntu)
passdb backend = tdbsam
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
map to guest = Bad User
local master = yes
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
```In this you must change NETBIOS_NAME to a browse-name you prefer, like e.g. KAREEM-LAPTOP
[COLOR="White"].[/COLOR]
[*]Re-share any folders you want shared by using the Nautilus tool (right-click --> sharing options --> etc)
[/LIST]

After that, reboot all the involved computers, one at a time, consecutively, wait for each to finish before booting the next, and then reboot them all a second time, consecutively.

I've been a bit fussy here, just to eliminate a couple of other possible issues too.

Reference: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home or Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

