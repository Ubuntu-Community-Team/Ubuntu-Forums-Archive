---
title: "cron tasks wont run on schedule"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by corkscrew on 2008-12-14
I have installed Gnome Schedule 2.0.2 to run a simple backup script i wrote (my first script) it simply copies my data directorys from one drive to another.
The script runs fine from a terminal. I have added it to Gnome schedule and want it to run every day. the task will run ok if i run it from within Gnome schedule but it will not automatically run?

Any help would be greatly apreciated

---

### Post by drs305 on 2008-12-14
> **corkscrew said:**
> The script runs fine from a terminal. I have added it to Gnome schedule and want it to run every day. *[COLOR="DarkRed"]the task will run ok if i run it from within Gnome schedule[/COLOR]* but it will not automatically run?
Do you mean you can manually start it from within gnome schedule with the 'Run task' button?

In the setup, you should see "Recurrent", "On Every Day at XXXX" or similar, and a Command Preview. You should also make sure you use the full path to the commands in your script.

In any case, if you post the script we can take a look at it and perhaps help.

---

### Post by corkscrew on 2008-12-14
yes sorry I can manually start it from within gnome schedule with the 'Run task' button
it works perfectly like that, and yes I have it set up "recurrent" i try setting it for a few minutes in advance of the current time to see if it runs but it passes the time and nothing happens

---

### Post by drs305 on 2008-12-14
Please post the command(s) you are trying to run.

---

### Post by corkscrew on 2008-12-14
> **drs305 said:**
> Please post the command(s) you are trying to run.
 ok hereit is ```
cp -dpRuvx /data/user /media/sata2-data/usercopy
```
 Dont know if the fact that the source is on an ext3 drive and the destination is a ntfs, having said that if i run the above command as a script or just in a terminal it runs fine

---

