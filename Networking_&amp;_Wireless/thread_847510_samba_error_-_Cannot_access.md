---
title: "samba error - Cannot access"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by phoenix81000 on 2008-07-02
[B]Hallo,

When i try to connect from my desktop to my laptop (both 8.04 up 2 date) i can access my shares. In this my external disk. So far so good. When i open my favorite anime Totems says:[/B]

An error occurred 
Could not read from resource. 
[B]

Ok well thats bad.. so i decide to try it with vlc:
Basically the error log shows this:[/B]

Using netbios name HARM-DESKTOP.
Using workgroup MSHOME.
[00000295] access_smb access error: open failed for 'harm-laptop/lacie/%5BINP%5DOne_Piece_339_SD%5B60E6F2AE%5D.avi' (Permission denied)
Performing aggressive shutdown.

**Ok so what THE HELL.. ive added a password for my user with sudo smbpasswd -a harm so that cant be the problem. Here is my testparm:**

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	comment = Home Directories
	invalid users = root

[Shares]
	available = No

[LACIE]
	path = /media/LACIE
	read only = No

Ok so WHAT THE HELL!! my config file looks a bit different my LACIE share should testparm as such:
        [LACIE]
        path = /media/LACIE
        browseable = yes
        read only = no
        writable = yes

[B]
So it basically ends up i HAVE to whatch my anime on my laptop.. which is ok but why the f isnt this working like it used to or is supposed to.

Here are pastebins of usefull stuff i suppose
[/B]

VLC error: [http://pastebin.org/48000](http://pastebin.org/48000)
TESTPARM : [http://pastebin.org/48001](http://pastebin.org/48001)
SMB.conf : [http://pastebin.org/48002](http://pastebin.org/48002)
SMBCLIENTLOG : [http://pastebin.org/48004](http://pastebin.org/48004)
[B]
Thanks for any help![/B]

---

