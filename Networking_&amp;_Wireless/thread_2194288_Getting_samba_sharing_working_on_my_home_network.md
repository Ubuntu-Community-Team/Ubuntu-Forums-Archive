---
title: "Getting samba sharing working on my home network"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by ratdog on 2013-12-17
Howdy Ubuntu gurus!

I've spent a few Sunday's trying to get my Ubuntu 12.04 home media server's sharing set up and my frustration is growing.  I need help.

I've installed samba and tried setting up sharing with nautilus and the system-config-samba GUI.  I've read several threads here and and have tried a few tutorials, most recently this one: [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba)

I am a networking novice and have gotten myself pretty confused.  The directory I want to share is on a second hard drive that I have gotten to mount automatically and I've changed permissions so that I am the owner and I believe everyone in my workgroup 'LIGHTPOOL' should be able to create and delete files.

I want to be able to access the shares from our 2 laptops (ubuntu 12.04 and ubuntu10.04/windows 7 dual boot).  

Here is the output of ```
testparm -s
```
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Media]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = LIGHTPOOL
	server string = %h homestead (Samba, Ubuntu)
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Media]
	comment = lightpool files on the server
	path = /media/sdb2/Media
	valid users = elysselightpool, lightpool, rashaanlightpool
	read only = No
```

I would love it if the share called Media would automatically show up on the laptops under network in Nautilus.

Thanks for your help

---

### Post by aromo2 on 2013-12-17
You could add "browseable = Yes" option and try smbclient to see if the share gets published:
```

smbclient -L your_smb_server -Ulightpool

```
Try nautilus if smbclient succeeds

---

### Post by ratdog on 2013-12-17
> **aromo2 said:**
> You could add "browseable = Yes" option and try smbclient to see if the share gets published:
```

smbclient -L your_smb_server -Ulightpool

```
Try nautilus if smbclient succeeds

Sorry, this novice needs some clarification...  

Did you want me to add "browseable = Yes" to the [global] section of my smb.conf file? What would this do for me?

In the smbclient command, what do I insert for your_smb_server? The IP address?

Thanks

---

### Post by Morbius1 on 2013-12-17
> I would love it if the share called Media would automatically show up on the laptops under network in Nautilus.
Run the following command from the laptop running Ubuntu:
```
nautilus smb://hostname.local/media
```
Replace "hostname" with the host name of your media server. Make sure the spelling matches the output of this command on that server:
```
hostname
```

If it gives you any error messages post them back to the forum.

---

### Post by ratdog on 2013-12-17
Yes, Nautilus gives me errors on the laptop:

Could not display "smb://entertainment-center.local/media/".
Error: Failed to mount windows share
Please select another viewer and try again.

---

### Post by Morbius1 on 2013-12-17
3 things:

[1] This is usually a permissions error not a samba error:
>  Error: Failed to mount windows share
What are the permissions of the target:
```
ls -al /media/sdb2
```

[2] For another Linux machine your host name is fine but for Windows to access it this name is too long:
> entertainment-center
Edit smb.conf directly and add a line under the workgoup line that looks like this:
```
netbios name = ent-center
```
[COLOR=#0000cd]*It doesn't have to be that exact name but it has to be 15 characters or less in length.*[/COLOR]

[COLOR=#0000cd] **EDIT**: Forgot a step. After editing smb.conf restart samba:[/COLOR]
```
sudo service smbd restart
sudo service nmbd restart
```

This is really a side issue since the "hostname.local" doesn't use a netbios name it uses the host name I'm just trying to clean this up a bit.

[3] I made a fatal mistake and didn't read the HowTo you referenced above before I posted and didn't realize you invoked the winbind voodoo.

There are 2 camps of folks who use samba:
** Those that say winbind is an absolute requirement
** And those who say that that those in the other group should be publicly castrated.

I'm in the second camp. If we can get smb://hostname.local working we can bypass all this winbind nonsense.

---

### Post by ratdog on 2013-12-17
Thanks for the help.

Here are the permissions:
```
lightpool@Entertainment-Center:~$ ls -al /media/sdb2
total 124
drwxrwxrwx  8 lightpool lightpool  4096 Jul 26 09:07 .
drwxr-xr-x  3 root      root       4096 Dec 13 10:05 ..
-rw-rw-rw-  1 lightpool lightpool  6148 Mar 15  2013 .DS_Store
drwxr-xr-x 12 lightpool lightpool  4096 Mar 20  2011 ffp
-rw-r--r--  1 lightpool lightpool 72889 Jun 20 04:14 ffp.log
-rwxrwxrwx  1 lightpool lightpool  1778 Mar 20  2011 fun_plug
drwxrwx---  9 lightpool lightpool  4096 Feb 25  2012 Media
drwxr-xr-x  3 lightpool lightpool  4096 Mar 20  2011 src
drwx------  2 lightpool lightpool  4096 Jul 20 20:11 .systemfile
drwxrwxrwx  3 lightpool lightpool  4096 Dec 30  2012 .TemporaryItems
-rw-rw-rw-  1 lightpool lightpool  4096 Dec 30  2012 ._.TemporaryItems
drwx------  5 lightpool lightpool  4096 Aug 18 10:42 .Trash-1000
```

I'm all for simple, so getting rid of winbind is fine as long as it works.  Thanks again!

---

### Post by Morbius1 on 2013-12-17
Your share looks like this:
> [Media]
    comment = lightpool files on the server
    path = /media/sdb2/Media
    valid users = elysselightpool, lightpool, rashaanlightpool
    read only = No
Your permissions look like this:
> drwxrwx---  9 lightpool lightpool  4096 Feb 25  2012 Media
The only remote user that will gain access to that share is lightpool so there's a number of ways around this issue. The simplest is to force all the "valid users" after they provide the correct passwords to become lightpool by adding something to the share:
> [Media]
    comment = lightpool files on the server
    path = /media/sdb2/Media
    valid users = elysselightpool, lightpool, rashaanlightpool
[COLOR=#0000cd]**    force user = lightpool**[/COLOR]
    read only = No
"valid users" will restrict who can access the share but once they are in everyone will be lightpool for that share.

Then restart smbd:
```
sudo service smbd restart
```

Now see if "smb://entertainment-center.local/media/" still gives you an error.

---

### Post by ratdog on 2013-12-17
I've made your suggested changes, but still get the same error messages.

I'm not sure if I have the users setup correctly.  Do I need to have a user created on the server with the same username as each laptop?  How do I ensure that the laptops are in the same workgroup?

Thanks again

---

### Post by Morbius1 on 2013-12-17
Yes, indeed you do. Actually you need to do 2 things:

[1] Create a local user on the server itself - like elysselightpool for example.

[2] Then you need to add them to the samba password database:
```
sudo smbpasswd -a elysselightpool
```
You need to do that for yourself as well:
```
sudo smbpasswd -a lightpool
```

[COLOR=#0000cd]**EDIT**[/COLOR]: I should have shut down about an hour ago so I'm afraid I'm going to have to leave you for today. I'll check back tomorrow.

---

### Post by ratdog on 2013-12-17
I was able to access the shares from a laptop!

After deleting all users and then setting up new users and passwords as you suggested, I was able to log in through nautilus.

This command: 
```
nautilus smb://entertainment-center.local/media/
```
did not work.

This one with the IP address did work!
```
nautilus smb://192.168.0.12/media
```

Trying 'Connect to Server' from the Nautilus File menu (as mentioned in another tutorial) did not work.

Now how can I get the laptops to save the samba password and automatically mount (or at least create a link to) the shared drive?

Getting so close!  Thanks for the help.

---

### Post by Morbius1 on 2013-12-18
>  Now how can I get the laptops to save the samba password and  automatically mount (or at least create a link to) the shared drive?
You are given an opportunity to save the credentials for a share when you access it:
[ATTACH=CONFIG]248703[/ATTACH]
To have the share easily available bookmark it once you open it in Nautilus: Bookmarks > Add Bookmark

---

### Post by ratdog on 2013-12-18
Fantastic!  Our network is now setup.

Thanks for all the help Morbius1.

---

