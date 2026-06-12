---
title: "Schedule a program to start"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Fizwidget on 2009-05-22
I'm having some trouble with gnome-schedule. I simply want to start a program at a specific time. I've tried typing the name of the program ('firefox' or 'deluge' for example) as the command, but the program does not start at the specified time. I've also tried pointing to the program (/usr/bin/deluge for example), but the program still doesn't start!

How do I perform this basic task? I'm not interested in learning how cron works at the moment, I just need to get this up and running.

Thanks.

---

### Post by drs305 on 2009-05-22
When you add an entry into gnome-schedule, it should be reflected in the user's crontab (or root's if you used "gksudo gnome-schedule"). 

So if you have entered the desired commands via gnome-schedule and they aren't working, please post the results of the following and we can see what was entered into crontab and perhaps why it isn't working for you.

```

crontab -l
sudo crontab -l # if entered as root

```

**[COLOR="DarkRed"]ADDED:[/COLOR]** For gui apps, you may need to add a display command, which you would place before the path/command you are entering in gnome-schedule.

Run this command to see which display you are using:
```

ls /tmp/.X11-unix/ 

```
It should return something like: X0

If it is "0", add this to the start of the command line, so it looks like this, and untick /dev/null:
> 
export DISPLAY=:0 && /usr/bin/firefox


I've sent you a PM as your post below was composed as I added to this one.

---

### Post by Fizwidget on 2009-05-22
Here's the output of that command:
```
03 10 * * * deluge >/dev/null 2>&1 #JOB_ID_3
```

As far as I can see, nothing happened at 10:03AM. The Deluge GUI certainly didn't start. I'm sure I'm making a silly mistake...

---

### Post by drs305 on 2009-05-22
Fizwidget, I was adding to my original post at about the same time you were making your second post. Review my first post additions, recommending adding the Display command and unticking the "/dev/null" option in gnome-schedule.

---

### Post by Fizwidget on 2009-05-22
Thanks, that got it working as desired :)

---

