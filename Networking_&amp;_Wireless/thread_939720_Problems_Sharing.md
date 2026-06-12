---
title: "Problems Sharing"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by polraudio on 2008-10-06
Im doing a school project where i have to network 3 ubuntu computer to file share between each other and i keep getting this error.
I dint know what the problem is. Any help will help alot.
```
Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
```

---

### Post by Archmage on 2008-10-06
It looks like the directoy /var/run/samba is missing. Maybe you need to create it or change the settings in the configuration.

But allow me to point out that Samba for Ubuntu-only-PCs is a waste of resources, since they are much better ways to share between them. NFS is easy to use, but if you need a higher security, you should look somewhere else.

---

### Post by polraudio on 2008-10-06
I dont have the directory and i cant install/download stuff on the computer due to some restricted access. I cant edit the config file it says im not the owner. So what would be my options.

---

### Post by superprash2003 on 2008-10-06
please post your smb.conf file .. in your terminal type sudo /etc/init.d/samba start and what post output?

---

### Post by Iowan on 2008-10-06
"sudo" *might* help with ownership problem. [SSHFS]("https://help.ubuntu.com/community/SSHFS") is another option, but instructor may have limited the options...

---

### Post by polraudio on 2008-10-08
> **superprash2003 said:**
> please post your smb.conf file .. in your terminal type sudo /etc/init.d/samba start and what post output?
Here is what i get
```
/etc/init.d/samba: command not found
```

> **Iowan said:**
> "sudo" *might* help with ownership problem. [SSHFS]("https://help.ubuntu.com/community/SSHFS") is another option, but instructor may have limited the options...
 I just get a page load error every time.(Network Timeout)

---

### Post by superprash2003 on 2008-10-08
did you add sudo?

---

### Post by Iowan on 2008-10-08
> **polraudio said:**
> ...
/etc/init.d/samba: command not found
Did you enter ```
sudo /etc/init.d/samba start
``` - I get that message if I don't include an option (start, stop, or restart).
> **polraudio said:**
> I just get a page load error every time.(Network Timeout) What causes the page load error?

[rephrase] What command do you issue that causes the page load error to appear?

---

