---
title: "Restart a program from terminal - command?"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by chuangt2u on 2011-04-25
Hi, all.

Is it possible to restart a program from the terminal?

I have Dropbox running 24/7 servicing a webcam, and the Dropbox cache is eating all of my memory space even though the images are only 10 to 50kb.

pkill dropbox  works fine, but I don't want to be manually stopping/starting it every 4 hours - I'd like to run a cron job to do it hourly. 

I can figure out the cron code needed - no problems, but what is the restart command?

Does anyone have any idea?

Cheers

C

---

### Post by collisionystm on 2011-04-25
sudo service dropbox restart

---

### Post by collisionystm on 2011-04-25
sudo /etc/init.d/dropbox restart

---

### Post by chuangt2u on 2011-04-25
> **collisionystm said:**
> sudo service dropbox restart

gives

rob@ubuntu:~$ sudo service dropbox restart
[sudo] password for rob: 
dropbox: unrecognized service
rob@ubuntu:~$ 

> sudo /etc/init.d/dropbox restart

gives

rob@ubuntu:~$ sudo /etc/init.d/dropbox restart
sudo: /etc/init.d/dropbox: command not found
rob@ubuntu:~$ 

Sorry, neither work.

Also, looking for a way to do this that doesnt need me to be there to enter a password... an unattended restart.

---

