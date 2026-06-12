---
title: "File sharing trouble!"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by lewbram on 2009-02-12
Hi,

I am trying to share files and printer form my ubuntu machine with my vista laptop.

Something has been setup but I don't know how I did it! When I go to 'places', 'networks' there is a shared file there but it has a password and I do not remember ever setting a password. Is there anyway I can remove this and start again?

Thanks
Lew

---

### Post by eastexsteve on 2009-02-12
> **lewbram said:**
> Hi,

I am trying to share files and printer form my ubuntu machine with my vista laptop.

Something has been setup but I don't know how I did it! When I go to 'places', 'networks' there is a shared file there but it has a password and I do not remember ever setting a password. Is there anyway I can remove this and start again?

Thanks
Lew

From my limited ubuntu experience, you should be able to access that file by using the password you use when you log on to the ubuntu machine.  Do some reading on Samba and how it works, and the smb.conf file.  When I set up file sharing for windows on my ubuntu 8.10 machine, this is the package it installed.

---

### Post by Voland on 2009-02-12
lewbram, type ```
gksu shares-admin
``` in terminal and review your settings. Also post here your /etc/smb.conf file. We can see if you add access to your shares.

---

### Post by superprash2003 on 2009-02-12
use advanced file sharing in windows [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx)

---

### Post by lewbram on 2009-02-12
> **Voland said:**
> lewbram, type ```
gksu shares-admin
``` in terminal and review your settings. Also post here your /etc/smb.conf file. We can see if you add access to your shares.


lewbram@lewbram-desktop:~$ gksu shares-admin

** (shares-admin:6078): CRITICAL **: Unable to lookup session information for process '6078'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(shares-admin:6078): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

---

### Post by Kellemora on 2009-02-12
Hi Lew

If you are ON the Ubuntu machine, looking at a Doze machine, usually all you need to do is just hit the enter key WITHOUT putting in a password.

At least on  XP-Home, XP-Pro, XP-MCE and XP-Pro-MCE that is!

Have no idea if that will work on the Ultimate Spyware OS though.

TTUL
Gary

---

### Post by cariboo on 2009-02-12
No matter what anyone else says smbclient wants a password to connect to Windows shares. Open a Applications-->Accessoreis-->Terminal and type:

```
sudo smbpasswd -L -a <user name>
```

The above command will ask you to create a samba password, I always use the password I use to login. Next

```
sudo smbpasswd -L -e <user name>
```

This enables the users and allows him to connect to the Windows share.

one of the previous posters gave you the command gksu shares-admin, to use this command press Alt-F2 and then type the command.

Jim

---

