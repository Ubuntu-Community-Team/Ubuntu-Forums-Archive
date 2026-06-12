---
title: "Samba Problem"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by beak1967 on 2008-03-03
Help!  Had Samba running a while back and was able to access files from the ubuntu machine that was running it.  Out of the blue it stopped working, possibly right after an update.  I have uninstalled and reinstalled samba with no results.  Having read some similar posts I ran the command ps aus | grep mdb and found that nmbd is not running.  I tried running /usr/sbin/nmbd -D to no avail but I'm new to linux and maybe that's not the proper command.  I also read somewhere that nmbd has to load before smbd.  Any help will be appreciated since I'm contemplating a fresh install of ubuntu to start from scratch.

---

### Post by Iowan on 2008-03-03
You can try  **sudo /etc/init.d/samba restart**.

---

### Post by beak1967 on 2008-03-04
Tried what you suggested Iowan and received the following response: "start-stop daemon: warning: failed to kill 4828: No such process."  Ran the ps aux | grep mdb command again and system response was two instances of /usr/sbin/smbd -D but no nmbd.  If nmbd is suppose to load it's not.

---

### Post by Eiríkr on 2008-03-04
Try just stopping samba:
```
sudo /etc/init.d/samba stop
```

If that fails, run your [font=courier]ps aux | grep mbd[/font], figure out the process IDs of the running smbd instances, and then manually kill them:
```
sudo kill PIDNUMBER
```

Once those are toast, then try starting samba:
```
sudo /etc/init.d/samba start
```

Provided it's up and running properly, check for nmbd:
```
ps aux | grep mbd
```

And just for good measure, make sure it can be properly restarted now, with no failures:
```
sudo /etc/init.d/samba restart
```

If any of these commands fail out, let us know, and post the full error messages if you can.  

Cheers,

Eiríkr

---

### Post by beak1967 on 2008-03-04
> **Eiríkr said:**
> Try just stopping samba:
```
sudo /etc/init.d/samba stop
```

If that fails, run your [font=courier]ps aux | grep mbd[/font], figure out the process IDs of the running smbd instances, and then manually kill them:
```
sudo kill PIDNUMBER
```

Once those are toast, then try starting samba:
```
sudo /etc/init.d/samba start
```

Provided it's up and running properly, check for nmbd:
```
ps aux | grep mbd
```

And just for good measure, make sure it can be properly restarted now, with no failures:
```
sudo /etc/init.d/samba restart
```

If any of these commands fail out, let us know, and post the full error messages if you can.  

Cheers,

Eiríkr
Here are the results of my efforts following your suggestions.  I ran the ps command three times to confirm what processes were running, stopped and restarted.  I am assuming that process 5713, which failed to kill because it didn't exist, is the nmbd process.  And as you can see it did not load with the subsequent start command.  So, I go back to my original assumption that samba is not working because nmbd is not loading at all.  Any further suggestions?

root@ubuntuserver:/home/beak# ps aux | grep mbd
root      5715  0.0  0.2  10968  2224 ?        Ss   05:21   0:00 /usr/sbin/smbd -D
root      5719  0.0  0.0  10968   888 ?        S    05:21   0:00 /usr/sbin/smbd -D
root      6394  0.0  0.0   2980   768 pts/0    S+   18:23   0:00 grep mbd
root@ubuntuserver:/home/beak# sudo /etc/init.d/samba stop
 * Stopping Samba daemons...                                                       start-stop-daemon: [COLOR="Red"]warning: failed to kill 5713: No such process[/COLOR]
                                                                            [ OK ]
root@ubuntuserver:/home/beak# ps aux | grep mbd
root      6420  0.0  0.0   2972   760 pts/0    S+   18:24   0:00 grep mbd
root@ubuntuserver:/home/beak# sudo /etc/init.d/samba start
 * Starting Samba daemons                                                                       [ OK ] 
root@ubuntuserver:/home/beak# ps aux | grep mbd
root      6436  0.0  0.2  10964  2224 ?        Ss   18:25   0:00 /usr/sbin/smbd -D
root      6440  0.0  0.0  10964   888 ?        S    18:25   0:00 /usr/sbin/smbd -D
root      6442  0.0  0.0   2976   760 pts/0    S+   18:25   0:00 grep mbd
root@ubuntuserver:/home/beak#

---

### Post by Eiríkr on 2008-03-04
Yep, sounds like something's gone funny.  Since it's nmbd that's having the problem, have a look at your nmbd log file, located at [font=courier]/var/log/samba/log.nmbd[/font].  Let us know what you find.  I'd also suggest posting a copy of your [font=courier]/etc/samba/smb.conf[/font] file.  

Cheers,

Eiríkr

---

### Post by beak1967 on 2008-03-05
> **Eiríkr said:**
> Yep, sounds like something's gone funny.  Since it's nmbd that's having the problem, have a look at your nmbd log file, located at [font=courier]/var/log/samba/log.nmbd[/font].  Let us know what you find.  I'd also suggest posting a copy of your [font=courier]/etc/samba/smb.conf[/font] file.  

Cheers,

Eiríkr

Thanks for your assistance to date.  Here is my nmbd log file following a stop and start of samba.

[2008/03/05 18:19:56, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/03/05 18:19:56, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating

It's all greek (unix) to me.  Hope it gives you some insight into what went wrong and how to fix it.  Thanks again, Alan.
[2008/03/05 18:19:56, 0] nmbd/nmbd.c:main(771)
  ERROR: Failed when creating subnet lists. Exiting.

---

### Post by beak1967 on 2008-03-05
> **beak1967 said:**
> Thanks for your assistance to date.  Here is my nmbd log file following a stop and start of samba.

[2008/03/05 18:19:56, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/03/05 18:19:56, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating

It's all greek (unix) to me.  Hope it gives you some insight into what went wrong and how to fix it.  Thanks again, Alan.
[2008/03/05 18:19:56, 0] nmbd/nmbd.c:main(771)
  ERROR: Failed when creating subnet lists. Exiting.

Here is my smb.conf file.  It appears like some lines have been commented out but I have no idea how or why.

[global]
;	netbios name = ubuntuserver
	server string = Alan's server
	workgroup = Workgroup
	security = user
	hosts allow = 127. 192.168.0.
	interfaces = 127.0.0.1/8 192.168.0.0/24
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	printcap name = /etc/printcap
;	load printers = yes
	cups options = raw
	printing = cups
	guest account = smbguest
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 8
	password level = 8
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = bcast lmhosts wins host
;	wins support = no
	wins server = 
;	wins proxy = no
	dns proxy = no
	preserve case = no
	client use spnego = no
	client signing = no
	client schannel = no
;	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no
	update encrypted = yes
;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
	username map = /etc/samba/smbusers
;	smb passwd file = /etc/samba/smbpasswd
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no
;	winbind refresh tickets = no
;	winbind offline logon = no

[homes]
	comment = Home Directories
	path = /home
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = no
;	available = yes
	browseable = no
;	guest ok = no
;	printable = no
	locking = no
	create mode = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
;	browseable = yes
;	writable = no
;	guest ok = no
	printable = yes
	share modes = no
	locking = no

[pdf-documents]
	path = /home/pdf-documents
	comment = Converted PDF Documents
;	available = yes
;	browseable = yes
	writeable = yes
	guest ok = yes

[pdf-printer]
	path = /tmp
	comment = PDF Printer Service
	printable = yes
	guest ok = yes
	use client driver = yes
;	printing = bsd
	print command = /usr/bin/gsambadpdf %s %u
	lpq command = 
	lprm command =

---

### Post by Iowan on 2008-03-05
Does running **testparm** yield any "nastygrams"?

---

### Post by beak1967 on 2008-03-06
Here is the response following testparm:

root@ubuntuserver:/home/beak# testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Warning: Service pdf-printer defines a print command, but print command parameter is ignored when using CUPS libraries.
Server role: ROLE_STANDALONE

Does any of this indicate why nmbd is not loading?  Thanks, Alan.

---

### Post by Eiríkr on 2008-03-06
I note that this smb.conf file has a pretty complicated set of options for someone who says they're just starting out with Linux... which makes me wonder if you picked it up somewhere?  Whatever the case, I'd *seriously* consider simplifying as much as possible.  

Anyway, for starters, it looks like nmbd is having problems with your interface setup, so start out by commenting out all the interface-related lines in your smb.conf file and restarting.  Then check if nmbd is running, and if not, check the logs again.  If you're *still* having trouble with nmbd at that point and the log file states the same trouble with interfaces, your problem might just be in your actual network configuration rather than your smb.conf settings, in which case posting your /etc/network/interfaces file might be helpful.  

Cheers,

Eiríkr

---

### Post by beak1967 on 2008-03-06
I think the complexity of my smb.conf file can be attributed to GSAMBAD gui that I tried using.  In any event, I commented out the interfaces line, stopped and restarted samba and all seems to have loaded properly.  At least the ps aux command shows that nmbd is loaded ahead of smbd.  I think I still have some other bugs to work out but it is too late to try and tackle them now.  Thanks for your assistance.  I'll post more later as the need arises.  Alan.

---

### Post by Eiríkr on 2008-03-06
Cheers then, glad things seem to be working better.  :D

And as an aside, I've been seeing quite a few examples of GUI-based Samba config tools really making a mess of things...  :shock:

Cheers,

Eiríkr

---

