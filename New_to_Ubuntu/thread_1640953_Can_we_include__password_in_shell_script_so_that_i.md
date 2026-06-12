---
title: "Can we include  password in shell script so that it does not ask fro password?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-12-08
Can we include password in a shell script?

My script contains
su  -c "notify-send test" USERNAME

It asks for password. Can we include the password in the script so that it does not ask fro password?

---

### Post by Brandon Williams on 2010-12-08
That is generally not a good idea. If you want a specific user to be able to run a specific command as some other user without entering a password, you can configure sudo to allow this. For example, the following in /etc/sudoers:```
bob ALL = (fred) NOPASSWD: /usr/bin/notify-send
```will allow user bob to run /usr/bin/notify-send as user fred without entering a password. Then, in the script to be run by bob, the command would be:```
sudo -u fred /usr/bin/notify-send test
```

---

### Post by sisco311 on 2010-12-08
+1

and you should run GUI apps as another user in a login shell: **su - [-c "command"] user** or **sudo -u user -i [command]**.

---

### Post by Guruprasad on 2010-12-25
Thank you Brandon Williams

With your suggestion I was able to get my script running without password.

---

