---
title: "Crontab tutorial.."
date: 2009-08-23
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-23
I have heard that by editing crontab file we can run a program / command at specific time intervals,but i dont know how to do this.Can someone explain me about crontab and give me some working examples?Thanks in advance..

---

### Post by Paddy Landau on 2009-08-23
I don't think that there's a GUI for this.

Open a terminal (Applications > Accessories > Terminal) and use the manual to find out more. Here are the commands you want:
```
man cron          # Some background
man crontab       # Some more background
man 5 crontab     # The syntax to use when editing a crontab file
```Experiment before putting anything into production.

---

### Post by Penguin Guy on 2009-08-23
To edit your crontab you type [COLOR="Green"]crontab -e[/COLOR]. You should see output such as the below:
```
# m h  dom mon dow   command
```
This simply means:
```
**m**inute, **h**our, **d**ay **o**f **m**onth, **mon**th, **d**ay **o**f **w**eek, **command** to run
```

Here is my crontab (used to do a backup every Sunday):
```
# m h  dom mon dow   command
  0 0  *   *   Sun   /usr/local/bin/backup
```
If, for example, I don't turn my computer on on Sunday, it will backup the next time the computer is turned on.

If I wanted it to backup at 9:00 on the first day of every month I would use:
```
# m h  dom mon dow   command
  0 9  1   *   *     /usr/local/bin/backup
```

You can figure out the rest.

---

### Post by SnappyU on 2009-08-25
> **Paddy Landau said:**
> I don't think that there's a GUI for this.

Open a terminal (Applications > Accessories > Terminal) and use the manual to find out more. Here are the commands you want:
```
man cron          # Some background
man crontab       # Some more background
man 5 crontab     # The syntax to use when editing a crontab file
```Experiment before putting anything into production.

There is a GUI scheduler for Ubuntu.  
Accessories > System Tools > Gnome Scheduler

---

### Post by Paddy Landau on 2009-08-25
> **SnappyU said:**
> There is a GUI scheduler for Ubuntu.  
Accessories > System Tools > Gnome Scheduler
Cool! I hadn't known about that.

For clarification, you need to install *gnome-schedule* (you can do this from Synaptic Package Manager). For me, it didn't add itself to the menu; I had add it manually. Or, from the terminal, run *gnome-schedule*.

---

### Post by kpkeerthi on 2009-08-25
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

