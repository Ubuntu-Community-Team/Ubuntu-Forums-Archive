---
title: "GDM Login Settings from Terminal?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by scrollmage on 2010-08-18
Hi!

I have a rather odd problem. I have a machine I can access via SSH but (for reasons too long to list) I need to change my gnome settings to automatically log into a specific user. Is there a way I can change this from the terminal? I have sudo rights and I am logged in as the user I want to log into automatically.

Sorry I am new to gnome and ubuntu :(

-SM

Edit: I am running 10.04 with all the updates.

---

### Post by silverglade00 on 2010-08-18
You can edit (or create if it's not there) the file /etc/gdm/custom.conf to setup auto login

```


[daemon]
AutomaticLoginEnable=true // enables autologin
AutomaticLogin=scrollmage // the username to autologin
TimedLoginEnable=true     // enables a timer so you can login someone else
TimedLogin=scrollmage     // the user to login after a certain time has passed
TimedLoginDelay=10        // a certain time that needs to pass (in seconds)


```

---

### Post by scrollmage on 2010-08-18
You're the man! Thanks!

---

