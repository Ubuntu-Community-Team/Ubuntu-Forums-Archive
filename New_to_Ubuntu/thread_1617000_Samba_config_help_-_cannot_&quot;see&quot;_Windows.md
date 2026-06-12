---
title: "Samba config help - cannot &quot;see&quot; Windows network or printers"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by bomber1712 on 2010-11-08
Hi all,

I am running Ubuntu 10.10 on a Compaq nc6220.  I have a Windows Network and all machines belong to MSHOME group.  I am running 2 Ubuntu systems (10.10 and 10.04), 2 XP, and 2 Win7 systems.  I have the internet wired to one XP and one Win 7.  The rest connect wirelessly.  I have no problem sharing the internet connection.  The Windows machines can all see each other, but not the Ubuntu machines (and I don't care if they can).  The printers are connected to an XP machine.

I really want the Ubuntu machines to be able to see the Windows Network and share the printers.  The funny thing is that I had this working at one point.  I didn't do anything special to get it working, it just did (I think it was on 9.1 and 10.04).  Suddenly, however, it no longer worked on that machine, and I have never got it working on my 10.10 machine.

Any assistance would be appreciated.


**Output from Ubuntu 10.10 Machine:**

testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
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
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No
	guest ok = Yes

---

### Post by HermanAB on 2010-11-09
Howdy,

The upper layers will not work if the lower layers are broken.

Check all the basics:

1. Are the Windows and Linux machines on the same subnet?
Linux: $ /sbin/ifconfig
Windows: c:\> ipconfig /all

2. Try to connect to the Windows machine from Linux:
$ telnet win.dows.ip.address 445

3. If you cannot connect, confirm that Server is running on Windows and that the Windows firewall is open.
c:\> net stop server
c:\> net start server
c:\> telnet localhost 445

Once all of that works, try smbclient.  it will show you the low level error messages received from Windows.  For example, if your password is expired, smbclient will tell you:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

