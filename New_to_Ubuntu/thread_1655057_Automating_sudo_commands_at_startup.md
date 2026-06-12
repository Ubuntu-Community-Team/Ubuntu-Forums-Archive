---
title: "Automating sudo commands at startup"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-12-29
Hi guys,

I have an Ubuntu file + print server on our network. It does everything fantastically, but after a reboot, to get printing working again, I need to run the following two commands:

```
family@svlamserver:~$ sudo service smbd restart
smbd start/running, process 1531
family@svlamserver:~$ sudo service cups restart
cups start/running, process 1544
```

Very strange and frustrating.. but is there a way I can automatically run them at startup? I can't just stick them in the gnome startup commands list because it won't run as root (or requests a password, the box is headless).

Thanks.

---

### Post by sisco311 on 2010-12-29
See: [lpbug]494141[/lpbug].

I would try to edit /etc/init/smbd.conf to something like:
```
description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems
          **and started cups**)
stop on runlevel [!2345]

respawn
...
```

---

### Post by vanadium on 2010-12-29
The safest way to achieve what you want is to add your commands to /etc/rc.local. You could compare rc.local with "autoexec.bat" from MS-DOS. Commands included there are run at startup as root. A perfect place to put your two commands, and less risk to break your setup.

[edit]Since this is the Absolute Beginners forum, I add some specifics.
* Press Alt+F2, in the "Run Application" dialog, type "gksudo gedit /etc/rc.local". Supply your login password.
* gedit opens with the file. Insert your commands before the "exit"
* Save and exit gedit.

---

### Post by JKyleOKC on 2010-12-29
+1 on Vanadium's reply, but since rc.local runs as root you should NOT include the "sudo" prefix on the commands.

---

