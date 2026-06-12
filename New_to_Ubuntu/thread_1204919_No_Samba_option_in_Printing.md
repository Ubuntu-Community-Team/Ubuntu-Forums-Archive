---
title: "No Samba option in Printing"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by barabaskid on 2009-07-05
Hello,

I've installed Samba (via packagae manager, selected "samba" and applied along with dependencies) on my 8.10 install, and when I got to System->Administration->Printing and attempt to add a new printer, I do not have the option to "Connect to Windows Printer via Samba" (or however that option is meant to be worded.

Basically, I have a printer hooked up to an XP machine which has a printer hooked up to it, and we share an internet connection through a wireless router (I am wireless, the XP connects to the router via an ethernet cable), so I'd like to me able to print off my laptop by connecting to that printer. I have the printer turned on to sharing (indeed another laptop in the house that runs XP can print from it wirelessly). I've been googling for hours, but to not avail. Any thoughts much appreciated!

Samuel

---

### Post by scrooge_74 on 2009-07-05
When you go to System>Printers

And you try to add a Printer it gives you several conection options one of which is Windows Printer via SAMBA.

I guess you need to have SAMBA comfigured properly to see the other PC first

---

### Post by barabaskid on 2009-07-05
What I am saying is, when I do that, that option isn't listed, even though I SAMBA properly installed via the package manager.

---

### Post by scrooge_74 on 2009-07-05
You got me on this one then, I have no clue what to do, I was following some advice that just said to go to System>Admin>printer and when adding a printer choosing which option for connection.

You may want to check [http://samba.org](http://samba.org) and look in there for the answer or wait till someone reads this thread since by we chatting it gets bumped into the first page ;)

---

### Post by goodwin57 on 2009-08-19
I've got the same problem on my acer aspire one which is running the latest issue (9.04 for the netbook).  With this, it isn't that the option doesn't work, it's that the option isn't even there to try.

I suspect a related problem is not being able to connect to my webdav or windows share by going through "file, connect to server" in an open nautilus (EDIT: or intrepid of whatever it is) window.  I've installed samba...what do I do next, is it as simple as just running it, if so, how do I set it to run at start up?

---

### Post by theozzlives on 2009-08-19
I always go:
```
gksu gedit /etc/samba/smb.conf
```
Under [GLOBAL] you'll see "workgroup=WORKGROUP", change WORKGROUP to your workgroup. Save, exit and do:
```
sudo apt-get install samba
```

It works everytime.

---

### Post by goodwin57 on 2009-08-20
My workgroup is actually called workgroup.  But anyway, I tried what you said, it removed a version of samba and put a different one on but I've not got access to 'samba printer' or whatever the option is, nor can I connect to my windows share...

---

### Post by scrooge_74 on 2009-08-20
You have anything like this in your smb.conf?

comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

If I remember right, I think there is also an option in samba to call your cups server to manage the printing, remember in linux you use cups to send print jobs. But I'm not using samba anymore so I dont remember the exact wording.

It was something like printer = cupsys you need to look this up sorry

---

### Post by goodwin57 on 2009-08-21
samba.conf has those lines.  I left them alone.  There's another section on 'printing' which I found.  I uncommented the last 2 lines:

```
# CUPS printing.  See also the cupsaddsmb(8) manpage in the cuppsys-client package.

printing = cups
printcap name = cups
```

so I went to /etc/cups, sudo gedit cupsd.conf found the line "show printers on the network" and changed browse No to browse Yes.  (As expected) that made no difference.  I can't see anything for cupsaddsmb/I don't know where I'd find something; open to suggestions.

---

### Post by mackkie on 2009-09-29
try 'sudo apt-get install smbclient'

This package does not seem to be installed by default and not necessary to browse samba shares, but IS necessary to add a SAMBA printer.

---

### Post by locketine on 2010-03-16
goodwin57, did you get this figured out? I'm having the same problem after removing everything samba from my system and reinstalling it.

None of the suggestions on this thread helped me.

---

### Post by OliverHaslam on 2012-04-20
Anyone have any luck with this? Same issue here.

---

### Post by Morbius1 on 2012-04-20
If the problem is the same:
> when I got to System->Administration->Printing and attempt to add a  new printer, I do not have the option to "Connect to Windows Printer  via Samba" Then you are most likely missing a few packages:
```
sudo apt-get install smbclient
``````
sudo apt-get install python-smbc
```

---

### Post by OliverHaslam on 2012-04-20
> **Morbius1 said:**
> If the problem is the same:
Then you are most likely missing a few packages:
```
sudo apt-get install smbclient
``````
sudo apt-get install python-smbc
```

Both appear to be installed and up to date.

---

