---
title: "Functioning script not running in crontab"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by bohemen on 2010-09-14
Hi

I have made a perl script that works fine when i run it manually in the command line. However, when this script is triggered from crontab it is not executed. Here is the crontab file

#!bin/sh
# m h  dom mon dow   command
04 01 * * * /usr/bin/perl /script/lg

I have tried both with and without #!bin/sh (just in case)

Do you have any clues?

I have also encountered the same problem at my Mac.

---

### Post by asmoore82 on 2010-09-14
I vaguely remember something about cron not being able to invoke any
interpreters - some type of security feature maybe.

I think you have to make the crontab call the script directly -
so you must set it as executable and make sure it begins like:

```
#!/usr/bin/env perl
# ...
```

---

### Post by MrWES on 2010-09-14
Try
#!/path/to/perl

---

### Post by bohemen on 2010-09-15
Thank you both. the env solution worked like a charm with my perl script. Thanks a lot

However, I have a similar problem with a regular script. It can be run in the terminal manually (in Mac). But again Crontab is putting up resistance;


#!usr/bin/env sh                                                                                                                                               
54 09 * * * sudo echo Backup finished > /testfile.txt
54 09 * * * sudo sh /script/backup.txt

Have also tried not including the env, renaming the script, setting the path to sh and so on.
Any clues?

---

### Post by fatality_uk on 2010-09-15
> **bohemen said:**
> Thank you both. the env solution worked like a charm with my perl script. Thanks a lot

However, I have a similar problem with a regular script. It can be run in the terminal manually (in Mac). But again Crontab is putting up resistance;


#!usr/bin/env sh                                                                                                                                               
54 09 * * * sudo echo Backup finished > **/testfile.txt**
54 09 * * * sudo sh /script/backup.txt

Have also tried not including the env, renaming the script, setting the path to sh and so on.
Any clues?

Rusty bash skills but what stands out your trying to output the file to the root **/** which I don't think you will; have permissions for?

---

### Post by bohemen on 2010-09-15
You are quite right that that might be a problem. However, I do have permission to write there, and it is not that line that is the problem. I just added it to see if crontab was running at all. So this line actually executes and adds the text line to the file. 

It is the script I cannot get to run

---

### Post by da burger on 2010-09-15
I have no experience with cron or cron tab but it sounds like your having the exact same problem again. Ensure /script/backup.txt is executable and starts with the line ```
#!/bin/sh
``` then replace ```
54 09 * * * sudo sh /script/backup.txt
``` with ```
sudo /script/backup.txt
```. Again I'm no expert but that might work.
 
On another note you ran ```
sudo echo Backup finished > /testfile.txt
```. Why have you sudoed that command? The echo command certainly doesn't need it to work, and the write operation doesn't gain any benefit from it. Plus you said you had permission to write there.
Hope this helped.
Angus

---

### Post by bohemen on 2010-09-15
Thanks to all of you. 

The perl script worked fine, but I had to chicken out on the regular script for the MAC (the last post). I therefore downloaded a graphical interface that did the trick. It is called CronniX and is a freeware. works like a charm.

Thank you guys

---

### Post by santiago g on 2012-08-01
> **bohemen said:**
> Hi

I have made a perl script that works fine when i run it manually in the command line. However, when this script is triggered from crontab it is not executed. Here is the crontab file

#!bin/sh
# m h  dom mon dow   command
04 01 * * * /usr/bin/perl /script/lg

I have tried both with and without #!bin/sh (just in case)

Do you have any clues?

I have also encountered the same problem at my Mac.

When running cron tab make sure your script starts with a change directory command where your script resides:

#!/bin/bash
cd /home/path/to/my/script/
commands.....

---

### Post by sffvba[e0rt on 2012-08-01
*Old thread **closed**.*


404

---

