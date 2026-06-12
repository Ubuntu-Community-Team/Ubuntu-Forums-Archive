---
title: "Scheduling a program to automatically start/stop"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by jestinjoy on 2009-04-15
Hi,
        
          I want to automatically start/stop a program(gwget,bittornado gui) at specific time.I tried the program GNOME Schedule.The task is shown cleared at a specific time, but it is not executed. Also I tried adding to cron jobs,but it didnt get executed.Please help.

---

### Post by DGortze380 on 2009-04-15
```

man crontab

```

---

### Post by lykwydchykyn on 2009-04-15
I'm not familiar with GNOME schedule, but if they're graphical programs, you will probably need to specify a DISPLAY environment variable and be logged in when it runs.

You might want to check /var/log/syslog for error messages around the time they were supposed to run.  

If they say something about not being able to open the display, you'll need to do something like this for your command:
```

export DISPLAY=:0 && mycommand

```

---

### Post by pzaw on 2011-06-16
hi

I am also looking for a way to stop torrent programs.
All torrent programs are either good at dl or good at scheduling but not both in my experience.

I have tried using schedule task. It runs the program but it does not stop it. I can kill the process.
Now I don't know if it will corrupt the download or not. If one of you experts can tell me.
I have been getting a lot of ISOs with emoty data. ie it would report 4G ISO but when you look at it it is empty. I am not sure why this is may be because of dummy files or because of the Kill command

I assumed if the last packet was corrupt torrent would have enough sense to re-download that packet when the DL program is run the next time.

****WARNING*****
care must be taken it could accidentally kill all essential processes!!!!
anyway this commend is successful but I am not guaranteeing: killall -9 nameofyourorogram
****WARNING*****

BE warned

pzaw

---

### Post by Cheesehead on 2011-06-17
You're supposed to stick around the swarm and seed.

1) Show us the crontab commands.
2) Tell us how you installed them.
3) If they run a script, show us the script.
4) Check for any cron or script error messages in /var/log/syslog at the times your cron jobs were supposed to run. If any, show us those, too.

---

