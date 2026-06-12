---
title: "mounting a dynamic windows 7 disk"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by luigibmth on 2011-06-21
i created a software raid array using disk management in windows 7, i successfully mounted it in ubuntu 11.04 using post 5 in this thread [http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk]("http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk") it works fine however is lost on shut down, is there a way to make it permanent? or do i have to create a file similar to a com file in windows and run it every time i want to access the raid array after a boot?

---

### Post by fabricator4 on 2011-06-26
> **luigibmth said:**
> i created a software raid array using disk management in windows 7, i successfully mounted it in ubuntu 11.04 using post 5 in this thread [http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk]("http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk") it works fine however is lost on shut down, is there a way to make it permanent? or do i have to create a file similar to a com file in windows and run it every time i want to access the raid array after a boot?

Yes, you can write the commands into a [shell script]("http://www.freeos.com/guides/lsst/ch02sec01.html") so that you don't have to type them each time you need to use the drive.  It should also be possible to put this script into the startup programs so that it automatically makes the drive accessible after each login.

---

