---
title: "Cron not running"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by televisi on 2009-05-02
Hi All,
I'm running Ubuntu server edition. Need your help in running cron

This is what I've done to test whether my cron works/not:
- Login with normal user (which also part of sudoers, but **not under root group**)

- Create directory **/testing with chmod 777** (I don't think it really matter who the owner of the directory is, right?)

- inside /testing folder, I put **script.sh**
```
date >> /testing/result
```

- I **touch /testing/result, and chmod 777** too
- I run **crontab -e**, which opens up cron editor (in vi/nano) from filename => /tmp/crontab.rTcrDa/crontab
```
#run the script every minute...
1 * * * * /testing/script.sh
```

- restart cron service, **sudo /etc/init.d/cron restart**
- wait for 1 minute, nothing coming up in /testing/result

_**Analysis:**_
- I ps aux|grep "cron", the service is running
```
root      4409  0.0  0.6   2100   764 ?        Ss   May02   0:00 /usr/sbin/cron
testuser        4714  0.0  0.4   1784   540 pts/0    R+   07:35   0:00 grep cron
```

- I login as root (**sudo -i**) and **ls /var/spool/cron/crontabs folder** and see that my login name already listed there
```
total 16
drwx-wx--T 2 root   crontab 4096 May  1 16:14 .
drwxr-xr-x 5 daemon daemon  4096 Jan  2  2000 ..
-rw------- 1 **[COLOR="Red"]testuser[/COLOR]**     crontab  266 May  1 16:14 **[COLOR="Red"]testuser[/COLOR]**
-rw------- 1 root   crontab  314 Apr 28 07:04 root
```

_**Different method:**_
- I login as root (**sudo -i**) and edit **/etc/crontab**
```
#run the script every minute...
1 * * * * testuser /testing/script.sh
```

- Apparently when I add above code in /etc/crontab, cron service is running, but strangely it only runs every hour, this is my **/testing/result** file looks like:
```
Sun May  3 01:01:02 EST 2009
Sun May  3 02:01:01 EST 2009
Sun May  3 03:01:01 EST 2009
Sun May  3 04:01:01 EST 2009
Sun May  3 05:01:01 EST 2009
Sun May  3 06:01:01 EST 2009
Sun May  3 07:01:01 EST 2009
```

Seems the system runs it every hour, and only run the job if I put in the root crontab, did I miss something here?

Thanks heaps!

**_Side questions:_**
- Should I do restart cron service all the time, after I/user make some changes to crontab?
- As **user level crontab** created in /tmp/ folder, should we backup this file too if we want to backup user files?, can we put restriction in the system, to not create user level crontab in /tmp/ folder?

---

### Post by Alterax on 2009-05-02
1 in that position means "minute is 1"
change it to */1 for "every 1 minute"

Yeah, you must restart crontab if you want it to reflect your changes.

---

### Post by blackgr on 2009-05-02
1 * * * * is wrong. Try * * * * *

---

### Post by televisi on 2009-05-02
WOW... what a prompt reply!!!
> **Alterax said:**
> 1 in that position means "minute is 1"
change it to */1 for "every 1 minute"

Yeah, you must restart crontab if you want it to reflect your changes.

> **blackgr said:**
> 1 * * * * is wrong. Try * * * * *
Both are correct, but now, why:
- only works from root crontab (**/etc/crontab**)?

**_Side questions:_** :P
- As user level crontab created in /tmp/ folder, should we backup this file too if we want to backup user files?, can we put restriction in the system, to not create user level crontab in /tmp/ folder?

---

### Post by televisi on 2009-05-13
Anyone able to answer my side question?
Thanks

---

