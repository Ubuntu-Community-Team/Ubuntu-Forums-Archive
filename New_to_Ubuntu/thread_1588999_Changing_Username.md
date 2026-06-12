---
title: "Changing Username"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by mmk213 on 2010-10-05
I am a student in a school where we are installing Ubuntu on old computers. We named the original profile StudentAdmin. We misspelled it, StudnetAdmin. We were able to change this to StudentAdmin, but the username is still studnetadmin. Is there a way to fix that?

---

### Post by ubudog on 2010-10-05
This should help you.


[http://ubuntuforums.org/showthread.php?t=821685](http://ubuntuforums.org/showthread.php?t=821685)

---

### Post by mmk213 on 2010-10-06
I read the link that you shared. It worked for me. Here's what I did to change the username. 
 
I changed the username by holding shift at boot to get to the recovery mode. Once I was there I went to the second ubuntu option then pressed enter. I dropped to the root terminal. I then put in the command 
 
usermod -l new -m -d /home/new old
 
That changed the username, but not the computer name. To change the computer name I opened a terminal put the command 
 
gksudo gedit /etc/hostname.
 
Put the password in when prompted. The host name file will open. Replace your old computer name with your new computer name. Save and close all windows and restart.
 
Thank you for helping me and I hope this helps you.

---

### Post by PapaNerd on 2010-10-06
Perhaps the simplest (albeit a bit risky) way would be to back up the passwd and shadow files ```

cd /etc
sudo cp -p passwd passwd.old
sudo cp -p shadow shadow.old

```
then edit /etc/passwd and /etc/shadow changing "studnetadmin" to "studentadmin", and finally fixing the naming in the directory structure: ```

cd /home
sudo chown -R studentadmin studentadmin

```

---

### Post by ubudog on 2010-10-06
Cool.

---

