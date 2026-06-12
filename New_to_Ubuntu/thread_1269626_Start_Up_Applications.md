---
title: "Start Up Applications"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-09-18
For some reason when Xubuntu starts up, the system monitor and install package manager automatically start up too. I looked in the boot menu and they weren't there. So, can anyone help me? Thank you.

---

### Post by sisco311 on 2009-09-18
Delete the content of the ~/.cache directory. 

.cache is a hidden directory in your home directory. you may have to press Ctrl+H to list the hidden directories.

Next time you log out/reboot/shut down make sure that the *Save session for future logins* check box is unchecked.

[http://www.upload3r.com/serve/180909/1253297679.png[/img]"][img]http://www.upload3r.com/serve/180909/1253297679.png[/img]]("[img)

---

