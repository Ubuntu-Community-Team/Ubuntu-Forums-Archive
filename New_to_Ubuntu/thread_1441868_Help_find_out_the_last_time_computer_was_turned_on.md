---
title: "Help find out the last time computer was turned on!"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Ubunser on 2010-03-29
Actually I want to find out if somebody loaded the system when I was away from home.

---

### Post by steev182 on 2010-03-29
You can see how long it's been up by going to the terminal and typing 'uptime' and pressing enter. That will say 'up 6 days' or whatever, otherwise, you could look in /var/log/ I just tried 'cat /var/log/kern.log.1 | grep 'KERNEL supported' ' as that comes up whenever the system boots and it showed me:
```
Mar 23 06:46:07 bronx kernel: [    0.000000] KERNEL supported cpus:
```

There's probably a more elegant way of doing it though, plus I have a few more kern.logs gzipped up so would probably want to look through those too if it wasn't a recent startup.

---

### Post by undecim on 2010-03-29
> **steev182 said:**
> You can see how long it's been up by going to the terminal and typing 'uptime' and pressing enter. That will say 'up 6 days' or whatever, otherwise, you could look in /var/log/ I just tried 'cat /var/log/kern.log.1 | grep 'KERNEL supported' ' as that comes up whenever the system boots and it showed me:
```
Mar 23 06:46:07 bronx kernel: [    0.000000] KERNEL supported cpus:
```

There's probably a more elegant way of doing it though, plus I have a few more kern.logs gzipped up so would probably want to look through those too if it wasn't a recent startup.

Exactly my thoughts as I read the title.

If you want to view the gzipped log files (for going back over a week or so)
```
zcat /var/log/kern.log.2.gz | grep 'KERNEL supported'
```

Of course, remember that anyone who has physical access to the computer could change these logs if they are know Linux and really didn't want you to know about them being on.

---

### Post by Ubunser on 2010-03-29
Thank you guys! Worked)));)

---

### Post by Nisal on 2010-03-29
this is peice of nice information :D if any one had change the log is there any other way to get details ?

---

### Post by undecim on 2010-03-29
> **Nisal said:**
> this is peice of nice information :D if any one had change the log is there any other way to get details ?

You could look for other tell-tale signs. Logs of package lists being updated, access times of files, etc...

This is the kind of thing that computer forensics experts do.

---

### Post by dwarfolo on 2010-03-29
> **Nisal said:**
> this is peice of nice information :D if any one had change the log is there any other way to get details ?

lastlog -t 1
will tell you who logged in during the last 24 h.

To be able to change the kernel log you must gain root privileges or ...well ... know the password of at least one of the sudoers users, and log in as such user.

---

### Post by undecim on 2010-03-29
> **dwarfolo said:**
> To be able to change the kernel log you must gain root privileges or ...well ... know the password of at least one of the sudoers users, and log in as such user.

Or have physical access. Physical access > root access

---

### Post by dwarfolo on 2010-03-29
Sure ... at least in 99.9% of the cases.
The great one truth in IT security, is that the only secure computer is the one not yet assembled hehehe
:p

---

### Post by AfrikaDietmar on 2011-02-18
hi guys,

i run a small network of around 5 machines and i need to track when each machine was switched on and off on a monthly basis, for each day. Is there a way i could get each machine to generate a text file where these details are recorded in a list accummulating for each day ? 

Eventually also have text file protected or stored somewhere hidden.

Let me know if you have an idea how this could be done... :)

bye bye,
Dietmar

---

