---
title: "crontab"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-20
when crontab runs a script, can the script output to the terminal for user interaction.

ie 
```

perform backup?
y
back up complete

```

only doesn't seem to working for me, so I guess I'm trying something that just can't be done?

---

### Post by M!K3_$ on 2010-10-20
I'm not sure if you can do this. 

But why would you want to do this? 
Say you in the middle of working on something and this pops up.
Or if you have left the machine and it wants to backup but it wont because you haven't answered yet. And then days go by (because your on holidays) and you have your cron script stacking.

You very well could have thought of all of this already, just throwing in my $0.02.

---

### Post by robsoles on 2010-10-20
crontab jobs run in their own process, or at least a process that isn't invoked by an easily accessed terminal. Messaging by broadcast is possible but interrupting whatever session(s) of terminal are running to gain input as to whether or not to proceed is a lot of work for very little gain.

+1 the basic idea(s) M!K3_$ expressed about this as well.

---

### Post by Hippytaff on 2010-10-20
cool...I now know...trying to use something it was not designed for for purposes that are pointless...nay intrusive :-)

Thanks both :-D

---

### Post by trikster_x on 2010-10-21
If you really want to have an indicator that is not intrusive there is a way to create a log file that would capture anything that would show up on a terminal screen.  Tell it to send the log to your desktop and cron silently gives you a way to know if your command has run.  If you include the "date" command at the end of your script or command, it will print the time and date at the end of the file so you know exactly when it finished.   

```
* * * * * "your command here" > /path/to/desktop.log
```

or

```
* * * * * "your command here" > /path/to/desktop.log 2&1
```

The second will include any errors that may not be seen on the stdout.

---

