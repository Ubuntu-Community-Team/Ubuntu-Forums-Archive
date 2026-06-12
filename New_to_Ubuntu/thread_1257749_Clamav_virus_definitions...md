---
title: "Clamav virus definitions.."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-04
How to disable CLAMAV automatic virus definition updates?I prefer it to  do manually..

---

### Post by MrWES on 2009-09-04
> **getyourkarthick said:**
> How to disable CLAMAV automatic virus definition updates?I prefer it to  do manually..

```
sudo freshclam
```

from the terminal. If you installed clamav, I'm sure the freshclam daemon (service) is running.

```
bill@bill-laptop:~$ ps aux | grep freshclam
clamav    2710  0.0  0.0   3244  1452 ?        Ss   Aug29   0:02 /usr/bin/freshclam -d --quiet

```
By default, freshclam checks virus defs once an hour. To disable, edit ```
sudo nano /etc/clamav/freshclam.conf
``` and change the checks from 24 to 0. Then ```
sudo /etc/init.d/freshclam restart
```

You could either remove or make not executable the /etc/init.d/clamav-freshclam script

---

### Post by karthick87 on 2009-09-04
I have edited the file and while restarting it failed to start..

karthick@karthick-desktop:~$ sudo /etc/init.d/clamav-freshclam restart
 * Starting ClamAV virus database updater freshclam                      [fail]

---

### Post by MrWES on 2009-09-04
> **getyourkarthick said:**
> I have edited the file and while restarting it failed to start..

karthick@karthick-desktop:~$ sudo /etc/init.d/clamav-freshclam restart
 * Starting ClamAV virus database updater freshclam                      [fail]


And that's what you wanted correct?

Now from the terminal type:
```
sudo freshclam
``` and that should run a manual update without running the freshclam daemon.

Bill

---

### Post by karthick87 on 2009-09-05
Ya thankyou! Is there anyway to find last updated date?

---

### Post by MrWES on 2009-09-05
> **getyourkarthick said:**
> Ya thankyou! Is there anyway to find last updated date?

```
/var/log/clamav/freshclam.log
```

---

