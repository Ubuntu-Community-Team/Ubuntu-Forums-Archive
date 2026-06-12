---
title: "Suexec problem"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by rajchd on 2010-07-09
Hi
 
I am new to ubuntu. I have downloaded version 10.04 server and installed on one computer. After a few retries it was installed succesfuly and was showing the default apache screen on network computers. Even phpmyadmin was working fine. 
 
Then I installed ispconfig on this machine and restarted the computer. On the restart of computer it refused to start apache and show error "**invalid command suexecusergroup**". I searched the net to find a solution and applied solutions found at one of the help sites. That resolved the issue to an extent and apache starts now with a few warning messages "**suexecusergroup directive requires SUEXEC wrapper**". Apache server now serves html pages I think but does not parse php files correctly.
 
Again I searched help sites and they suggested to run chmod 4755, chmod 4711, chmod 4111 etc. commands on the /usr/sbin/suexec or usr/lib/apache2/suexec or /opt/httpd/bin/suexec etc. But I can not find suexec at these locations. 
 
Can someone help me to find suexec and resolve this issue please?
 
Thanks
 
Raj

---

### Post by rajchd on 2010-07-09
This problem is resolved by "su apt-get install apache2-suexec-custom"
 
But a problem still remaining.  My phpmyadmin site is not running, instead browser is attempting to download the php files.

---

