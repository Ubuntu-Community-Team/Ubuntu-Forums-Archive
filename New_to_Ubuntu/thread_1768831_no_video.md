---
title: "no video"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Drawstop on 2011-05-27
I have downloaded Kino and when I click on capture I get the message "Warning: raw 1394 kernel module not loaded or failure to read/write/devraw1394".
Please can someone help. Also please note that I am an oldie and have never used a terminal.
What is sudo?
Man thanks for any help.
Drawstop.

---

### Post by KL_72_TR on 2011-05-27
[sudo] = _**su**_peruser _do_ 
It gives some extra power to a simple user in order to execute some commands.

---

### Post by Drawstop on 2011-05-27
Thanks very much. Does this mean I have to type in that phrase before the command each time?

---

### Post by KL_72_TR on 2011-05-27
No [sudo] is given only for special and important commands.
According to this site:[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)
you must change the 'read/write' permissions to /raw1394
> sudo chmod a+rw /dev/raw1394[sudo] - superuser do
[chmod] - change mode
[a] - all users
[+]
[rw] - read/write
[/dev/raw1394] - the file to which you want to change permissions
After this you will be prompted to give your password (or maybe not).
In the end see the changes with [ls] command:
> ls -l /dev/raw1394[ls] - list
[-l] - long (is option for the command [ls])
[/dwv/raw1394]
You must see something like this: 
> crw-rw-rw- ............... /dev/raw1394
Important is to see the [rw] and a [-]dash
But if instead get this result:
> ls -l /dev/raw1394> ls: cannot access /dev/raw1394: No such file or directory it means that the file [raw1394] does not exist in your system.

---

### Post by Drawstop on 2011-05-28
Many thanks for all the help so far but when I type sudo chmod a+rw /dev/raw1394 all I get is "richard@richard-desktop" and a flashing cursor.
I have tried replacing "sudo" with my password and my administrators name and everything I can think of but no joy.
Any suggestions?
Thanks
Richard.

---

