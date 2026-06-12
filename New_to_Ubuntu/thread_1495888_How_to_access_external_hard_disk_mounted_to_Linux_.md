---
title: "How to access external hard disk mounted to Linux machine from Windows"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Ladybird78 on 2010-05-28
Hello,

I have Ubuntu Lucid Lynx in one machine and Windows XP in another machine. 
I have connected both machines using Samba.
I have an external hard disk connected to the Linux machine ( /media/MyBook)
I want to share a directory (/media/MyBook/NewData)in the external hard disk so that a user logged in t to the Windows machine can use that directory ( /media/MyBook/NewData) to do his/her analysis.

Thank you

---

### Post by Morbius1 on 2010-05-28
The fastest way is this:

Open Nautilus ( home folder ) > right click on /media/MyBook/NewData

Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete files", and "Guest Access"
Select "Create Share"

Open Terminal and type:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section of smb.conf
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own login user name*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba.

In 10.04:
```
sudo restart smbd
sudo restart nmbd

```If you run into problems post the output of the following commands:
```
net usershare info
testparm -s
```

---

### Post by sudheer penubarthi on 2011-04-28
Excellent post got it working straight away thanks

---

