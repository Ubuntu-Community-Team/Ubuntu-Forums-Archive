---
title: "How to add startup program that requires root privileges?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by d.asahi on 2009-01-07
I'm running 8.04 on a Lenovo T61, and I've been experiencing insufficient cooling fan speed. Others have reported this same issue ([example1]("http://ubuntuforums.org/showthread.php?t=872108")) ([example2]("http://ubuntuforums.org/showthread.php?t=794469")).

As a fix, I installed a program that controls the fan speed ([http://linux.die.net/man/8/fancontrol]("http://linux.die.net/man/8/fancontrol")), which works great--except I have to start it manually each time I turn the computer on, as it requires my root password in order to run.

[LIST=1]
[*]Is there a way to get this program to load automatically every time the computer starts so I don't have to give it the root password each time? (In fact, it doesn't start even though I give it my root password. I have to manually run it and then give the password a second time.)
[*]Alternatively, is there a way to fix my insufficient fan speed problem that won't require all this?
[/LIST]

Thank you very much. :D

---

### Post by kpkeerthi on 2009-01-07
[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by sarang on 2009-01-07
Another idea:
You could add an entry to sudoers using the [FONT="Courier New"]sudo visudo[/FONT] command (use [FONT="Courier New"]sudo -s[/FONT], then [FONT="Courier New"]EDITOR=gedit && visudo[/FONT] if you are not comfortable with vim) that allows you to run that program as the superuser without having to enter the sudo password. Then you could add the sudo version of it to your regular session startup sequence. (For gnome, Preserences -> Sessions -> Add and add sudo program_path as the program to run instead of adding just program_path).

I believe the line that needs to be added to sudoers is:

```

 yourUserName     ALL = NOPASSWD: program_path

```

eg: 
```

sarang ALL = NOPASSWD: /bin/myprogram

```

It is important for security reasons that you specify the full path of your program. Also, please see the sudoers manual at [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

as this (or actually anything you do to make things run as root) has security implications.

---

