---
title: "Windows 7 can see shared folder, but can't get in"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by JWWWONKO on 2010-06-16
I tried Ubuntu a couple of years back and I am just trying to get back into it now.  I am as NOVICE and NEWBIE as they come.  I installed the latest on a P4 machine and it seems to run great.  I think I added all of the Samba bits and pieces so I can add this PC to my windows home network.  When I am on the windows machine, I can see the UBUNTU computer.  I click that and I can see all of the folders that I shared.  But if I try to open any of those folders, I get this;
"WINDOWS CANNOT ACCESS \\Ubuntu\My Music"

I can ping each computer from the other, the UBUNTU machine is connected wirelessly to the router and the Windows is wired.  I have read many suggestions from various sources, but I am not sure why I cant access my files.  I have adjusted permission and passwords, regedits, new Ubuntu users, and more.

What is the best course of action to see why these computers wont share nice?

Any help would be appreciated, thanks!

---

### Post by spiky001 on 2010-06-16
Hi I think the problem is with the file ext on Ubuntu I dont think windows can read ext4 or ext 3 not 100% if i,m wrong some1 point it out, I think you should make the partition ntfs

---

### Post by Locke_99GS on 2010-06-16
Possibly mismatched usernames or smb password isn't in sync with user password.

See here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

edit: spiky001; Samba doesn't care much about the filesystem. SMB is a protocol for sending data over a network. So long as both sides can understand the protocol, the data will make it through.

---

### Post by Morbius1 on 2010-06-16
Post the output of the following commands so everyone can see what's up:

```
net usershare info
sudo net usershare info
testparm -s
```Also this one:
```
ls -dl /path-to-the-My-Music-directory
```For example if "My Music" is in the /media directory the command would be:
```
ls -dl /media/"My Music"
```

---

### Post by JWWWONKO on 2010-06-16
net usershare info

[disk2_vol1]
path=/media/DISK2_VOL1
comment=
usershare_acl=Everyone:F,
guest_ok=y

[my documents]
path=/media/DISK2_VOL1/Documents and Settings/Johnny/My Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[my music]
path=/media/DISK2_VOL1/Documents and Settings/Johnny/My Documents/My Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[dox]
path=/media/DISK2_VOL1/Documents and Settings
comment=
usershare_acl=Everyone:F,
guest_ok=n

[johnny]
path=/media/DISK2_VOL1/Documents and Settings/Johnny
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by JWWWONKO on 2010-06-16
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: wins
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = 
	map to guest = Bad User
	null passwords = Yes
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	os level = 33
	wins support = Yes
	usershare allow guests = Yes
	usershare owner only = No

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[MyFiles]
	path = /media/samba/
	force user = YOUR_USERNAME
	force group = YOUR_USERGROUP
	read only = No
	create mask = 0644

---

### Post by JWWWONKO on 2010-06-16
All of the files that I want to access from the Windows machine are on the Ubuntu Machine Disk2_Vol1 which is mounted and it is NTFS

---

### Post by Morbius1 on 2010-06-16
Unfortunately I wasn't smart enough to ask you how you're mounting /media/DISK2_VOL1. This is one of those situations where it does matter how the filesystem is formatted.

This is most likely an NTFS partition and I'm going to assume ( and tell me if I'm wrong ) that you are mounting it through Nautilus or from "Places". If so then it will mount with you as owner and permissions set to 0700. You can read and write to the partitions (7) but no one else can (0).

Since you're mostly using Nautilus-share you can easily work around this problem by adding one line to the **[COLOR=Blue][global][/COLOR]** section of smb.conf:
```
force user = mobius1
```[COLOR=Blue]*Change morbius1 to you own login username. No need to create a samba user.*[/COLOR]

Then restart Samba:
```
sudo service smbd restart
```You have other problems as well:
The following nautilus-share does not allow guests but all the child folder allow guests. This will not work. So you need to go back into nautilus and unshare /media/DISK2_VOL1/Documents and Settings
> 
[dox]
path=/media/DISK2_VOL1/Documents and Settings
comment=
usershare_acl=Everyone:F,
guest_ok=nAlso, the following Classic-share will never work unless you're hiding your real force user name but it's not interfering with the Nautilus-share so just leave it alone for now:
> [MyFiles]
    path = /media/samba/
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
    read only = No
    create mask = 0644

---

### Post by JWWWONKO on 2010-06-16
Thats it!  Thank you Morbius1
It works like a charm and I really appreciate your quick reply and precise directions!  
I am sure I will have more questions as I explore further.

Thanks Again

---

### Post by pepseeh on 2010-07-08
I hate to bump this thread but I'm having the same problem. Like JWWWONKO I am still a noob to all of this, I've done everything and every tip I could find on Google, and I'm kinda losing my patience here.

I'm running Kubuntu 9.10, and like the original problem, I can see this Kubuntu laptop on Windows, but I can't access it. It's also worth nothing that only one Windows 7 computer can see the Kubuntu laptop, but the others can't, and that I couldn't see my Windows computers from Kubuntu. Well, last night the Windows PC showed up on Kubuntu (specifically the workgroup folder), but I also couldn't access it, and now this morning it's nowhere to be found.

I tried what Morbius suggested, but to no avail.

This is what shows up from the testparm command (apparently nothing happens when I type in net usershare info):

rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"                                  
Processing section "[print$]"                                    
Processing section "[RO_PUBLIC]"                                 
Processing section "[test]"                                      
Loaded services file OK.                                         
Server role: ROLE_STANDALONE                                     
[global]                                                         
        workgroup = MORAN                                        
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
        force user = ro

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

[RO_PUBLIC]
        comment = /home/ro/Public
        path = /home/ro/Public
        read only = No
        guest ok = Yes
        wide links = No

[test]
        path = /home/ro/test
        valid users = ro
        read only = No
        guest ok = Yes


I would really appreciate help on this.

---

