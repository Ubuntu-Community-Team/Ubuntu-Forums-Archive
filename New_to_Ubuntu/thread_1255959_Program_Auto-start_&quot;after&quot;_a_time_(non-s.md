---
title: "Program Auto-start &quot;after&quot; a time (non-specific)"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-09-02
Hi,
Is it possible via Crontabs {or other ) to have a program open automatically when the PC is powered up anytime within a specific period? (not a specific time)  
I have a PC which runs one slideshow in the morning and a different one in the afternoon.
This OK as long as there is no power interruption, in which case it reverts to the normal startup program( the first show)
Is it possible to write a script to cover this?

kenmac2

---

### Post by kotnik on 2009-09-02
Here's how I'd do it (I made up times).

Startup shell script at the boot:
- determines what time it is
- starts appropriate slideshow

Cron job at 9AM:
- kills whatever slideshow is up and running, and starts daylight show

Cron job at 9PM:
- kills whatever slideshow is up and running, and starts nighttime show

You just need a bit of shell foo, and you're on.

---

### Post by kenmac2 on 2009-09-02
kotnik,
The Cron jobs part is covered.
Could you expand on the shell script idea?
Is it possible to write some script in the startup area that can determine which time period it is in, and act on this info?

kenmac2

---

### Post by aeiah on 2009-09-02
im crap with bash but given some time (ho ho ho) you should be able to construct something. you just want a if else statement really. you can get the time using the date command:

```
date +"%H:%M"
```

you just need a bash script that reads:

```


if 'date +"%H:%M"' > 21:00:
    run night presentation
else:
    run day presentation


```


obviously my syntax is wrong because as i said, im crap at bash. something i need to learn really since python can be heavy handed for things like this.

---

### Post by kotnik on 2009-09-03
Sure, here's a skeleton for you:

```
#!/bin/bash

if [ `date +"%H"` -ge 21 ]; then 
        echo "It's past 21h.  Start night show";
else
        echo "It's before 21h. Day show, please";
fi
```

---

### Post by kenmac2 on 2009-09-04
Thanks for your help.

kenmac2

---

