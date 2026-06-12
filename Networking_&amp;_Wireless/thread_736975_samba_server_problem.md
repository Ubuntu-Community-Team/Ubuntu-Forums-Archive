---
title: "samba server problem"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by switchcase on 2008-03-27
Hi, if anyone can help with my problem, it would be greatly appreciated.

I have recently set up Samba on my Ubuntu box (gutsy) to share files with an Win XP machine across a LAN using a router. The XP machine has a wired connection while the Ubuntu machine uses a wireless connection. I have two shares set up ('LANSHARED' and 'MOVIES'). 'LANSHARED' is located in my home folder of the Ubuntu setup and MOVIES is on an external hard drive connected to the same machine but is read-only. On the XP machine I have these network shares mapped as drives Y and Z. Everything on LANSHARED seems to work without any problems, however whenever I try to access files from MOVIES Ubuntu crashes (it just freezes). Sometimes Ubuntu will also freeze when running Azureus (torrent manager), I'm not sure if this is related.

Here's the contents of the Samba configuration file:
> 
[global]
	workgroup = mshome
	server string = %h server (Samba, Ubuntu)
	security = share
	name resolve order = lmhosts hosts
	wins support = yes

[LANSHARED]
	path = /home/chris/LANSHARED
	force user = chris
	force group = users
	comment = Windows Share
	available = yes
	browsable = yes
	public = yes
	writable = yes
	guest ok = yes

[MOVIES]
	comment = Movies Network Folder
	path = /media/EXTNL HDD/Movies
	force user = chris
	force group = users
	writable = no
	browseable = yes
	public = yes
	guest ok = yes


Thanks in advance for any help. I'm baffles as to what's causing the problem. :confused:

Chris. :)

---

### Post by Eiríkr on 2008-03-27
Ubuntu locking up entirely doesn't sound like a Samba problem.  Can you access the external drive after logging into Ubuntu directly (i.e. not through Samba)?  When using Azureus and Ubuntu freezes, are you saving the torrent to your external drive?

Looking at your conf file, 
[list][*][font=courier]public = yes[/font] and [font=courier]guest ok = yes[/font] are synonyms, so you only need one or the other.
[*][font=courier]browsable = yes[/font] is the default, so you can delete this line altogether to simplify your file.
[*][font=courier]available = yes[/font] is also the default, so you can delete this line too.
[*][font=courier]writable = no[/font] is a synonym for [font=courier]read only = yes[/font], which is again the default.  
[*]I notice you have [font=courier]wins support = yes[/font], but you don't include "wins" in your [font=courier]name resolve order[/font] line...?  But then again if it works, I guess it's okay.  ;)[/list]

Anyway, I'd definitely check that your external drive is functioning properly.  A full-on OS lockup is usually an indication of a bad driver or a bad part.  

Cheers,

Eiríkr

---

### Post by switchcase on 2008-03-28
I can access the external drive with no problems whatsoever, or at least it seems. It does seem to be functioning correctly. Is there any tests I can run to check this further? Oh and, Azureus does not access this drive, only my internal one.

Azureus sometimes will run without incident and other times Ubuntu will crash at what seems a random point. The crashes don't occur at any particular point in using Azureus. It also seems that a crash is less likely to occur while running Azureus, if it is the only program I have running.

I have made the changes you suggested to the Samba configuration file and restarted the Samba, yet it doesn't seem to have made any difference. I'm a little stuck as of what to do. I guess one option is to scrap the MOVIES share and copy files from the external drive to LANSHARED.


Thanks for your reply.
Chris.

---

### Post by Eiríkr on 2008-03-28
Next time you crash, have a look towards the end of your syslog file and see if there's anything that might indicate what's going on:
```
less /var/log/syslog
```

If the crash is due to a software glitch, or to a hardware glitch that the software notices, *something* should be posted through to the syslog.  I'd also recommend keeping a notepad near your machine and jotting down what you were doing and what programs were open when you crash to see if you might be able to narrow down what's going on.  The only hard lock-ups I've had on my various Linux distros had to do with either bad drivers, or bad hardware, but who knows.  These are big complicated systems, and it's really more of a surprise that things don't go boing more often.  

Cheers,

Eiríkr

---

### Post by switchcase on 2008-03-29
Ill have a look into that. =) Thanks for the help.

---

### Post by Iowan on 2008-03-30
Although probably not the issue, the space in > path = /media/EXTNL HDD/Movies *might* be confusing the OS. You might need to "escape" the space - or rename the directory (mount).

---

### Post by Eiríkr on 2008-03-30
@Iowan --

You'd think so, but smb.conf file parsing actually doesn't barf on either spaces or apostrophes within paths (I've got paths with both in my smb.conf file).  Escaping such characters in conf file paths will actually cause Samba to balk.  

Cheers,

Eiríkr

---

