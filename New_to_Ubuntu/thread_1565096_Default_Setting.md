---
title: "Default Setting"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by SEECo on 2010-08-31
How to set everything to the default in kubuntu. Plz tell any command if possible.

---

### Post by limestone on 2010-08-31
Re-install, if you don't have set some rescue or return point..

---

### Post by vagrale13 on 2010-08-31
> **SEECo said:**
> How to set everything to the default in kubuntu. Plz tell any command if possible.
If you want all user settings, just create a new user!

---

### Post by SEECo on 2010-08-31
I have got my very important data in it any other way to do it.

---

### Post by SEECo on 2010-08-31
Any thing else pppppppplllllllllllllllleeeeeeeeeeeeeeeaaaaaaaaaaaaassssssssssssseeeeeeeeeeeee.

---

### Post by Elfy on 2010-08-31
don't bump so soon.

---

### Post by ankspo71 on 2010-08-31
> **SEECo said:**
> How to set everything to the default in kubuntu. Plz tell any command if possible.

Hi, the majority of your kde settings are in a folder named .kde inside your home folder. Renaming this folder will give you a backup of your kde settings and force kubuntu to use the default settings.

The following command will rename the .kde folder to .kde-backup
```
mv ~/.kde ~/.kde-backup
```

Now all you need to do is restart (or logout and login). Here is a command to restart if you need it:
```
sudo reboot
```
Hope this helps.

---

### Post by SEECo on 2010-08-31
Does this this command work for gnome if we replace 'kde' with 'gnome'.

---

### Post by andrewthomas on 2010-08-31
no

---

### Post by SEECo on 2010-08-31
Well her are the results of doing this:

fahad@dell-server:~$ mv ~/.kde ~/.kd backup
mv: target `backup' is not a directory
fahad@dell-server:~$

---

### Post by andrewthomas on 2010-08-31
> **SEECo said:**
> Well her are the results of doing this:

fahad@dell-server:~$ mv ~/.kde ~/.kd backup
mv: target `backup' is not a directory
fahad@dell-server:~$
```
mv ~/.kde ~/.kde.backup
```copy and paste.  you made a typo

---

### Post by SEECo on 2010-08-31
It didn't worked. The results are below:

fahad@dell-server:~$ mv ~/.kde ~/.kd backup
mv: target `backup' is not a directory
fahad@dell-server:~$

---

### Post by andrewthomas on 2010-08-31
> **SEECo said:**
> It didn't worked. The results are below:

fahad@dell-server:~$ **mv ~/.kde ~/.kd backup**
mv: target `backup' is not a directory
fahad@dell-server:~$
> **andrewthomas said:**
> [CODE**]mv ~/.kde ~/.kde.backup**[/CODE]copy and paste.  you made a typoSee the difference?

```
mv ~/.kde ~/.kde.backup
```**copy and paste.  you made a typo**

---

