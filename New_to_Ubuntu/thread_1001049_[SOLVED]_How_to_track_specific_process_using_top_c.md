---
title: "[SOLVED] How to track specific process using top command?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by kajman on 2008-12-03
If I'm interested in some particular process information that may be given by the top command, but it doesn't fall to any of the column categories, how can I track it?

For e.g. I'd like to see some details on a newly installed app - gmail-notify. I know only the process name, but it does not take any reasonable amounts of CPU or Mem to have it listed. It's casual in every way :) 
What's the solution?

Thanks for any replies.

---

### Post by Titan8990 on 2008-12-03
Top is meant to show the processes that are using the most resources.


But to view one specifically:


ps aux | grep PROCESSIAMLOOKINGFOR

Then take the PID and run top like so:


top -pXXXX

where XXXX = the PID of the process you would like to monitor

---

### Post by adult swim on 2008-12-03
you could use top, first find the pid of gmail-notify
```
ps -C gmail-notify
``` and then view it with top ```
top -p xxxxx
``` where xxxx is the pid returned from the first step

---

### Post by kajman on 2008-12-03
Works very nice, thank you ;)

---

### Post by hyper_ch on 2008-12-03
or rather install and use "htop"... you can easily search there plus it looks a lot prettier ;)

---

### Post by kajman on 2008-12-03
Thanks! It looks really nice. But I noticed something unusual:
top shows that I have 125 tasks total, and htop at the same time says that there are 246 of them... Why is that? Where does the difference (and a big one also) come from?

---

### Post by kajman on 2008-12-03
Thanks! It looks really nice. But I noticed something unusual:
top shows that I have 125 tasks total, and htop at the same time says that there are 246 of them... Why is that? Where does the difference (and a big one also) come from?

---

### Post by hyper_ch on 2008-12-03
no clue, never noticed this until now myself :(

read the man pages... I'm sure it will be in there somewhere.

---

