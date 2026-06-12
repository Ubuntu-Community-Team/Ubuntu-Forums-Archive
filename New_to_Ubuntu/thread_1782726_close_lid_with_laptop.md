---
title: "close lid with laptop"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by VVAW on 2011-06-15
I have a laptop hooked up to a monitor I can't close my lid 
how to enable close lid DO NOTHING.

I am also trying to ugrade to 11.04 currently have  10.10 keeps failing saying need 10.04tls what does that mean

1 last thing how do I map a samba drive permantly every time I reboot I have to connec to server

---

### Post by cariboo on 2011-06-15
> **VVAW said:**
> I have a laptop hooked up to a monitor I can't close my lid 
how to enable close lid DO NOTHING.

I can';t help with the exact command, as I'm running Oneiric, but power settings menu item is under system

> I am also trying to ugrade to 11.04 currently have  10.10 keeps failing saying need 10.04tls what does that mean

Press Alt-F2 and type:

```
update-manager -d
```

> 1 last thing how do I map a samba drive permantly every time I reboot I have to connec to server

You can map the drive you want to automagically mount in /etc/fstab, the command should look something like this:

```
//willy/media/music /media/music smbfs auto,username=,password=,uid=1000,umask=000,user  0  0
```

//willy/media/music = the share name on the server
/media music = the mount point on the client
smbfs = file system type
username and password = should be self evident

---

### Post by VVAW on 2011-06-15
thanks 
I go through update I think it fails at file 75.

In the power settings there is no option to do nothing
just suspend,blank monitor, or shutdown

Whe I map the drive if I reboot it is no longer there..

---

### Post by LadySapphira on 2011-06-15
To enable close lid do nothing:

System > Preferences > Power Management
That will bring you to those settings.


Are you trying to upgrade through update manager?  You could try going to Synaptic Package manager, looking up the file it's looking for.  Could you give the exact file name?
Cariboo probably knows more about this than me.

---

### Post by VVAW on 2011-06-15
system>preference>Power managment  
In the power settings there is no option to do nothing
just suspend,blank monitor, or shutdown

---

### Post by Maheriano on 2011-06-15
Try grabbing the top of the lid with one hand and pulling towards you. It should close.

---

### Post by TBABill on 2011-06-15
> **Maheriano said:**
> Try grabbing the top of the lid with one hand and pulling towards you. It should close. LOL!!!! That one made me giggle just at the pure genius of the sarcasm. 
 
Power management must be missing a setting if you can't choose for it to ignore laptop lid closing.

---

