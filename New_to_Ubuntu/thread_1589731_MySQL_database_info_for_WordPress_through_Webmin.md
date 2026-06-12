---
title: "MySQL database info for WordPress through Webmin"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by christopherjoel on 2010-10-06
I've mostly setup my first Ubuntu 9.10 server to use as a web host on Rackspace Cloudserver and I've run into a brick wall.  I've got the MySQL database created and the files for WordPress uploaded, but I can't find the database info to put into the config file for WordPress.  I'm moving from a Shared Godaddy server, so I'm used to the database info being easily found.  I created the database through Webmin, but there doesn't appear to be any info about the database itself in Webmin.  Can someone please tell me where to find this info?  If that wasn't clear enough, I'm looking for what to put into the Database Host field in the WordPress config file.

---

### Post by robsoles on 2010-10-06
In case it hasn't been said: Welcome to UF.

If the wordpress installation is on the same server as the mysql database installation then you want to put **localhost** or **127.0.0.1** into the field asking for the database host name.

---

### Post by christopherjoel on 2010-10-06
Thanks Rob!  Yeah, I had tried that earlier today and it didn't work (don't know why), but I've done so much on the server today, it's hard to tell when I resolved the issue.  I tried localhost right after I posted this and it worked.  Thanks for the help!

---

### Post by robsoles on 2010-10-07
Earlier the firewall might not have had the port opened for localhost (3306 if memory serves) and perhaps a restart in-between or some other happy accident opened the firewall - glad it's not a problem to you anymore in any case!

Please consider marking your thread as solved using the thread tools in red above :)

---

