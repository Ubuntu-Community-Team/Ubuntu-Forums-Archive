---
title: "How to add a script to startup in terminal"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-02-27
hello 

have been working on conky off and on all day....

I need to add a script to my startup routine and can't figure it out.  I tried using the gui, but the change didn't stick.

I'm not interested in enabling root permission on the gui either.

I couldn't find a thread describing this process.
thanks a lot,
wbg

---

### Post by Apollo87 on 2010-02-27
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=208954](http://ubuntuforums.org/showthread.php?t=208954)

---

### Post by wannabegeek on 2010-02-27
hi and thanks for the code

it didn't work however...also, I mistakenly copied my conky config file
to /etc/init.d  and updated it...

how do I remove the two ?

---

### Post by Apollo87 on 2010-02-27
You can remove the update by running

```
update-rc.d -f  blah remove
```
Replace the blah with the file name

Then you can remove the file by deleting it.

---

### Post by Apollo87 on 2010-02-27
Ok so, I tried this on my box and it worked.

First create a file called conky.sh and open it
```
gedit conky.sh
```

and then place this script inside and save it:
```
#! /bin/sh
# conky.sh
# Starts/stops conky

case "$1" in
  start)
    echo "Starting script conky "
    conky & > /dev/null
    echo "Done"
    ;;
  stop)
    echo "Stopping script conky"
    killall -e conky
    echo "Done"
    ;;
  *)
    echo "Usage: conky.sh {start|stop}"
    exit 1
    ;;
esac
exit 0

```
and then make it executable:
```
chmod +x conky.sh
```

This is a script that essentially just starts or stops conky.
 

 Now you need to open up .profile
```
gedit ~/.profile
```

and add the path to the script on the bottom of it followed by start:
```
/path/to/file/conky.sh start
```

Save it and restart. Conky should start at login now.

---

### Post by wannabegeek on 2010-02-28
thanks Apollo,

this is beginning to make some sense to me... :0

wbg

---

### Post by Apollo87 on 2010-02-28
The part about init.d is how you run a script at boot.  If you want to run an application, doing it that way would do nothing; you need to run it login.

---

### Post by WorldTripping on 2010-02-28
There is a different way also.

Make a file called ConkyStart.sh (or whatever).

Put some code like this in it:

```

#!/bin/bash
sleep 15
conky -d -c /home/USERNAME/.conkyFile1.rc
sleep 5
conky -d -c /home/USERNAME/.conkyFile2.rc
exit

```

Where USERNAME is your user name, and the files ending in .rc are your conky config files.

Make it executable:

```

chmod +x ConkyStart.sh

```

Now just use the Startup GUI to add the starting of this file, 

```

sh ~/.ConkyStart.sh

```

This is the preferred way if you have more than one conky config file that you wish to execute at startup, ie one conky at the top of the screen and one at the bottom.

Hope this helps.

WorldTripping

---

### Post by WorldTripping on 2010-02-28
Oh and if you are getting into conky then you REALLY should have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

An absolute wealth of info and the starting point for any conky related questions.

There is also an offshoot here:

[http://conky.linux-hardcore.com/]("http://conky.linux-hardcore.com/")

WorldTripping

---

