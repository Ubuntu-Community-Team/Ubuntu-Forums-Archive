---
title: "Printer sharing problems"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by BDavis81 on 2010-07-26
Hey guys. I am a very new Ubuntu user and have a problem.

I have Ubuntu 10.04 installed on my desktop and Win Vista installed on a laptop. Both are connected to a wireless router. I have an Epson printer connected to the Ubuntu desktop and it works perfect. When I had Windows installed on the desktop, I was able to print over the home network from the laptop without a problem. After installing Ubuntu, I am not able. I went into Vista and managed to find the Ubuntu workgroup and my printer in the network. Added the printer in Vista and tried to print. All I am getting is a Communication Error on the Vista computer.

Any help would be greatly appreciated. Thank you.

---

### Post by rolnics on 2010-07-26
I've been trying to reply to this all day!

I've re-read your post, do you have windows firewall on or any firewall on? This might be what's causing the comms error?

You might have to look into using samba to share the printer with windows, I'm no expert on samba, but I do use it.

---

### Post by BDavis81 on 2010-07-26
No firewalls unless Ubuntu comes installed with one. I have Samba installed on my desktop and all the permissions look to be set to allow incoming.

---

### Post by oldsoundguy on 2010-07-26
silly question, but it has to be asked.  Do you have sharing turned on for the printer in Ubuntu?

Just as with a printer on a Windows computer being accessed from a Linux computer on a net, permissions have to be granted.

I have 7 machines .. 5 Linux .. 4 total wireless .. set up in work station locations and they share 5 printers and there are two other printers that are Windows only as no drivers for them in Linux (one an Avery Label printer.)  It took a while to get everything that COULD talk talking.  But they all work now.

---

### Post by BDavis81 on 2010-07-26
Yeah, I went to System > Admin > Printing and the printer has Shared checked and in the Server settings part I have Publish printers checked. Thanks for all the help so far guys.

---

### Post by rolnics on 2010-07-27
Have you checked to make sure your configuration file is working correctly?

Run the following command to check things are ok.

```
testparm /etc/samba/smb.conf
```

Do you also know what shares are active? 

```
smbclient -L yourhostname
```

This will list the share available.

If you want to read more about these commands and samba in general then [click here]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553838") I've copied the commands from that page.

---

### Post by rjhidson on 2010-07-27
I am having a similar issue with my shared printer. I have two work stations, one is Windows Vista 64x and the other is running Ubuntu 10.4

From the windows machine I can see the Ubuntu workstation and the shared printer. The shared printer is set in Windows as the default printer but, when I try and print to it from Windows it does not work. I don't get any errors, or indication that there is an issue. 

The printer is shared on the Ubuntu desktop, published in the server settings and I can print to it from Ubuntu, but not from Windows. Stranger still is that when I set up the printer, I can get the test page to work just fine. 

Any ideas?

---

### Post by BDavis81 on 2010-07-27
> **rolnics said:**
> Run the following command to check things are ok.

```
testparm /etc/samba/smb.conf
```

This is what I got:

brandon@ubuntu:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = BRANDY-PC
	server string = %h server (Samba, Ubuntu)
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	use client driver = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No
	guest ok = Yes
brandon@ubuntu:~$ 


> **rolnics said:**
> Do you also know what shares are active? 

```
smbclient -L yourhostname
```

This is what I got:

Domain=[BRANDY-PC] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	D$              Disk      Default share
	IPC$            IPC       Remote IPC
	Public          Disk      
	Users           Disk      
Domain=[BRANDY-PC] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------






Any thoughts?

---

### Post by fbobraga on 2010-07-27
> **BDavis81 said:**
> (...)
Domain=[BRANDY-PC] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]
(...)

do the 'smbclient -L' thing on the Ubuntu box (wich has the printer connected and shared):
```
smbclient -L localhost
```

---

### Post by BDavis81 on 2010-07-28
> **fbobraga said:**
> ```
smbclient -L localhost
```

I get an error saying:

session setup failed: NT_STATUS_LOGON_FAILURE

---

### Post by rolnics on 2010-07-28
You might have already done this, but reading other forums, it seems likely that you haven't setup your user's for sharing.

You firstly need a root user to do this run this command
```
smbpasswd -a root
```
It will ask for a password, best not to use the same one as on your ubuntu system.

If you want more infomation on that command just type
```
man smbpasswd
```

And then setup the users with smbpasswd

Then try BDavis81 command again, or if you know the ip's / host names of each pc add that to the end of the command and see what happens.

---

