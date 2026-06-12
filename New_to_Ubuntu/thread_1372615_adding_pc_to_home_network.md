---
title: "adding pc to home network"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-04
Hello friends

Could you please show me how to add pc running Ubuntu to my home network?I need to change workgroup name in order to share printer connected to other pc running vista.
Thank you in advance for the lecture.

---

### Post by ikt on 2010-01-05
> **manny43 said:**
> Hello friends

Could you please show me how to add pc running Ubuntu to my home network?

Heya!

For most machines all that it requires is plugging an ethernet cable into a modem/router running with DHCP, an ethernet cable is just a typical network cable, usually blue, and most typical modem routers run with DHCP already, so really you should be ready to go right off the bat.

> **manny43 said:**
> 
I need to change workgroup name in order to share printer connected to other pc running vista.
Thank you in advance for the lecture.

What version of ubuntu are you running?

If you're sharing a printer connected to your ubuntu computer with the vista machine, the vista machine should be able to see your printer unless I'm missing something. 

Hope everything works out for you :)

---

### Post by Morbius1 on 2010-01-05
Although I contend that having the same workgroup name on all machines in a network is not required, I think I'm going to give up on that battle.

To change the workgroup name:

Open **Terminal**
Type [B]gksu gedit /etc/samba/smb.conf

[/B]Look for a line at the begining of the file that looks like this:

> # Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroupAnd change the workgroup after the "=" to whatever you want.

Save the file, exit gedit, and back in the terminal:
**sudo service samba restart**

---

### Post by theozzlives on 2010-01-05
> **Morbius1 said:**
> Although I contend that having the same workgroup name on all machines in a network is not required, I think I'm going to give up on that battle.

To change the workgroup name:

Open **Terminal**
Type [B]gksu gedit /etc/samba/smb.conf

[/B]Look for a line at the begining of the file that looks like this:

And change the workgroup after the "=" to whatever you want.

Save the file, exit gedit, and back in the terminal:
**sudo service samba restart**

I agree, but I would do:
```
sudo /etc/init.d/samba restart
```

If you don't have samba installed, change your smb.conf, then do:
```
sudo apt-get install samba
```
then:
```
sudo smbpasswd -a <username>
```

Where <username> is would be your username.

---

