---
title: "Script: help using variable with cp"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jasonmh on 2009-02-10
I'm using GNOME on Ubuntu 8.10 Intrepid, and any help would be greatly appreciated.

I'm needing this script to locate a file, and copy it to the desktop.
**Here is the alternate version which is easier to look at, but still doesn't work :/**
```
#!/bin/sh
# Copies buffered FlashMedia file from Firefox's temp directory to the desktop

FFF_FILE = lsof -p `ps -A|grep firefox|grep -v grep|awk '{print $1}'` | grep /tmp/Flash | awk '{print $9}'

cp $FFF_FILE /home/webdev/Desktop
```

**The original script is...**
```
#!/bin/bash
# Copies buffered FlashMedia file from Firefox's temp directory to the desktop

cp 'lsof -p `ps -A|grep firefox|grep -v grep|awk '{print $1}'` | grep /tmp/Flash | awk '{print $9}'' /home/webdev/Desktop
```

---

### Post by jasonmh on 2009-02-10
bump

---

### Post by blueridgedog on 2009-02-10
Your first awk command results in a list of process ID's (test it on the command line).  After that you are grepping for "/tmp/Flash" from among those id's and you will not find it.  Also, I do not know the reason for the back tick after the first grep.  Perhaps you should just use the second grep and awk.

---

### Post by jasonmh on 2009-02-10
For the command
```
cp 'lsof -p `ps -A|grep firefox|grep -v grep|awk '{print $1}'` | grep /tmp/Flash | awk '{print $9}'' /home/webdev/Desktop
```

[LIST=1]
[*]ps -A|grep firefox|grep -v grep|awk '{print $1}'
   This finds the PID for firefox
[*]lsof -p [pid found in step1]
   This lists the files being used by Firefox
[*]grep /tmp/Flash | awk '{print $9}'
   This finds the Flash Media file found among those in Step2
[*]cp [file found in step3] /home/webdev/Desktop
   This step is supposed to copy that flash file to the desktop
[/LIST]

I can do these steps manually one at a time and everything prints off fine.  But when I put them all together in a script, than it gives me the errors...
```
cp: cannot stat `lsof -p pid | grep /tmp/Flash | awk {print': No such file or directory
cp: cannot stat `}': No such file or directory

```

---

### Post by supersonicdarky on 2009-02-10
here's what i was able to come up with

```
#!/bin/bash

ONE=`ps -A | grep swiftweasel | grep -v grep | awk '{print $1}' | tail -n 1 | head -n 1`
TWO=`lsof -p $ONE | grep /tmp/Flash | awk '{print $9}'`

if [ "$TWO" != "" ]; then
	echo $TWO
	#Copy file here
else
	echo "None found"
fi
```

edit: i use swiftweasel and not ff, which apparently has 3 processes so i needed the head and tail

---

### Post by jasonmh on 2009-02-10
Mental note, probably just a limitation to the cp program itself.
Thank you supersonicdarky, I really appreciate the script you made :)

---

