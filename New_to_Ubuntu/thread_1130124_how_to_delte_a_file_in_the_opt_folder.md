---
title: "how to delte a file in the opt folder ?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by djmh on 2009-04-19
The file "Songbird_1.1.2-1042_linux-i686.tar.gz" cannot be moved to the trash.

Unable to trash file: Permission denied

i moved the tar file to my opt folder while attempting to install songbird , i was unable to install it , but now when i go to delete the file in the opt folder it tells me i cant (see above error message )
i googled how to delete files in the opt folder , but it really didnt make much sense to me .
any help would be appreciated , thanks :)

---

### Post by lolol i r linux noob on 2009-04-19
u have to be root but i wouldnt advise logging in as root its not safe

---

### Post by djmh on 2009-04-19
well , what could happen if i log in as root ?
like if i just log in delete the file and log out ?

---

### Post by dnairb on 2009-04-19
In terminal, type:

```
sudo rm /opt/Songbird_1.1.2-1042_linux-i686.tar.gz
```

Type your login password when prompted, then press <RETURN>

sudo - gives you root access
rm - removes file

---

### Post by Paddy Landau on 2009-04-19
Type this command.
```
sudo rm -i Songbird_1.1.2-1042_linux-i686.tar.gz
```sudo temporarily takes you into root.

---

### Post by HeirPixel on 2009-04-19
> **djmh said:**
> The file "Songbird_1.1.2-1042_linux-i686.tar.gz" cannot be moved to the trash.

Unable to trash file: Permission denied
Use **Alt + F2** and type **sudo rm /opt/Songbird_1.1.2-1042_linux-i686.tar.gz** to remove the file. The same line can be entered into a terminal if you prefer :)

---

### Post by djmh on 2009-04-19
got it , worked perfectly - thanks evryone :D !!!

---

