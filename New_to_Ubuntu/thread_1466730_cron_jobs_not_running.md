---
title: "cron jobs not running"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-04-30
I have 2 cron job on is

crontab -e
0 0 * * * avast-update
0 12 * * * avast-update

this above one works the one below not at all

sudo crontab -e
0 3 * * * apt-get update & apt-get dist-upgrade
0 15 * * * apt-get update & apt-get dist-upgrade

i have even restrated my computer after i have saved the crontab. anyone have any idea why my jobs are not running? I'm new to this.

---

### Post by kukibird1 on 2010-04-30
> **lance bermudez said:**
> I have 2 cron job on is

crontab -e
0 0 * * * avast-update
0 12 * * * avast-update

this above one works the one below not at all

sudo crontab -e
0 3 * * * apt-get update & apt-get dist-upgrade
0 15 * * * apt-get update & apt-get dist-upgrade

i have even restrated my computer after i have saved the crontab. anyone have any idea why my jobs are not running? I'm new to this.


Try &&  as well as -y 

sudo crontab -e
0 3 * * * apt-get update && apt-get dist-upgrade -y 
0 15 * * * apt-get update && apt-get dist-upgrade -y 

[http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/]("http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/")

---

### Post by lance bermudez on 2010-04-30
thank you for corecting my post but i all ready had the -y in the

0 3 * * * apt-get update && apt-get dist-upgrade -y 
0 15 * * * apt-get update && apt-get dist-upgrade -y 

i just for got to post it how ever i did not have the && i will try that thank you.

---

### Post by kukibird1 on 2010-04-30
> **lance bermudez said:**
> thank you for corecting my post but i all ready had the -y in the

0 3 * * * apt-get update && apt-get dist-upgrade -y 
0 15 * * * apt-get update && apt-get dist-upgrade -y 

i just for got to post it how ever i did not have the && i will try that thank you.

System > Administration > Software Sources > Updates  has auto update options.

---

### Post by lance bermudez on 2010-05-02
im still having trouble getting this to work. my file says that it is saved into some place called /tmp/crontab. but when i go to see if their is a file in /tmp/.crontab i see nothing and my cron jobs do not work

sudo crontab -e
0 3 * * * apt-get update && apt-get dist-upgrade -y
0 15 * * * apt-get update && apt-get dist-upgrade -y

---

### Post by lance bermudez on 2010-05-02
my cron job look like the pics

acer@kacer:~$ sudo crontab -e

PATH ="/bin:/usr/bin:/usr/local/bin"
SHELL="bin/bash"
0 16 * * * apt-get update && apt-get dist-upgrade -y # JOB_ID_1
0 12 * * * apt-get update && apt-get dist-upgrade

---

### Post by lance bermudez on 2010-05-03
still not working i have even restrated the computer after each change

acer@kacer:~$echo $PATH
acer@kacer:~$sudo crontab -e
SHELL=/bin/bash
PATH=(path from echo $PATH dont know what it is at the time)
0 16 * * * apt-get update ; apt-get dist-upgrade -y # JOB_ID_1
0 12 * * * apt-get update ; apt-get dist-upgrade

---

### Post by kukibird1 on 2010-05-05
> **lance bermudez said:**
> still not working i have even restrated the computer after each change

acer@kacer:~$echo $PATH
acer@kacer:~$sudo crontab -e
SHELL=/bin/bash
PATH=(path from echo $PATH dont know what it is at the time)
0 16 * * * apt-get update ; apt-get dist-upgrade -y # JOB_ID_1
0 12 * * * apt-get update ; apt-get dist-upgrade

Have you tried it without the SHELL & PATH entries? The pictures show /bin/bash as /bin/bach.

---

### Post by lance bermudez on 2010-05-06
yes i have don it  with out the SHELL & PATH entries. Some one told me that i needed them. what i was doing before them was
sudo crontab -e
chose the nano editor (it was it was the easiest to use)
0 3 * * * apt-get update; apt-get dist-upgrade; notify-send "updates done next at 3am" -t 0

crtl x
y
enter
restart computer

---

### Post by BenB1 on 2010-05-07
> **lance bermudez said:**
> I have 2 cron job on is

crontab -e
0 0 * * * avast-update
0 12 * * * avast-update

this above one works the one below not at all

sudo crontab -e
0 3 * * * apt-get update & apt-get dist-upgrade
0 15 * * * apt-get update & apt-get dist-upgrade

i have even restrated my computer after i have saved the crontab. anyone have any idea why my jobs are not running? I'm new to this.

New to it as well. So, I'm not sure.


You might consider spreading these out a little more. As in, you could  split apt-get update to one line then on the next apt-get dist-upgrade.  New to it as well. So, I'm not sure. But it may be what is needed.  Putting two things on one line might be confusing the computer. I don't  see why it would but computers are like people at times, fickle. Hope  This Helps.

---

### Post by legatek on 2010-05-07
In cron you have to input the full path:

```
/usr/bin/apt-get update && /usr/bin/apt-get dist-upgrade -y
```

---

### Post by bredman on 2010-05-07
In general, it is easiest to put all of your commands into a script file, and set cron to execute this script file.

The end result is the same, but you can execute the script manually from the command line to see if it works and to see the error messages. It also makes your crontab easier to read.

---

