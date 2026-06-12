---
title: "File access/permission"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by new_kubunto on 2009-04-29
Hello, I have installed an application called cacti that use apache2. I have a lot of problem on file permission problem."Error like  permission denied" on an application file append frequetly. The problem is that on the error message is never specified the user that doesn' have the required permission. How can I debug this kind of problem ? there is a system log file that log the file access where is specified username and permission violation ?

---

### Post by coffeeaddict22 on 2009-04-29
kernel messages get written to /var/log/dmesg; if you type in a terminal ```
dmesg
``` you'll probably see what you want, although ```
 dmesg | grep permission
``` might give you less to wade through and still get it.  If you don't like the terminal, System/Administration/Log file viewer is another way to have a look.

---

### Post by webtechquery on 2010-02-27
This means that you have the rights permission problem.
To resolve this issue, following website may help:
[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

---

