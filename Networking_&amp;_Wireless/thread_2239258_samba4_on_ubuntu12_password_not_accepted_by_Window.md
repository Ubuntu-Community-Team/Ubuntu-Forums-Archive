---
title: "samba4 on ubuntu12 password not accepted by Windows 7"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by normwheatley on 2014-08-12
Hi,

I have a windows 7 laptop running VirtualBox with an ubuntu 12.04 VM. I'd like to access unbuntu files from my PC (this is a test, as my files are actually on a Ubuntu server machine but I don't want to mess that up yet).
I am trying to use Samba (standalone) for this ... which means samba4. I can do this by the GM+NOME GUI (on a separate ubunut 12 VM) but I want to use the command line for everything as our main ubuntu server has no gui.

So, I've managed to install samba4 I believe and have set up users and a few shared folders but when I go to windows and try to map a network drive to one of these shared folders my password is rejected. 
Some oddities
a)  I start samba by  .... sudo service samba4 start
b) my /var/log/samba has one file log.%m
c) this log file shows a failure when samba starts up ...

  task_server_terminate: [Cannot start Winbind (standalone configuration): Failed to find record for FACSVM in /var/lib/samba/private/secrets.ldb: No such object: (null): Have you provisioned this server (FACSVM) or changed it's name?]

d) smbclient shows ...
sudo smbclient -L localhost -U%
[sudo] password for fc: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.0.0alpha18]

	Sharename       Type      Comment
	---------       ----      -------
	allusers          Disk      all users
	homes           Disk      Home Directories
	printers         Printer   All Printers
	print$           Disk      Printer Drivers
	nwshare        Disk      test using cli install of samba
	IPC$             IPC       IPC Service
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.0.0alpha18]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
fc@facsvm:/var/log/samba$ 

Any ideas?

thanks heaps

norm

---

### Post by bab1 on 2014-08-13
> **normwheatley said:**
> Hi,

I have a windows 7 laptop running VirtualBox with an ubuntu 12.04 VM. I'd like to access unbuntu files from my PC (this is a test, as my files are actually on a Ubuntu server machine but I don't want to mess that up yet).
I am trying to use Samba (standalone) for this ... which means samba4. I can do this by the GM+NOME GUI (on a separate ubunut 12 VM) but I want to use the command line for everything as our main ubuntu server has no gui.

So, I've managed to install samba4 I believe and have set up users and a few shared folders but when I go to windows and try to map a network drive to one of these shared folders my password is rejected. 
Some oddities
a)  I start samba by  .... sudo service samba4 start
b) my /var/log/samba has one file log.%m
c) this log file shows a failure when samba starts up ...

  task_server_terminate: [Cannot start Winbind (standalone configuration): Failed to find record for FACSVM in /var/lib/samba/private/secrets.ldb: No such object: (null): Have you provisioned this server (FACSVM) or changed it's name?]

d) smbclient shows ...
sudo smbclient -L localhost -U%
[sudo] password for fc: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.0.0alpha18]

	Sharename       Type      Comment
	---------       ----      -------
	allusers          Disk      all users
	homes           Disk      Home Directories
	printers         Printer   All Printers
	print$           Disk      Printer Drivers
	nwshare        Disk      test using cli install of samba
	IPC$             IPC       IPC Service
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.0.0alpha18]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
fc@facsvm:/var/log/samba$ 

Any ideas?

thanks heaps

norm
Since this is a VM and you are using Ubuntu 12.04, I suggest you kill this VM and start over.  There is no reason to use Samba4 in 12.04.  It was a test version and not at all what was finally released as.  In fact Samba 4.1 is the only version you should ever use.

I suggest that if you are using 12.04 then use Samba3 particularly if you are using the server a standalone (workgroup) server.  If you were to use Ubuntu 14.04 and Samba 4.1 as a standalone server it will work the same as Samba 3 in earlier editions of Ubuntu.

There is no need for winbind with a workgroup Samba server.  On a single segment network there is no need for a WINS server.  Winbind and WINS are two completely different concepts but in the end on a workgroup server you need neither.

---

### Post by normwheatley on 2014-08-13
excellent!
I purged samba4 and installed samba 3 ... just by sudo apt-get install samba smbfs .... a snap!
It works great :)

thanks so much

Norm

---

### Post by bab1 on 2014-08-13
> **normwheatley said:**
> excellent!
I purged samba4 and installed samba 3 ... just by sudo apt-get install samba smbfs .... a snap!
It works great :)

thanks so much

Norm
The package smbfs is the client side Samba package.  In Ubuntu 14.04 the package is called ***cifs-utils*** and the Samba4.1 package is named  ***samba***

The choice of using the package name of *samba * for the package of Samba 4.1 with the current Ubuntu release is most likely due to the fact that only Samba 4.1 is supported by Ubuntu 14.04.

If we have solved this it would be nice for you to mark the thread as solved.  See the thread tools at the right top of the page,

---

