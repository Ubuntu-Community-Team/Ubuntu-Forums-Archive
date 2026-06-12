---
title: "shutdown-at-night"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by seanarickymurphy on 2010-11-27
Is their a way to have shutdown-at-night shutdown at specific times?

---

### Post by marl30 on 2010-11-27
> **seanarickymurphy said:**
> Is their a way to have shutdown-at-night shutdown at specific times?

There is this program in the software center called qshutdown that does exactly that.

---

### Post by Cheesehead on 2010-11-27
The 'gshutdown' and 'kshutdown' packages provide advanced shutdown options with a GUI. 

If you prefer command line, you can have a cron job shut down the system at any time you wish. Of course, if you are working late one night, it might shut down on you...and then not shut down later that night. (There are ways to prevent shutdown if you are still logged in, but you must remember to include one in your script). Google 'cron tutorial' for some great info on how to use this powerful tool.

Or the command-line 'shutdown' command is quite flexible, and you can set (or script) a shutdown hours in advance. Handy for shutting down the system after a specific  job or at a specific time as part of a larger set of actions. See 'man shutdown'.

---

### Post by marl30 on 2010-11-27
> **Cheesehead said:**
> The 'gshutdown' and 'kshutdown' packages provide advanced shutdown options with a GUI. 

If you prefer command line, you can have a cron job shut down the system at any time you wish. Of course, if you are working late one night, it might shut down on you...and then not shut down later that night. (There are ways to prevent shutdown if you are still logged in, but you must remember to include one in your script). Google 'cron tutorial' for some great info on how to use this powerful tool.

Or the command-line 'shutdown' command is quite flexible, and you can set (or script) a shutdown hours in advance. Handy for shutting down the system after a specific  job or at a specific time as part of a larger set of actions. See 'man shutdown'.
Good info; however, I noticed that Gshutdown refused to work and only logs off when you set it to shutdown. Kshutdown on the other hand only seem to work on KDE. Qshutdown is the only one in the repository that actually does what it says it does. 

What I want to know about the command line timed shutdown before I look more into it... does it allow you to set like the days you would like your computer to shutdown at a specific time, allowing it to have a different shutdown time some days, and none on others?

---

### Post by madjr on 2010-11-27
> **marl30 said:**
> Good info; however, I noticed that Gshutdown refused to work and only logs off when you set it to shutdown. Kshutdown on the other hand only seem to work on KDE. Qshutdown is the only one in the repository that actually does what it says it does. 

What I want to know about the command line timed shutdown before I look more into it... does it allow you to set like the days you would like your computer to shutdown at a specific time, allowing it to have a different shutdown time some days, and none on others?

you have to start gshutdown with root privilages

i added this to the launcher:
gksu /usr/bin/gshutdown

might be a little inconvenient for some, but by asking for your password, other people cant launch it in case they are using your computer.

anyway the packager should probably fix this, as many think it doesnt work.

---

### Post by nm_geo on 2010-11-27
I think a cron job or script with would be cool.  Checking on how to myself now.


```
[COLOR=red]sudo shutdown -h -P 24:00[/COLOR]
```

LOL I had a shutdown running as I was adding this info and it shut me down duH..
You can use 18:00 for 6:00PM or
 +1 would be one minute instead of the hh:mm time

---

### Post by nm_geo on 2010-11-27
> **seanarickymurphy said:**
> Is their a way to have shutdown-at-night shutdown at specific times?

Yes there is 

```
sudo crontab -e 
59 23 * * * /sbin/shutdown -h -P now
 
```First line calls up editor nano probably
second line is the code in the cronjob
Hit control X to close nano editor 
and say yes to save
You should shut down @ 11:59 PM everyday,

---

