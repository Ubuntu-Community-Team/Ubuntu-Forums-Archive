---
title: "Mac OS X having trouble connecting to Ubuntu Samba"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by AJESQ on 2008-10-19
I am trying to connect my OS X 10.5.5 to my Ubuntu 8.04 computer running samba.

So I do the usual connect to server things smb://192.168.99.69/Archives and get this error:
Connection Failed
You do not have permission to access this server

Now I have had windows and linux pc's connect to this samba shares no problem..... but mac wont. HELP!


smb.config below:
alex@ubuntu:/etc/samba$ cat smb.conf
# Samba config file created using SWAT
# from 192.168.69.104 (192.168.69.104)
# Date: 2008/08/31 10:30:55

[global]
	workgroup = AJSNETWORKS
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	map to guest = bad user
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	valid users = media
	write list = media

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[Movies]
	comment = Movies
	path = /Archives/Movies

[TV]
	comment = TV
	path = /Archives/TV

[Music]
	comment = Music
	path = /Archives/Music

[Software]
	comment = Software
	path = /Archives/Software

[Archives]
	comment = Archives Directory
	path = /Archives
	valid users = alex
	write list = alex

[Recent]
	comment = Recently Downloaded Files
	path = /Archives/Recent
	read only = No
	create mask = 0777

[Home]
	comment = Home Directory
	path = /home/alex
	valid users = alex
	write list = alex

---

### Post by dmizer on 2008-10-20
Try adding these two options to your global section:
```
wins support = no
name resolve order = lmhosts wins host bcast
```

Restart samba before testing:
```
sudo /etc/init.d/samba restart
```

Edit:
Failing that, please take a look here: [http://www.macwindows.com/panther.html](http://www.macwindows.com/panther.html)

---

### Post by AJESQ on 2008-10-20
I tried that.... no luck same issue.

I did test and was able to get a login screen to my room mates vista box... so it seems it has to be an incompatibility with MAC OS X .5.5 and samba...

I checked the link but it didnt seem to have my exact issue...

any other suggestions?

---

### Post by dmizer on 2008-10-20
> **AJESQ said:**
> I tried that.... no luck same issue.

I did test and was able to get a login screen to my room mates vista box... so it seems it has to be an incompatibility with MAC OS X .5.5 and samba...

I checked the link but it didnt seem to have my exact issue...

any other suggestions?

Can you mount by url: go menu > enter url for the server (try with the server's ip address too).

---

### Post by AJESQ on 2008-10-20
Do you mean in Mac OS X how I connect to the server? I go through the "connect to server" menu option.


I have not yet tried auto mounting but don't think it would help any.... I have read that there are problems with leopard and accessing samba servers... but I have not yet found a resolution.

I fear that I might have to call apple support on this... and like for real when was the last time I called tech support for a computer? lol

hope you have another trick up your sleeve.

---

### Post by dmizer on 2008-10-21
I don't have a copy of OSx that will connect to the network, so this is difficult for me.

Try this: [http://blogs.techrepublic.com.com/opensource/?p=173](http://blogs.techrepublic.com.com/opensource/?p=173)

---

