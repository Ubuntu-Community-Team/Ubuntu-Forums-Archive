---
title: "Samba - Cant browse one of 3 machines on network"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by xpatrick on 2011-04-24
I have 3 machines on the my network all running Ubuntu 10.10 -  no Windows machines - and recently something changed that means I cant browse one of them from the other 2

I can see the machine in Network list in Nautilus but when I click on it there is a delay then an error message saying 'Unable to mount Location - cant retrieve list from server' - I have seen this error a few times on the forums but none of the solutions seem to solve it for me

I can browse both the other machines from the problem machine and can connect to all three via VLC

I am using samba - I have always had problems with networking - I presume Samba - where connections and shares seem to intermittently stop working so have tried installing various networking apps such as Sadms most recently - it maybe this that has caused the problem - but uninstalled now

I have worked through a number of guides describing configuring Samba, but none seem to solve this problem.

I wonder if it is a problem with Samba, or some other configuration, but I dont know what? I thought about uninstalling Samba and reinstalling, but there are several packages relating to Samba and Im not sure which I should target

Thanks for any help

Patrick

---

### Post by Morbius1 on 2011-04-24
Although it may not seem like it, 'Unable to mount Location - cant retrieve list from server' isn't really a Samba problem it's a networking problem. The network can't resolve a machine name to an ip address. Try to access the share on the problem machine by ip address:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the problem machine.*[/COLOR]

If that works then Samba is probably OK or may need some tweaking.

You might want to post the output of the following command from the problem machine so we can see how samba is set up:
```
testparm -s
```

---

### Post by xpatrick on 2011-04-25
I also have now tried setting all 3 machines as fixed ip - this has result in the Network nor being browsable at all!

output as requested

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[DATA01]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ELPHIN_NETWORK
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
	valid users = patrick
	read only = No

[DATA01]
	comment = description
	path = /media/DATA01


As far as Fixing IPs go - what should I set as DNS server? 

Thanks

Patrick

---

### Post by Morbius1 on 2011-04-25
As far as I can see there is nothing wrong with your smb.conf so here are some things to check:

[1] It's possible that nmbd is not running so run the following command and see if the other machine can see this machine:
```
sudo service nmbd restart
```[2] It's also possible that your machine name is too long. Your workgroup name is almost at the limit in length so the machine name may exceed it. It has to be 15 characters or less in length and the easiest way to fix it is to use smb.conf itself. Add the following line to the [global] section of smb.conf:
```
netbios name = something-15-characters-or-less-in-length
```Then restart samba:
```
sudo service smbd restart
```[3] Firewalls tend to get in the way so you might want to disable it on this box and see if things improve.

[4] You might want to run the following diagnostic:
```
smbtree
```What it should do is list every workgroup on the lan, every host within those workgroups, and every share within those hosts. It will also produce error messages if it can't do the above.

---

### Post by Morbius1 on 2011-04-25
For some reason I completely ignored the first sentence of your last post:
> I also have now tried setting all 3 machines as fixed ip - this has result in the Network nor being browsable at all!If all the machines on your lan now have fixed ip addresses you really no longer have to browse the shares. You can bookmark them:

Run the following command with the correct ip address:
```
nautilus smb://192.168.0.100
```Then when Nautilus opens up bookmark it: Bookmarks > Add bookmark. It will then show up under Places in the left panel of Nautilus just like a "mapped drive" does in Windows.

If you still want to browse then you can add the ip addresses and their machine names to /etc/hosts, for example under the 127.0.1.1 line add:
```
192.168.0.100 mach1
192.168.0.101 mach2
```

---

### Post by xpatrick on 2011-04-25
All working now

Fantastic

Many many thanks

---

