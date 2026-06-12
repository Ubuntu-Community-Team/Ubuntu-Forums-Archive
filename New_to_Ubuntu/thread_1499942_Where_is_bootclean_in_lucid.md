---
title: "Where is bootclean in lucid?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-06-02
A few days back, after I upgraded to lucid, /tmp was not being cleared at reboot. I made a [post]("http://ubuntuforums.org/showthread.php?t=1463485") and after a few days (and some upgrades), it started working again. Now, again it is not working. TMPTIME is 0 in /etc/rcS.

It is really frustrating. Does bootclean has anything to do with it? Any suggestion will be appreciated.

---

### Post by arrange on 2010-06-02
Cleaning the */tmp* is done by **/etc/init/mounted-tmp.conf** now.

---

### Post by mmasroorali on 2010-06-02
Thanks. Since my /tmp does not get cleared at boot, I assume that it is not working. What is it I can do to make it work?

---

### Post by arrange on 2010-06-03
OK, can you please post the output of```
status mounted-tmp
grep TMPTIME /etc/default/rcS
mount
ls -al /tmp
cat /etc/init/mounted-tmp.conf
```

---

### Post by mmasroorali on 2010-06-03
> **arrange said:**
> OK, can you please post the output of```
status mounted-tmp
grep TMPTIME /etc/default/rcS
mount
ls -al /tmp
cat /etc/init/mounted-tmp.conf
```

Attached in the same order. Thanks in advance.

---

### Post by arrange on 2010-06-03
All looks OK, but still */tmp* has not been emptied, strange...

Could we do some debugging? Please open the file ```
gksudo gedit /etc/init/mounted-tmp.conf
```and insert 2 lines of code into it, so instead of```
...
task

script
    . /etc/default/rcS

    cd "${MOUNTPOINT}"
    rm -f .X*-lock
...

```

you'll have (indentation is not important)```
...
task

script
	exec > /var/log/mounted-tmp.log 2>&1
	set -x

	. /etc/default/rcS


    cd "${MOUNTPOINT}"
    rm -f .X*-lock
...

```Save the file and restart the computer. Then post the contents of **/var/log/mounted-tmp.log** and ```
grep -w init /var/log/syslog
```

---

### Post by mmasroorali on 2010-06-03
Thanks again. Files attached. I had to rename the second one, since the original one was termed as an invalid file.

---

### Post by arrange on 2010-06-03
Do you have *findutils*?```
which find
dpkg -l | grep find
```

---

### Post by mmasroorali on 2010-06-03
Yes, find seem to be in the system.

masroor@rafid-hamiz:/tmp$ which find
/usr/bin/find
masroor@rafid-hamiz:/tmp$ dpkg -l | grep find
ii  findutils                                       4.4.2-1ubuntu1                                        utilities for finding files--find, xargs
ii  kfind                                           4:4.4.2-0ubuntu2                                      file search utility for KDE 4
ii  mlocate                                         0.22.2-1ubuntu1                                       quickly find files on the filesystem based o
masroor@rafid-hamiz:/tmp$ 

Anything to do with the path of find at boot time?

---

### Post by arrange on 2010-06-03
[COLOR="Silver"]Anything to do with the path of find at boot time? [/COLOR]
It definitely looks like that, doesn't it?

I would change the file again, this time add **echo $PATH**```
...
        exec > /var/log/mounted-tmp.log 2>&1
	set -x
        echo $PATH

```
and change *find* into **/usr/bin/find**```
...
    /usr/bin/find . -depth -xdev $TEXPR $EXCEPT ! -type d -delete
    /usr/bin/find . -depth -xdev $DEXPR $EXCEPT -type d -empty -delete

```Then restart and check the log again.

---

### Post by mmasroorali on 2010-06-03
It worked once, the stopped working. The last line of log file is really puzzling. See the attached files.

But is not the apparent bug affecting others as well?

---

### Post by arrange on 2010-06-04
Now this is really weird. *Not found* should mean the command/file does not exist :(

Does the *find* command work normally from the Terminal? Try running this script (I've changed it so that it does not delete anything, just lists it)```
#! /bin/sh
cd /tmp
EXCEPT='! -name .
            ! ( -path ./lost+found -uid 0 )
            ! ( -path ./quota.user -uid 0 )
            ! ( -path ./aquota.user -uid 0 )
            ! ( -path ./quota.group -uid 0 )
            ! ( -path ./aquota.group -uid 0 )
            ! ( -path ./.journal -uid 0 )
            ! ( -path ./.clean -uid 0 )
            ! ( -path "./...security*" -uid 0 )'
find . -depth -xdev $EXCEPT ! -type d
exit 0
```

If this works, I would try reinstalling *mountall*```
sudo rm /var/cache/apt/archives/mountall*
sudo apt-get --reinstall install mountall
```During the reinstall it may ask you if you want to keep your current version of *mounted-tmp.conf*, say **no**.

---

### Post by mmasroorali on 2010-06-04
The script you provided clearly works, and find is there. Really puzzling. 

Out of sheer desperation, I have decided to go for complete reinstallation of Lucid, which I have not done for the last four or five upgrades. This is against my philosophy, I have always wanted to find the reason. But when I am going for reinstallation of mountall, why not go for reinstllation of the system?

Please accept my sincerest thanks for the wonderful help you provided in the last couple of days.

---

### Post by arrange on 2010-06-04
> **mmasroorali said:**
> ...
 But when I am going for reinstallation of mountall, why not go for reinstllation of the system?
...This is not the same, is it? Sometimes a file is just corrupted, or contains some invalid (and invisible) characters and the easiest way is to rewrite it. This is what the reinstall would have done. You gave up too soon :)

---

### Post by mmasroorali on 2010-06-04
Yes, I agree with you that perhaps I gave up too soon. But, strange world, it does not work even after a complete reinstallation. Right now I can not reboot my machine (all the those software installations after a new installation), I will post the files in a a couple of hours.

---

### Post by mmasroorali on 2010-06-04
Now it works (at least it worked for two reboots) after path for find is added to mounted-tmp.conf. I will have to cry out again if it stops working at some point.

---

### Post by frederickjh on 2010-07-07
Hi all!

This problem is related to the new startup system that is now used to start more startup programs in Lucid. 

tall-male figured this out and his post on how to fix it is here.

[http://ubuntuforums.org/showthread.php?p=9558012#post9558012](http://ubuntuforums.org/showthread.php?p=9558012#post9558012)


The problem is upstart starts things in parallel and if the job tries to run before all the piece are in place. The job will fail.

---

