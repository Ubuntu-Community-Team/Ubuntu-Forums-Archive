---
title: "how to switch off the auto shutdown command??"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by koyakishore on 2009-08-04
hi..

actually...i use the command

"sudo shutdown -h HH:MM" to shut down automatically at specified time..

now..my questions are..

1)
will that be possible to switch off this command?? or will that be possible to change the input time??


2)
can i disable my internet connection by using similar type of command??

i'm not sure whether my 2nd query is right or wrong..

help me out..

thanks in advance..:)

---

### Post by pedro3005 on 2009-08-04
Sure, if you ran sudo shutdown in a terminal, hold CTRL C. If not, there was a command, but i forgot, wait until someone else says it.

To disable your internet via command you could try
ifconfig eth0 down
That is if eth0 is the name you're using. If not, just substitute.

---

### Post by kpkeerthi on 2009-08-04
```

sudo shutdown -c

```
will cancel any scheduled shutdowns.

---

### Post by wizard10000 on 2009-08-04
> **koyakishore said:**
> hi..

actually...i use the command

"sudo shutdown -h HH:MM" to shut down automatically at specified time..

now..my questions are..

1)
will that be possible to switch off this command?? or will that be possible to change the input time??


2)
can i disable my internet connection by using similar type of command??

i'm not sure whether my 2nd query is right or wrong..

help me out..

thanks in advance..:)

If you set a time for shutdown then shutdown runs in the background and can be killed just like any other process  :)

On disabling the internet connection - the quick and dirty way is like this:

sudo ifconfig eth0 down

or if it's a wireless connection, 

sudo ifconfig wlan0 down

then you'd bring them back up with

sudo ifconfig eth0 up

or

sudo ifconfig wlan0 up

but note this will shut off your network card, not kill your internet connection.  If you've got shares mapped over a LAN you'd probably like something a little less drastic than shutting off your NIC  ;)

edit:  I liked kpkeerthi's answer on the shutdown thing much better than mine  :D

---

### Post by koyakishore on 2009-08-04
thank you for ur replies..

now..can i disable my internet connection at specified time just like auto shutdown??

---

