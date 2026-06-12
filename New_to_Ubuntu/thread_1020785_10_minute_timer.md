---
title: "10 minute timer"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Doormat on 2008-12-24
I am looking for a timer I can set to alert me every 10 minutes. I haven't been successful in finding one yet. Does anyone know of a reliable one that has an alert? Thanks. Using hardy 8.04

---

### Post by retskrad on 2008-12-24
You could try google or sourceforge.

---

### Post by ken22 on 2008-12-24
I would recommend the linux commands "at" and the "cron" system to schedule events.

---

### Post by Doormat on 2008-12-24
> **ken22 said:**
> I would recommend the linux commands "at" and the "cron" system to schedule events.
I want to get an alert every 10 minutes and as I understand it these two are used to run something at a specific time.

---

### Post by ken22 on 2008-12-24
Ok, some code is needed.

Try shell script like

```
while :;do
	# Put your code here. 
	sleep 600
done
```

Save it as remind.sh . Make it executable with ```
chmod +x remind.sh
``` and run it by ```
./remind.sh &
```

---

### Post by scorp123 on 2008-12-24
> **Doormat said:**
> I want to get an alert every 10 minutes and as I understand it these two are used to run something at a specific time. "cron" can also be used to execute programs in specific intervals. Please read here:

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

Further down the page are a few examples that you could maybe use and modify to meet your own needs?

---

### Post by jackmetal on 2008-12-24
There are also a few applets and applications available to do it.  One for example, is: alarm-clock (found in the repositories).  It can set counters and alarms, and can be scheduled and repeated, etc..

---

### Post by Gulyan on 2008-12-24
> **jackmetal said:**
> There are also a few applets and applications available to do it.  One for example, is: alarm-clock (found in the repositories).  It can set counters and alarms, and can be scheduled and repeated, etc..

I also use 'Alarm Clock' and I am very happy with it. I recommend it to all of you. :popcorn:

---

### Post by st33med on 2008-12-24
```
sudo apt-get install timer-applet
```

Then right click the panel and click "Add to Panel ..." and search for Timer.  You should be able to set it up from there.

---

### Post by kansasnoob on 2008-12-24
> **st33med said:**
> ```
sudo apt-get install timer-applet
```

Then right click the panel and click "Add to Panel ..." and search for Timer.  You should be able to set it up from there.

+1.

I use it different, but it should work.

---

### Post by s3a on 2008-12-24
What about sanduhr?

---

