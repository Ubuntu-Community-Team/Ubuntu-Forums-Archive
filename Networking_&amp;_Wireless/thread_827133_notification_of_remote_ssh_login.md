---
title: "notification of remote ssh login"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by angryswede on 2008-06-12
Is there some sort of applet or notification that can be used in gnome which will notify the user if a user has logged in remotely using ssh?  I know you can run who or finger from the shell or you can use network tools, but I was looking for something event-driven that will just display a notification on your gnome desktop.

---

### Post by dmizer on 2008-06-13
here's a tutorial i found which sends an email.  it could be modified to take other actions as well: [http://www.crucialp.com/resources/tutorials/secure-server-securing/email-alert-root-ssh-login-e-mail.php](http://www.crucialp.com/resources/tutorials/secure-server-securing/email-alert-root-ssh-login-e-mail.php)

i'm sure there's other options for you, i only did a quick search via google.

---

### Post by chadlongstaff on 2012-05-15
chaddy@mactux:~$ cat watcher.sh 
#!/bin/bash
tail -fn0 /var/log/auth.log | \
while read line ; do
        echo "$line" | grep "Accepted"
        if [ $? = 0 ]
        then
                espeak "you have a caller"
        fi
done

---

### Post by chadlongstaff on 2012-05-16
^ you'll probably want to add that to startup applications, only works if you have an admin account, but shouldn't require sudo. I prefer a spoken notification, feel free to mod it to call the notifier... no ideas how as yet.

---

