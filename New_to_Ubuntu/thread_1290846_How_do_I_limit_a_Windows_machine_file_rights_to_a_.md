---
title: "How do I limit a Windows machine file rights to a users /home folder on Ubuntu server"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-10-14
I have got a rather rudimentary Jaunty Server running and have setup 3 other Ubuntu machines to access the individual users /home folder.  On my laptop I access my /home folder on the Server, my father accesses his /home folder on the server, and my desktop accesses my /home folder on my server. So all is running sweet on the Ubuntu side.

However, I am having difficulty understanding what Samba requires for my sister who uses a Windows XP laptop to access her /home folder on the Ubuntu server. I can see the printer from the Windows machine but if I try to access anything else it just tells me I haven't got permissions.

Basically what I want/need is for the Windows laptop to be able to access, read, and write files to my sisters /home folder and the family /home folder which has been setup. I do not want it to be able to access anything else apart from being able to print off the servers printer. Is this possible? if so how do I go about achieving this?

All help greatly appreciated.
Thanks in advance.
Michael.

---

### Post by swerdna on 2009-10-14
Your sister's laptop must have the same workgroup name as the Ubuntu server and your sister must be added to the Samba user database on the Ubuntu server.

---

### Post by k3lt01 on 2009-10-14
Thats all done and I am still just seeing the Printer on the server. If I try to look for anything else Windows just tells me I haven't got permissions.

---

### Post by swerdna on 2009-10-14
Q1: What address do you use to try to goto your sister's home folder from her machine, is it \\servername\sisters_linux_username?

Q2: And, you should be able to log to her home folder from every windows machine using that address, can you?

Q3: And please post the results of this command on the server:```
pdbedit -L
```

Q4: and this command:```
testparm -s
```

Q5: and this:```
ls -l /home
```

---

### Post by k3lt01 on 2009-10-14
Thanks for your help I appreciate it.
> **swerdna said:**
> Q1: What address do you use to try to goto your sister's home folder from her machine, is it \\servername\sisters_linux_username?I had read a few things before I posted and they had indicated all I needed to do was use \\fiona@10.1.1.5\ and that would allow us to get in. Needless to say that didn't work, I then posted this thread. In the time after your initial reply, I took a look at your page, nice work btw, and used \\10.1.1.5\fiona and that didn't work either. However, using just \\10.1.1.5\ allowed me to see the printer, which wasn't even turned on, and a "Printer & Fax" folder. Any other attempts to access her Ubuntu /home folder just get the "permissions" message.

I have also restarted Samba a few times, each time checking to see the changes applied to the smb.conf file are still saved, to see if anything was hanging on therefor stopping a successful login.

> **swerdna said:**
> Q2: And, you should be able to log to her home folder from every windows machine using that address, can you?We only have one Windows machine, my sisters laptop, so I don't know if we can log in using another machine or not.

Actually, I have  a spare hdd for my laptop that has XP on it. I will try that in the morning and see if that can access the correct /home folder.

> **swerdna said:**
> Q3: And please post the results of this command on the server:```
pdbedit -L
```

Q4: and this command:```
testparm -s
```

Q5: and this:```
ls -l /home
```I will do this in the morning, all the other machines are now turned off, server included.

Thanks again for your help.

---

### Post by k3lt01 on 2009-10-14
> **swerdna said:**
> Q1: What address do you use to try to goto your sister's home folder from her machine, is it \\servername\sisters_linux_username?Tried this again and it still wont get into her /home.

> **swerdna said:**
> Q2: And, you should be able to log to her home folder from every windows machine using that address, can you?no dust storm today so I have to get outside to clean up, will probably try this tonight.

> **swerdna said:**
> Q3: And please post the results of this command on the server:```
pdbedit -L
```
```
sudo pdbedit -L
[sudo] password for michael: 
nobody:65534:nobody
michael:1001:michael,,,,
fiona:1002:fiona,,,,
charles:1003:charles,,,,
janet:1004:janet,,,,
```

> **swerdna said:**
> Q4: and this command:```
testparm -s
```
```
testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
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

```

> **swerdna said:**
> Q5: and this:```
ls -l /home
```
```
ls -l /home
total 36
drwxr-xr-x  9 charles charles  4096 2009-08-30 10:29 charles
drwxr-xr-x 22 fiona   fiona    4096 2009-10-14 13:12 fiona
drwxr-xr-x  2 janet   janet    4096 2009-08-29 12:02 janet
drwx------  2 root    root    16384 2009-08-29 09:41 lost+found
drwxr-xr-x 24 michael michael  4096 2009-10-15 06:47 michael
```

Have to go and do some cleaning up now :(
Thanks again for your help

---

### Post by swerdna on 2009-10-14
I think we might be onto something here. Check in the directory /var/lib/samba/usershares with this command:```
ls -l /var/lib/samba/usershares
```That should show any shares that you made with the sharing tool in Nautilus. What do you see from that command?

---

### Post by k3lt01 on 2009-10-14
> **swerdna said:**
> I think we might be onto something here. Check in the directory /var/lib/samba/usershares with this command:```
ls -l /var/lib/samba/usershares
```That should show any shares that you made with the sharing tool in Nautilus. What do you see from that command?Total 0

So I'm going to have to go through the entire procedure again to see what's gone wrong.

---

### Post by swerdna on 2009-10-14
> **k3lt01 said:**
> Total 0

So I'm going to have to go through the entire procedure again to see what's gone wrong.

No you don't have to go through it again. I was targeting usershares because no shares were defined in smb.conf:

There are two types of shares:
[LIST=1]
[*]usershares are created with the sharing tool in Nautilus which makes a config file for each share and stores it in /var/lib/samba/usershares
[*]Classical shares are created by putting one stanza for each share into the file smb.conf.
[/LIST]
At the time you last posted, you had no usershares because there's nothing in the directory /var/lib/samba/usershare and you had no classical shares because no shares were defined in smb.conf. So at that time you had no shares at all.No wonder your sister can't log on.

So now create the roaming share which allows private share access for each Ubuntu user, access to the user's home directory.

To do that you put these lines in a paragraph (known as a stanza) in the bottom of the file smb.conf. Here's the stanza/share/code:
```
[homes]
comment = Home Directories
browseable = no
read only = no
create mask = 0775
directory mask = 0775
valid users = %S
```

Open smb.conf with su powers using this command:```
gksu gedit /etc/samba/smb.conf
```

And put the code at the bottom.

restart all participating machines, sequentially, waiting for each to finish booting before starting the next.

Then you should be asked for credentials when you use this address in windows ```
\\servername\username or \\server IP\username
```

---

### Post by k3lt01 on 2009-10-14
Got it working.

Swerdna, your a legend.

The problem was the server wasn't saving the changes I made, I don't know why but it has now. I went back and changed the relevant parts, again. I had to delete fiona as a Samba user and add her back in, yes even though Samba showed no users she was still in the system and had to be deleted before I could add her properly. I then restarted Samba, rebooted Windows Explorer on the XP laptop went to My Network Places > Workgroup > server > Windows asked for the log in and it logged in.

I am now going to copy her files into her /home directory for her and teach her how to use the server.

WooHoo :guitar:

Thanks mate, your knowledge and help is greatly appreciated.

---

### Post by swerdna on 2009-10-15
Glad to help -- enjoy

---

