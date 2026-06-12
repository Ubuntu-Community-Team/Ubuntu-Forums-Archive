---
title: "updates"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-08-24
my IP provider requires me to do my updates after 1am how download manager to download at a cretin time

---

### Post by DougieFresh4U on 2010-08-24
Why mess with the 'update manager' 
I am more comfortable using terminal to update

```
sudo apt-get update
sudo apt-get dist-upgrade
```

though I use 'aptitude' instead of 'apt-get'

---

### Post by Chad Olson on 2010-08-25
> **DougieFresh4U said:**
> Why mess with the 'update manager' 
I am more comfortable using terminal to update

```
sudo apt-get update
sudo apt-get dist-upgrade
```though I use 'aptitude' instead of 'apt-get'



how do i delay the download until the right time

---

### Post by ubudog on 2010-08-25
You would have to leave your computer on, but you can use cron.

[http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)

---

### Post by Chad Olson on 2010-08-25
> **ubudog said:**
> You would have to leave your computer on, but you can use cron.

[http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)

is cron the same thing as gnome scheduler

---

### Post by Calash on 2010-08-25
By default Update Manager will not install anything for you.  You have to tell it to go ahead and run.  So the simple solution is to stay up late once a month and run your updates.

For a more automated solution you can use the idea posted or see this thread for some other solutions.

[http://ubuntuforums.org/showthread.php?t=1449498](http://ubuntuforums.org/showthread.php?t=1449498)

---

### Post by ubudog on 2010-08-25
> **Chad Olson said:**
> is cron the same thing as gnome scheduler

No.

---

### Post by -kg- on 2010-08-26
> **ubudog said:**
> >  Originally Posted by Chad Olson  View Post
is cron the same thing as gnome scheduler

No.

Actually, yes.  I just found the following page (dated Aug 2, 2010):

[http://techthrob.com/2010/08/02/how-to-schedule-tasks-with-gnome-scheduler/]("http://techthrob.com/2010/08/02/how-to-schedule-tasks-with-gnome-scheduler/")

> If you’ve used Linux for a while you’ve probably learned about cron, which is the system service responsible for executing scheduled tasks. Cron  runs in the background, and helps keep your computer running. At scheduled times, it launches programs to rotate log files, [COLOR="Red"]check for software updates[/COLOR], and perform other housekeeping jobs. You can also use cron to your own advantage and to schedule your own tasks; for example, a routine backup of your home directory, or to check if you have new mail. The easiest way to schedule tasks in Ubuntu or Fedora is to use the gnome-schedule application. This tutorial will show you how to schedule tasks using the Gnome Scheduler, [COLOR="Red"]a graphical front-end for cron.[/COLOR]

---

### Post by ubudog on 2010-08-26
Oh, sorry about that.  I have to do more research... :)

---

### Post by tarps87 on 2010-08-26
note:
```
sudo apt-get update && sudo apt-get upgrade -y
```
or if you are running it as root
```
apt-get update && apt-get upgrade -y
```
Will remove the need for user input

---

### Post by Chad Olson on 2010-08-31
> **tarps87 said:**
> note:
```
sudo apt-get update && sudo apt-get upgrade -y
```or if you are running it as root
```
apt-get update && apt-get upgrade -y
```Will remove the need for user input

i've used sudo apt-get update  but nothing happens is their a problem with a password do I have to work it in another directory to avoid having to put in a password.

---

### Post by tarps87 on 2010-09-01
> **Chad Olson said:**
> i've used sudo apt-get update  but nothing happens is their a problem with a password do I have to work it in another directory to avoid having to put in a password.

How are you trying to use it?

---

