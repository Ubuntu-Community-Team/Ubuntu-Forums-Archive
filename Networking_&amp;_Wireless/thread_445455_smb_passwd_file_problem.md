---
title: "smb passwd file problem"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by krisbowen on 2007-05-15
Hello all,
After a break from Ubuntu Dapper, I have reinstalled Fiesty Desktop on an Acer laptop.
great distro! Seamless beryl on an Intel shared graphics card..everything works well..wireless okay after loading the broadcom drivers.

I am attempting to set up this lappy as a server for file sharing to both a XP lappy and a Vista lappy.

I followed this guide : 

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

I have installed and updated Samba with the only issue being assigning a new password.

here is terminal output:

kris@ubuntu-laptop:~$ sudo smbpasswd -a 'whoami'
New SMB password:
Retype new SMB password:
Failed to modify password entry for user whoami


Any suggestions on where to go from here????

---

### Post by dolphin_oracle on 2007-05-16
You may need to set up your user under ubuntu first.  The guide you cited indicates to make sure any users are setup under unbuntu first.

good luck!

---

