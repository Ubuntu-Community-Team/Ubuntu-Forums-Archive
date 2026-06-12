---
title: "Cannot Install Anything!"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by youngbuild on 2011-07-21
Whenever I go to install an Application off of the Software Center I get this error

"E:Could not open file /tmp/aptdaemon-frozen-statusFu56Tz/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened. "

I am new to Ubuntu.

---

### Post by wildmanne39 on 2011-07-21
> **youngbuild said:**
> Whenever I go to install an Application off of the Software Center I get this error

"E:Could not open file /tmp/aptdaemon-frozen-statusFu56Tz/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened. "

I am new to Ubuntu.
Hi, try this first.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
if you get errors please post them here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by youngbuild on 2011-07-21
Thank you very much. 
It worked!

From now on Ill keep the code and error in the brackets.

---

### Post by wildmanne39 on 2011-07-21
> **youngbuild said:**
> Thank you very much. 
It worked!

From now on Ill keep the code and error in the brackets.Hi, your welcome! I am glad it worked,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

