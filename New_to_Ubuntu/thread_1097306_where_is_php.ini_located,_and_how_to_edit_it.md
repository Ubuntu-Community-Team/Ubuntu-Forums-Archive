---
title: "where is php.ini located, and how to edit it"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by InternetDominus on 2009-03-15
Hi, I have installed xampp at /opt/lampp/lampp but have no way to find php.ini.

I need to modify it so I can upload via phpmyadmin a 2mb sql file

Also, how do I edit files? If I use Place -> Home Folder I see all folder, and browse file, I open files,but when try to modify them, I have no permission

how do I get such permission?   

Or, am I only to modify files via terminal?

Thanks,

ID

---

### Post by chrisod on 2009-03-15
From the terminal, type sudo nautilus, then type your password. This will give you the file manager with root privileges. Then you can right click on a file and edit permissions. Be careful though - you can screw up your system if you edit / delete the wrong file.

Also, aren't .ini files a Windows thing? I don't think I've ever seen them used in Linux.

---

### Post by stmiller on 2009-03-15
Open a terminal and type:


```

sudo gedit /etc/php5/apache2/php.ini

```

:)

---

### Post by mvalviar on 2009-03-16
If you installed xampp under /opt it should be

```
/opt/lammp/etc/php.ini
```

alternatively you can direct your browser to localhost and go to phpinfo(), Ctrl-F and find "Loaded configuration file". That should give you the complete path of php.ini

To edit hit Alt-F2, type gksudo gedit /opt/lampp/etc/php.ini

---

