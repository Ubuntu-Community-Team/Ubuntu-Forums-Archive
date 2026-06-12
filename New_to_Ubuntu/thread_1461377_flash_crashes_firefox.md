---
title: "flash crashes firefox"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Existance0 on 2010-04-24
Every time I go to a youtube page or any page that has flash on it firefox will simply begin to load the flash content and then crash does anyone know what I can do to fix this?

---

### Post by xumuk37 on 2010-04-24
is your computer x64?

---

### Post by wojox on 2010-04-24
You could try here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by trig on 2010-04-24
What is your system specs, and is this a new problem?

---

### Post by Existance0 on 2010-04-24
My system specs... I have no clue lol this computer is an ancient server I pulled out of my attic hold on a second why I look them up.

...
...
...


[http://support.dell.com/support/edocs/systems/sgeck/sm/Intro.htm#TechnicalSpecifications](http://support.dell.com/support/edocs/systems/sgeck/sm/Intro.htm#TechnicalSpecifications)

Is this a new issue... uh I guess so it just started when I began using this system because my good computer had some hardware issues and I am unable to repair it right now.

---

### Post by Existance0 on 2010-04-24
> **wojox said:**
> You could try here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

The issue that seemed closest to my issue didn't fix it the code randomly aborts for no reason.
```
arie@DT:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libdns35 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
arie@DT:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libdns35 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
arie@DT:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libdns35 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.

```

---

### Post by Aped on 2010-04-24
There are a number of different flash players available for Firefox. If you can't get one working, my suggestion would be to just try one of the others. Think there were 3, last I checked.


edit: anticlimactic 100th post! Will the inanity ever end?

---

### Post by Existance0 on 2010-04-24
I fixed it :p

---

### Post by wojox on 2010-04-24
What did you do?

---

### Post by ddecator on 2010-04-24
If you are using the daily PPA, then there was an issue with Flash not running properly as a separate process from Firefox. It got fixed for Firefox 3.6.x recently, and the fix for Firefox 3.7.x should be available soon (if not already).

---

