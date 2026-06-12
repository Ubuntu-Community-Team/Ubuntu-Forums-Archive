---
title: "investigating first crash"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-10
My Ubuntu Intrepid took it's first crash. On restart I'm investigating what may have happened. The last entry in the syslog is at least 3 mins before when I think the crash occured (and those last syslog events don't spell alarm to me). Any pointers to where I should look and what to look out for?!
thanks

---

### Post by Crafty Kisses on 2009-03-10
Hey there! You might want to check your kernel logs, that could very well point you in the right direction. You can locate the kernel logs by running the following in Terminal:
```
sudo nano /var/log/kern.log
```

---

### Post by dimitriv on 2009-03-10
thanks codename

I ran that, the last entry/event is over 20 minutes before I think the failure occured. I base the failure time on the last modified time on an what was an open data file.

The hunt continues...

Cheers

---

