---
title: "Auto start up applications."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-15
Is there a way to automatically start up applications in Ubuntu 8.04? I'd like to make sure my calendar program (Sunbird) starts when ever I boot. Thanks for any assistance.

---

### Post by dross_kuh on 2009-04-15
Take a look in menu  > system > preferences > sessions

---

### Post by jwaclawsky on 2009-04-15
Ok I went to menu > system > preferences > sessions and added my Sunbird calendar to the start up programs, but when I boot still it doesn't start up. I don't see any errors anywhere but then again I am not sure where to look. Any advice would be appreciated. Thanks!

---

### Post by dross_kuh on 2009-04-16
I can only think you have the "command" typed in wrong or an option missing off it? try this...

right-mouse-button on Applications-menu >  Edit-Menus , find your program Sunbird...  right-mouse-button on it and Properties...

copy the "command" exactly into the command in your session`s....

hope that help`s :/

---

### Post by jwaclawsky on 2009-04-16
Thanks. That did it. Spelling problem. BTW, Is there an error log or something I can check in the future to see if the system is finding an error or not finding something because of spelling etc?  Thanks

---

### Post by dross_kuh on 2009-04-16
still learning myself here :/  but...
theres a whole bunch of logs in /var/log   :)

happy hunting in there m8y ;)

---

