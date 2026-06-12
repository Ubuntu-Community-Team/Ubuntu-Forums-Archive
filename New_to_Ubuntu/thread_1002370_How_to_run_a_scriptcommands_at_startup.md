---
title: "How to run a script/commands at startup?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Tibco on 2008-12-04
I have a problem with ubuntu eating my hard disk, where the load counts are really high, and i have looked at a lot of the threads but none of them seem to work for me (i am using Hardy). But anyway, the command "sudo hdparm -B 255 /dev/sda" works perfectly and stops my load count from increasing. How do i make this command run when ever i log in?

Bonus question: is there any way i can also get this command to run at the resume from hibernate? I am using Kpowersave in gnome, because it works better for me than PM-UTILS, if that is helpfull.

---

### Post by glennric on 2008-12-04
You could create an init script that will run at boot.

Put the command
```
hdparm -B 255 /dev/sda
```
in a new script in the directory /etc/init.d
Make sure to set that file as executable.
Then type 
```
sudo update-rc.d script-name start 01 S .
```
Make sure to use whatever you name the file for script-name.

As to resuming from hibernation, I could help you get this script to run if you were using pm-utils, but I don't know how to do it with KPowersave.

---

### Post by jpkotta on 2008-12-05
The traditional place to add such things is /etc/rc.local.  AFAIK, all ACPI frontends use the stuff in /etc/acpi/.  Put a script in /etc/acpi/resume.d/.

---

### Post by Shwefty on 2008-12-05
If you prefer the GUI approach, you could put it in Sessions.

System -> Preferences -> Sessions

---

