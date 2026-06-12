---
title: "new hd + samba share = BSOD on windows client"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by ZenMasta on 2008-04-04
I recently added a 2nd hd and I shared a folder on the new hd via samba, however the windows computer crashes everytime it tries to access the new share and is very delayed in accessing the old shares. Anyone know what would cause this?

Prior to installing this new hard drive I already had a couple of shares the windows pc without any problems, and quite fast I might add. However if the win pc access the new share on the 2nd HD it blue screens and crashes. Additionally if I access any of the old shares it's very slow. If I delete the share from the new HD everything runs fast and without error again. :(

---

### Post by Eiríkr on 2008-04-04
What version of Windows are you using?  Remember, there are many versions available, and they all have their own peculiarities.  :-|

Cheers,

Eiríkr

---

### Post by ZenMasta on 2008-04-04
xp pro sp2 :)

---

### Post by Eiríkr on 2008-04-05
Wow, you're getting BSODs on Win XP from a _share_?  That's just messed up.  

This makes me wonder if your share config might include some of the more esoteric options that seem to crop up when certain GUI config tools are used.  Would you be so kind as to post the contents of your smb.conf file?  You can display them by opening a terminal and typing:
```
less /etc/samba/smb.conf
```

Cheers,

Eiríkr

---

### Post by ZenMasta on 2008-04-05
Originally I created the shares with webmin. But I've even deleted them all and remade with swat. there's no difference. Currently the share on the new hd isn't listed but if it was it would be

[music]
	path = /media/disk/music
	read only = No

```
[global]
	workgroup = BLAKE
	server string = samba
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[pics]
	path = /home/Rob/pics
	read only = No

[movies]
	path = /home/Rob/movies
	read only = No
```

Here's one thing I don't understand maybe this is part of the problem? When I connected the hd to my computer in computer/file browser it appears 1 disk  called
/boot with a little post it and pin icon on it and its only 83.9mb
This has some files on it.
2 folders, grub and lost+found
some files that appear to be fedora 5... probably at one point fc5 was on this hd because the files all have fc5 in the name.

i downloaded gnome partition editor and saw another partition which I formatted to ext 3 this is 74 gb
The other one I forget what it was but I reformatted it using ext3 and that's what I've been using.

---

### Post by Eiríkr on 2008-04-05
Your smb.conf file looks sane, so that wouldn't seem to be the issue.  A serious blue-screen like what you describe would then seem to indicate some sort of hardware trouble, but that's outside of my ken.  

Anyone else with any ideas?

Cheers,

Eiríkr

---

### Post by geddeth on 2008-04-24
I'm getting this too, except my box crashes HARD when I save to the share. No BSOD, no nothing.

Is it related to this thread: [http://ubuntuforums.org/showthread.php?t=468151](http://ubuntuforums.org/showthread.php?t=468151) ?

---

