---
title: "/var/log eats up memory"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by 21:27 on 2008-12-26
I had about 20Gb free memory on my ubuntu partition, and then suddenly I notice I have only 1Gb left. I check with disk usage analyzer and it show, that /var/log has 19Gb. What is the reason for this? syslog.O is 5Gb, messages.O has 5Gb, kern.log.O has 5Gb. Don't know what may have caused this.

---

### Post by scragar on 2008-12-26
It's .0, not .O, and they can safely be deleted, they are old logs from your last boot(There is some sort of error that results in this btw, I've heard about it before).



[http://ubuntuforums.org/showpost.php?p=6200061&postcount=8](http://ubuntuforums.org/showpost.php?p=6200061&postcount=8)

---

