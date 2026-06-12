---
title: "Unable to run .sh -file. How do I run it?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by madsc89 on 2010-06-18
I'm not a complete newb, but something tells me this is a stupid problem, so I'll post the question in this part of the forum.

I'm trying to run Mobile Atlas Creator 1.8alpha10. This is a java program with a start.sh script for starting it.

On earlier installations, it has worked good, but now I recieve different error messages depending on how I try to run it. 

If I simply GUI-start it, it opens in gedit. In open with -menu there is no obvious start program. In Karmic, I got a promt asking wether to run it, run it in terminal or open it in gedit.

If I try to drag the file into a terminal an press return, this happens:
```
****@***-laptop:~$ '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh' 
bash: /media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh: Permission denied
****@****-laptop:~$ sudo '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh' 
[sudo] password for ***: 
sudo: unable to execute /media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh: Permission denied

```

Content of start.sh:
```

#!/bin/sh

# This file will start the TrekBuddy Atlas Creator with custom memory settings for
# the JVM. With the below settings the heap size (Available memory for the application)
# will range from 64 megabyte up to 512 megabyte.

java -Xms64m -Xmx512M -jar Mobile_Atlas_Creator.jar
```

In properties->permissions, "Allow executing file as program" is ticked, and I'm actually not able to untick it. It stays unticked for a split second, then ticks itself.


How to GUI-start it?
How to terminal start it?

Thanks a bunch!

---

### Post by Perfect Storm on 2010-06-18
```
cd /where/the/file/is
chmod +x file.sh
sh file.sh
```

---

### Post by admiralspark on 2010-06-18
I may be wrong, but don't you have to perform those commands as sudo? ex: sudo chmod +x file.sh

---

### Post by ronnielsen1 on 2010-06-18
> I may be wrong, but don't you have to perform those commands as sudo?  ex: sudo chmod +x file.sh
It's been a while since I've done it in terminal but I don't think you want to do this because then it would be owned by root. I believe you do have to sudo sh file.sh or sudo ./file.sh. I usually right click on the file and mark it executable in properties.

---

### Post by eriktheblu on 2010-06-18
File ownership will determine if you chmod or sudo chmod.

In the GUI, right click and then run in terminal.

From the CLI, 
*This won't work*
```
sh /path/to/file/start.sh
```
*This won't work*

Alternative: create a launcher for the script.

---

### Post by madsc89 on 2010-06-18
> **Artificial Intelligence said:**
> ```
cd /where/the/file/is
chmod +x file.sh
sh file.sh
```

This worked. Thank you.

However. I would still like to be able to run it through nautilus. There is no option to run in terminal when I right click. Help?

---

### Post by jms1989 on 2010-06-18
when you double click on the file, do you see anything that says "Run" or does it just open gedit?

---

### Post by madsc89 on 2010-06-18
Gedit right away. When I right click->properties->open with, this is waht I get. I've just pressed the reset button.

EDIT: Hmmm. Why doesn't "sh '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh'" work, when cd, "sh start.sh" does?
```
***@***-laptop:~$ sh '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh'
Unable to access jarfile Mobile_Atlas_Creator.jar
***@***-laptop:~$ cd '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/'
***@***-laptop:/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10$ sh start.sh
INFO - log4.xml not found - enabling default error log to console
INFO - Total avialable memory to MOBAC: 455.13 MiB
INFO - Proxy configuration applied: system settings

```

---

### Post by eriktheblu on 2010-06-18
> **madsc89 said:**
> 
EDIT: Hmmm. Why doesn't "sh '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/start.sh'" work, when cd, "sh start.sh" does?
I suspect because your script is looking in the current directory rather than an absolute directory.

Say you run the script from ~, when it get's to the meat of it```
java -Xms64m -Xmx512M -jar Mobile_Atlas_Creator.jar
``` 
it's looking in ~ when it should look in /media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/

My advice, create a launcher with this as it's command:
```
java -Xms64m -Xmx512M -jar '/media/sdb1/utvidelse/mobile atlas creator/1.8alpha10/Mobile_Atlas_Creator.jar'
```
Test the command in a terminal first.

---

### Post by Penguin Guy on 2010-06-18
When I double click an executable file, I **always** get a run dialogue (screenshot attached) regardless of where the file is.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160855&stc=1&d=1276888359[/IMG]

---

### Post by madsc89 on 2010-06-18
eriktheblu: Thank you, makes sense.

I do not get that dialog. I got it when I was running Linux Mint 8 (Karmic), but I don't recall seeing it after I installed Lucid (clean ubuntu). 

Any ideas how to enable it?

---

