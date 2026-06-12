---
title: "Crontab doesn't work"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by ehalls on 2010-01-04
Hi, I cant get crontab to work. Do you have to enable it in ubuntu 9.10? According to the attachment, shouldn't firefox be started once in a minute? 

Best regards

Erik

---

### Post by bodhi.zazen on 2010-01-04
This is one of the most common mistakes with crontab.

crontab uses a minimal shell with a minimal path.

use the full path, /bin/firefox rather then firefox

Also, you can not run multiple versions of firefox in that way. If firefox is already running you will get an error message to that effect.

---

### Post by Greenwidth on 2010-01-04
You haven't entered a time for it to run.
For every minute it would be:
*/1 * * * *
see:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by ehalls on 2010-01-04
> **bodhi.zazen said:**
> This is one of the most common mistakes with crontab.

crontab uses a minimal shell with a minimal path.

use the full path, /bin/firefox rather then firefox

Also, you can not run multiple versions of firefox in that way. If firefox is already running you will get an error message to that effect.

Ok, but the thing is that I'm not even getting an error message. I wrote firefox for testing, but the reason I want to use crontab is that I want to suspend the computer at a particular time. Pressing alt-F2 and running the command ```
pmi action suspend
``` works, however using the command in crontab does nothing. 

But the command ```
* * * * *echo "hello there" >> /home/erik/hej.log 
``` writes to the log file once in a minute... strange :S

---

### Post by ehalls on 2010-01-04
> **Greenwidth said:**
> You haven't entered a time for it to run.
For every minute it would be:
*/1 * * * *
see:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Hi Greenwidth, 
I guess both ```
*/1 * * * * echo "hello there" >> /home/erik/hej.log
``` and```
 * * * * * echo "hello there" >> /home/erik/hej.log
``` writes to the log file for me once a minute...

---

### Post by bodhi.zazen on 2010-01-04
> **ehalls said:**
> Ok, but the thing is that I'm not even getting an error message. I wrote firefox for testing, but the reason I want to use crontab is that I want to suspend the computer at a particular time. Pressing alt-F2 and running the command ```
pmi action suspend
``` works, however using the command in crontab does nothing. 

But the command ```
* * * * *echo "hello there" >> /home/erik/hej.log 
``` writes to the log file once in a minute... strange :S

I believe echo is a builtin

At any rate, use the full path , lol

/usr/sbin/pmi action suspend

---

### Post by ehalls on 2010-01-04
I have come up with the solution, sorry to bother you. In case anyone is reading, you have to write the path variable in the top of the file after writing```
 crontab -e
``````
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```

---

### Post by ehalls on 2010-01-04
> **bodhi.zazen said:**
> I believe echo is a builtin

At any rate, use the full path , lol

/usr/sbin/pmi action suspend

thanks bodhi.zazen, your fast :)

---

### Post by bodhi.zazen on 2010-01-04
> **ehalls said:**
> thanks bodhi.zazen, your fast :)

=)

Glad you got it working

---

