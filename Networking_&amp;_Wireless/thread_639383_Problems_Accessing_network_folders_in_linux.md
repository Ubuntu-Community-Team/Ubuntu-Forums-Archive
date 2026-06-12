---
title: "Problems Accessing network folders in linux"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by n.jin on 2007-12-13
iam problem access my shared network folders , i could access network folers from linux to windows but the windows to linux i get an error, tried access my shared folders via localhost but i get this error message " Folder contents could not be displayed, Music couldnt be found, perhaps it has recently been deleted"
taking note this has worked before with no problems,

```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/12/13 19:01:49

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Shared Files]
	path = /home/jeff/Shared Files
	read only = No
	guest ok = Yes

[Music]
	path = /home/jeff/Music
	guest ok = Yes

[Videos]
	path = /home/jeff/Videos
	guest ok = Yes
```

---

### Post by n.jin on 2007-12-13
here is a little screenshot of the error iam getting
[IMG]http://img.photobucket.com/albums/v142/oooo12/Screenshot-1.png[/IMG]
[IMG]http://img.photobucket.com/albums/v142/oooo12/Screenshot.png[/IMG]

---

### Post by n.jin on 2007-12-13
ok while i was waiting for a reply inthis thread i did a little experiment, i tried sharing a folder in my linux os that i havent shared before, for this i shared my tmp folder, now lo and behold my windows os and me was able to access it just fine

[screenshot]("http://img.photobucket.com/albums/v142/oooo12/3.png")


now iam thinking is there a way a could reset everything and start all over again, because what i see here is that i got 3 folders here that used to work just fine before i had that power surge in our area ( me thinks that when this problemstarted) tried deleting and recreating the shared folders again via System>admin>shared folders , which doesnt work BUT tried sharing a new folder which i havent shared before (ie /tmp) and works just fine.

i hope i got the message across, thanks for anyone who would help out.

---

### Post by n.jin on 2007-12-14
bump up

---

### Post by n.jin on 2007-12-14
can anyone point me to the right direction please :(

---

### Post by DrP on 2007-12-14
hi n.jin,

I too am having the same issue except all my pc's now use ubuntu 7.1.  My prob only happened recently for what ever reason.  I did do a system restore using 4BAK to restore my whole partition from a backup image.  Howevere my home dir location is on seperate partition.

But like you I found that sharing a directory I have never shared before would work ok and can be access from other pc's.  but sharing the original shared dirs I had keep saying that perhaps I deleted them.  crap!

however using "system log viewer" i opened a samba log file in the /var/logs/samba/ dir and found the error message and after that it said user permissions denied is the cause.


so thought I'd mention this for a new area of investigation and if you too had made any changes to upset permissions?

DrP.

---

### Post by n.jin on 2007-12-18
hi DrP, 

sorry but i have completely given up hope on this matter since i could not get professional help reagarding this matter, not even a single post just telling me to just reinstall the whole os since there is no cure for it :(

well anyway, i did remember getting that user permission error after my computer booted up after the power surge. just ignore it since it didnt told me which one had changed.

wish i could help you out , i reverted back to winxp (not permanent) just playing this MMO game than wine cant emu, hehe

anwyay i think the problem lies to some table where samba stores the info on the location of each network folder/network path, or so i have read in the samba website, i just dont know how to reset it, iahve already tried uninstalling and reinstalling samba to fix the problem but still no go..checked on the forums..still no answer.. so

i ended up reinstalling the gutsy, works like a charm, problem fixed, but you and i both know its really a hassle doing it just in case this happened again...for me this already happened twice, during a power surge, and everytime, only my local networking gets problems linux side.

i hope this get you an idead on where to look, and if you get to solve this problem please do post here or icq me, thanks good luck friend

---

