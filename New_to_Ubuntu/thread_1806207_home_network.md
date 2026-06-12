---
title: "home network"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by claytonbagwell on 2011-07-17
This a re-post searching for answers.  I have two computers running 10.04 LTS lucid lynx.  They are wired (LAN) to the same router (switch.)  I want to be able to access files from one compputer to the other.  I have marked the folders I want to share.  <network> allows me to see the folders on both computers that are marked for sharing.  When I try to share (open) a shared shared file I am asked for a workgroup domain password.  My sudo password does not work.  Using the terminal entry <sambapasswrd> allowed me to set a samba password but that new password did not work.  (In fact, it somehow changed my login password!?)  What is the secret to share files between two computers that use Ubuntu and are wired from the same router?  Please help.

---

### Post by mikejonesey on 2011-07-17
start->places->conntect to server... 

enter login details...

i use samba for connecting to windows networks only...

---

### Post by e79 on 2011-07-17
Try installing the smbfs packages on both computers :

```
sudo apt-get install smbfs
```

---

### Post by claytonbagwell on 2011-07-17
Thank you e79--------I did as you suggested and both computers have smbfs.  Then I tried to share files using <network>, and was again asked for the password required for share documents on the computer.  Where does that password come from?  Can I set it, change it or eliminate it?

---

### Post by claytonbagwell on 2011-07-17
Mikejonesey----Thanks for the idea.  I tried to do it, and it works.  I connect to the other computer's list of sharable folders.  But when I ask to open the folder I am asked for a password to share files.  I don't know what this password is and I don't know where to find it.  Any ideas (I hope)?

---

### Post by Morbius1 on 2011-07-17
Please post the output of the following command:
```
testparm -s
```And just in case post the output ( if any ) from this one:
```
net usershare info --long
```BTW:
> Using the terminal entry <sambapasswrd> allowed me to set a samba  password but that new password did not work.  (In fact, it somehow  changed my login password!?)It's "smbpasswd -a user-name" not "sambapassword -a user-name" but unless you created a share requiring a password it may not be necessary.

---

### Post by claytonbagwell on 2011-07-17
rafael@RafasTosh:~$ testparm -s
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
rafael@RafasTosh:~$

---

### Post by claytonbagwell on 2011-07-17
rafael@RafasTosh:~$ net usershare info --long
[documents]
path=/home/rafael/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

rafael@RafasTosh:~$

---

### Post by mikejonesey on 2011-07-17
using the method above you should be able to use the user account on the target machine instead of any share user pass... (you should not need to make any folder shared using this method). the method used via the connect to server (select ssh and port 22, target user and password) is sftp which runs off the ssh protocal it's fast, safe...

once your managed the above, if you want to look into a way of perminantly mounting you will probably want to look into somthing like sshfs which is dead easy to use...

---

### Post by Morbius1 on 2011-07-17
I'm not exactly sure how you managed to create a usershare in Lubuntu but with that share definition you force the remote user to authenticate himself to access the share. So you have 3 options:

[1] Create a samba password for yourself and access with your username:
```
sudo smbpasswd -a rafael
```[2] If you don't want the remote user to access your share as you then it gets a bit more complicated.

You will need to create a local user on the Lubuntu machine and then give him a samba password. That will be the user name and password he will use to gain access.

[3] You can change the share definition to allow guest access. 

Again, I'm really interested in how you created a usershare in Lubuntu but you can change it via a command line:

```
net usershare add documents /home/rafael/Documents "documents folder" everyone:F guest_ok=y

```And then you will need to change permissions to allow guests to access it:
```
 sudo chmod 0777 /home/rafael/Documents
```

---

### Post by claytonbagwell on 2011-07-17
Both of the methods that I used resulted in the same password request. I tried "smbpasswrd -n" to set no password.  That did not change the request for a password.  I tried "smbpasswrd -n <my user name>" and was again asked for a password to share the files.  Since you say that I should not need a password using these methods, do you think it would be good to re-install the Ubuntu?  I mean, something is wrong it seems.  Can it be so much trouble to link two computers using Ubuntu, LAN wired from the same switch?

---

### Post by Morbius1 on 2011-07-17
I never said you did not need a password to access the share. I said the opposite. Your share definition requires it.

Why didn't you do a "sudo smbpasswd -a rafael"
[COLOR=Blue][B]
EDIT: [/B][/COLOR]In you last post you mentioned "Ubuntu" - does this mean you are running Ubuntu not Lubuntu?

---

### Post by claytonbagwell on 2011-07-17
Thank you, everybody.  I am going to drop it for now.  I just don't get it.  I will try to get some hands on help.  Thank you so much...and I do love Linux!

---

### Post by claytonbagwell on 2011-07-17
Yes, Ubuntu, 10.04 LTS, Lucid Lynx.

---

### Post by claytonbagwell on 2011-07-17
32 bit version on a Toshiba 235D 64 bit machine

---

### Post by Morbius1 on 2011-07-17
You posted in the Lubuntu section of the forum is the reason I asked.

BTW, your smb.conf and your usershare created in Nautilus are perfect. Usually when people post here with problems they've done terrible things to their samba configurations and expected it to work. But yours is without error.

When you come to terms with adding a samba user and password I'm sure it will work out.

---

