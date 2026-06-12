---
title: "How do I install this file...  What opens .sh files?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by ltipto1 on 2009-11-07
/Downloads/boinc_6.10.17_i686-pc-linux-gnu.sh

---

### Post by Iowan on 2009-11-07
.sh are shell files and *should* be executable from command line. I don't remember if the .sh is required.

---

### Post by twisted_steel on 2009-11-07
Yes, they are executable from the command line, provided the permissions are set up properly.  By default, downloaded files do not have executable permissions set.  You can do this from a terminal window with the following:
```
chmod u+x /Downloads/boinc_6.10.17_i686-pc-linux-gnu.sh
```

This sets executable permissions for just your user.  You can also change this by right-clicking on the file in the file browser and going to the Properties tab.  Select "Allow executing file as program".  Then, run the program directly from the terminal window:
```
/Downloads/boinc_6.10.17_i686-pc-linux-gnu.sh
```Sometimes, it will be fine to do something like
```
sh /Downloads/boinc_6.10.17_i686-pc-linux-gnu.sh
```but it is really dependent on how the script is written ahead of time (what scripting language).  For example, a script written in csh may not run if you try to execute it with bash.

---

