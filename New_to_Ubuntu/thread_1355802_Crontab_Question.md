---
title: "Crontab Question"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Thelasko on 2009-12-15
I have a cron job running every hour.  However, sometimes the cron job doesn't finish within the hour.  When I go to check the logs, I get an output that says "X program is already running, only one instance can run at a time."  This is an issue because I don't know if the program has hung or not.

Can I make it so the cron job doesn't run if another one hasn't finished?

---

### Post by mvalviar on 2009-12-15
I'm no expert but the this works for me
```
ps aux |grep 'X Program'|grep -vq grep || 'X Program'
```
If X Program is still running this command does nothing.

---

### Post by fatality_uk on 2009-12-15
Mind if I ask what the program is? It could be that a script could be wrapped around to lauch and close it tidily

---

### Post by Thelasko on 2009-12-15
> **fatality_uk said:**
> Mind if I ask what the program is? It could be that a script could be wrapped around to lauch and close it tidily

Mirobridge.  I like the way you think.

How would I make it so only one instance of a script can run at a time?

---

### Post by benjaminsuman on 2009-12-15
I would wrap your job in a script that creates a pid file at the beginning of execution and deletes the file when the job is finished.  By checking for the file at the beginning of your script, you can discover whether the previous job is still running and bi-pass execution of the rest of your job.

---

### Post by Thelasko on 2009-12-15
> **benjaminsuman said:**
> I would wrap your job in a script that creates a pid file at the beginning of execution and deletes the file when the job is finished.  By checking for the file at the beginning of your script, you can discover whether the previous job is still running and bi-pass execution of the rest of your job.

[Like this?]("http://kirk.webfinish.com/2009/10/bash-shell-script-to-manage-pid-file-creationdeletion/")

---

### Post by benjaminsuman on 2009-12-15
Yes, that example would handle all of the different ways your job could exit.   Here is a simple example that handles just the first bullet point from the article you linked.
> Problem: You want your script to execute without overlapping another execution.
Solution: Make a flag file so you know that your script is already executing.```

#!/bin/bash
process_name="processX"
if [ ! -f /tmp/${process_name}.pid ]; then

#execute job here
  job_cmd & process_id=$!
  echo process_id > /tmp/${process_name}.pid  
  wait $process_id
  rm /tmp/${process_name}.pid
else
  echo "previous job still running"
fi

``` job_cmd would be the command you are currently trying to run with your cron job

---

### Post by Thelasko on 2009-12-15
my command is quite long to run this program.```
env `dbus-launch` sh -c 'trap "kill $DBUS_SESSION_BUS_PID" EXIT; /usr/share/mythtv/mythvideo/scripts/mirobridge.py -V'  > "/tmp/mirobridge.log" 2>&1
```
Will that effect the outcome of this script?  Is any of this redundant?

I put it all on one line.

---

### Post by benjaminsuman on 2009-12-15
you would have to break that command up into at least a couple of lines, but the easier solution would be to put your command in a separate script and execute it from your process management script.

---

### Post by Thelasko on 2009-12-15
It works fine on all one line.

Thanks!

---

