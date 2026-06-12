---
title: "Problem running a python script using cron"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by kvorion on 2009-11-25
Hi All,

I have a python script that does some processing with MySQL and Hadoop. I am trying to run this script periodically using cron.

```

This is what I have in my crontab file:
* * * * * /home/path/to/script/InvokeExtensionCheck.py

```
The problem is that this script does not seem to work because it does things like create log files and run Hadoop jobs.

I also tried:
```

* * * * * python /home/path/to/script/InvokeExtensionCheck.py 

```
which also does not work

My cron did seem to be working because the following worked:
```

* * * * * echo "hello" >> /nutch/code/logs/test.txt

```

Any suggestions are welcome.

Note: The python script works fine on commandline:
./InvokeExtensionCheck.py does what it is supposed to.

---

### Post by kvorion on 2009-11-25
Solved the problem. I realized that cron runs the script in a different context. So it was not getting access to a configuration file that I was trying to access right in the beginning. Used absolute path name for the configuration file, and it started working.

---

