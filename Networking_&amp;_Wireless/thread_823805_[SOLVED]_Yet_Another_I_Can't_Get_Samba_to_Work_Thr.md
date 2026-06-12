---
title: "[SOLVED] Yet Another I Can't Get Samba to Work Thread"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Major_Kong on 2008-06-09
I'm trying to share my printer on the local home network, and i'm having some problems...

smb.conf  :

> [global]

	workgroup = something

	server string = %h server (Samba, Ubuntu)

	dns proxy = no

	netbios name = something-desktop

	log file = /var/log/samba/log.%m

	max log size = 1000

	syslog = 0

	panic action = /usr/share/samba/panic-action %d

	security = share

	encrypt passwords = true

	passdb backend = tdbsam

	obey pam restrictions = yes

	guest account = nobody
	invalid users = root

	unix password sync = yes

	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes

	map to guest = bad user



	printing = cups
	printcap name = cups

	usershare allow guests = yes
	username map = /etc/samba/smbusers


[printers]
	comment = All Printers
	browseable = yes
	path = /var/spool/samba
	printable = yes
	guest ok = yes
	read only = yes
	create mask = 0700

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

smbtree returns nothing...

I can't see where the problem is...


(Running Ubuntu 8.04, and winbind is installed)

---

### Post by jonandrews on 2008-06-09
I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


The is also a guide to setting up access to a Windows printer. Hope they help.

---

### Post by Major_Kong on 2008-06-09
> **jonandrews said:**
> I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


The is also a guide to setting up access to a Windows printer. Hope they help.

Already tried it. No effect :(

---

### Post by superprash2003 on 2008-06-09
firstly are the pcs able to ping the ubuntu pc with the printer?

---

### Post by Major_Kong on 2008-06-09
Yes.

---

### Post by superprash2003 on 2008-06-10
are you trying to connect from a windows or ubuntu pc?

---

### Post by Major_Kong on 2008-06-10
> **superprash2003 said:**
> are you trying to connect from a windows or ubuntu pc?

Ubuntu.

But the problem is still that i can't get no output from smbtree.

---

### Post by atryus28 on 2008-06-10
I have seen this problem several times.  Unfortunately I have no solution for you as I have not seen it fixed.

Oh wait I just noticed your samba config file.  You only have access via the creator with 700.  7 equals full control, the second number is for group and the last number is for others.  Try setting your printer to be 777 for now.  It's just a printer I doubt you will have any security issues with people printing.  ;)

so this :
[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700

Should read as this:
[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0777

You should also notice your global settings block the root user and guest is automatically mapped to "bad user" so even though you may have root as the only allowed person no one will be allowed to use it since only root has access and root is also blocked.  The samba.conf in Ubuntu seems really restricted pretty much TOO restricted honestly.

---

### Post by Major_Kong on 2008-06-10
Still nothing. :S

What i don't get is that in previous versions, i got samba to work perfectly. What am i missing ?

---

### Post by atryus28 on 2008-06-10
I am thinking there is something seriously wrong with Ubuntu server in general.  First of all it refuses to get an IP addy with dhcp during install or after.  During install I even gave it the dhcp name, fqdn, and then IP.  It refuses to get an address, this is not a problem with the network as EVERY other system (a few nix systems and an ubuntu desktop) get one just fine without an extra issue.  This even happens if I use vmware.

Now I too am trying to setup samba (as I have done a million times before) and yet nothing is working correctly.  I am losing faith in ubunutu more and more and the bonehead in charge at Canonical has the gall to publicly claim how they way they do things is best and how successful hardy was.  He must not use his own software which is having a host of issue for a 3 and 5 year support release.  I am generally losing faith in linux anymore honestly.  Things actually used to work BETTER a few years ago and now we have glitz and glam on the desktop and the basics breaking on the server end and desktop too.  Uggh  I think I going back to using type writers.  I have been dealing with nix for years and it's getting exhausting anymore.  

Maybe someday the linux crowd will actually get it's crap together.

---

### Post by superprash2003 on 2008-06-10
go to system->administration->printing and go to policies.. and ensure that Shared and Enabled is CHECKED

---

### Post by Major_Kong on 2008-06-10
> **superprash2003 said:**
> go to system->administration->printing and go to policies.. and ensure that Shared and Enabled is CHECKED

Already did that.

---

### Post by superprash2003 on 2008-06-10
try reinstalling samba

---

### Post by Major_Kong on 2008-06-11
Still nothing.


Solved: The new packages seem to have fixed the problem, whatever it was.

---

