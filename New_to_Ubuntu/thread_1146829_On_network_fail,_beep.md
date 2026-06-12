---
title: "On network fail, beep"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by bennis on 2009-05-03
Hey, i was wondering how to write a shell script that would detect if my network was up, then run a command i had. Here's how i would imagine it to work:

It would ping 192.168.0.1
If up: do nothing
if down: while true; do sleep $(($RANDOM/500)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done

And i'd stick it in the cron folder that runs it every ten minutes. Thanks for any help. Also, where is that folder?

---

### Post by freak42 on 2009-05-03
Hi, I don't do shell scripting, however ping returns codes when finished
0 : everything worked well
1 : timeout or some packets lost
2 : other error

use the -c (count) flag to make ping stop after a while.

for instance :
ping 192.168.0.1 -c 1

will ping your router (I guess) once, and either return 0 for ping successful or 1 for ping unsuccessful

man ping
has further information about this.
hth

---

### Post by freak42 on 2009-05-03
ok,.. I give up,.. I coulnd't resist:
```
#!/bin/bash
ping 192.168.0.1 -c 1 > /dev/null
if [ "$?" = "0" ]; then
	echo success
else
	echo failed
	beep
fi
```
will either print out success or failed (and beep).

---

### Post by bennis on 2009-05-03
That's awesome. Thank you both. Now my dad won't be willing to unplug my server!

Actually, another thing. Would this work as an infinite loop?
function nettest {
ping 192.168.0.1 -c 1 > /dev/null
if [ "$?" = "0" ]; then
        sleep 600
else
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
        beep -f $((RANDOM/10)) -l $(($RANDOM/100))
        sleep $(($RANDOM/60))
fi
}
while true; nettest

---

