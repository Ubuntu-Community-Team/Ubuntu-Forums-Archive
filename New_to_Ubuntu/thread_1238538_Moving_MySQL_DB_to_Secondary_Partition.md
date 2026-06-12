---
title: "Moving MySQL DB to Secondary Partition"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by pcamis on 2009-08-12
I've successfully installed the latest versions of Ubuntu Server and Drupal on a server with two RAID 1 arrays.  Everything is installed & configured on the primary array.  Before I go to work on the Drupal configuration, I want to move the MySQL database over to the secondary array.  I tried doing so by following these instructions:

[http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive](http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive)

I hit the end where I attempt to restart MySQL, but all I get is a response "fail".  No error code or other notification.  I can modify the "my.cnf" file to restart MySQL from the primary array no problem, but can't get it to work from the secondary.

I've also tried copying the entire MySQL folder to the new location, with the same results.

I presume it's a permissions issue, but I'm not familiar enough with Linux or MySQL to identify the problem.

Thanks in advance for any assistance!

---

### Post by unutbu on 2009-08-12
Ubuntu installs mysql-server with an apparmor profile, 

/etc/apparmor.d/usr.sbin.mysqld

This apparmor profile restricts the directories into which mysql can read/write. In order for mysqld to read /path/to/secondary/array/DATABASE you must edit /etc/apparmor.d/usr.sbin.mysqld by adding lines like this:
```

  /path/to/secondary/array/DATABASE/ r,
  /path/to/secondary/array/DATABASE/** rwk,
```

After you edit /etc/apparmor.d/usr.sbin.mysqld, you may also need to restart the mysqld server and maybe also apparmor:
```

sudo /etc/init.d/apparmor restart
sudo /etc/init.d/mysql restart

```

PS. On the web page you referenced, 
[http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive](http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive)
Don on August 15, 2008 mentions a little about this issue. You may also find more info about apparmor here: [http://ubuntuforums.org/showthread.php?p=6353900#post6353900](http://ubuntuforums.org/showthread.php?p=6353900#post6353900)

---

### Post by pcamis on 2009-08-12
Thanks so much unutbu - I completely missed the additional comments at the end of that link which covered the issue.  That said, your help with the straightforward commands made life very easy!  I did end up needing to reboot the entire server, but once I did that, everything was as I wanted it.

Cheers!

---

