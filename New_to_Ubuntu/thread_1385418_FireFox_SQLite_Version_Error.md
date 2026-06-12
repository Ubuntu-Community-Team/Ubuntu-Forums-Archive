---
title: "FireFox SQLite Version Error"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by cht1963 on 2010-01-19
Since upgrade from 9.04 to 9.10, Firefox refuses to run, and displays the error message 
The application has been updated, but your version of SQLite is too old and the application cannot run.
Window title is "SQLite Version Error"
I have attempted to locate the most recent version of SQLite, but I have no idea which version I need.
I uninstalled / reinstalled both SQLite and FireFox.
I also get the same error with the Galeon browser.
Seamonkey works, however.
Does anyone know what version of SQLite works with Firefox 3.5?
- OR -
How can I install an older version of FireFox that will work with the SQLite that I have?

---

### Post by lovinglinux on 2010-01-19
I guess you tried to re-install **sqlite3** package, which is just a command-line interface for SQLite 3 and it's not used by Firefox.

The correct package of sqlite is **libsqlite-3.0** and the version is **3.6.16-1ubuntu1**.

You could try to reinstall it, along with firefox, firefox-3.5 and xulrunner-1.9.1. You need to go to Synaptic and mark them for re-installation. Don't try to remove libsqlite-3.0 and then re-install, otherwise it will also uninstall a lot of gnome dependencies and probably will break your system. So the re-install is the way to go.

---

### Post by cht1963 on 2010-01-19
Cool that sounds like it will work.  What is the command line to install the libsqlite-3.0?
I tried apt-get and it did not work.
Thanks for the quick response.
Nevermind- found the synaptic package installer.
I tried reinstalling everything and I still get the same error message...
I had libsqlite0 version 2.8.17-6 build1 also installed, so i removed it, and still get the same error message..

---

### Post by synapsys on 2010-01-19
```
sudo apt-get install libsqlite-3.0
```

sorry you said reinstall

```
sudo apt-get --reinstall install libsqlite-3.0
```

---

### Post by cht1963 on 2010-01-19
Still receiving the error message SQLite version too old.
Running from the command line yields:

**christhompson@ubuntu:~$** firefox

(firefox:5546): GLib-WARNING **: g_set_prgname() called multiple times
Aborted
**christhompson@ubuntu:~$** firefox -safe-mode

(firefox:5555): GLib-WARNING **: g_set_prgname() called multiple times
Aborted
**christhompson@ubuntu:~$**

---

### Post by synapsys on 2010-01-19
Have you tried resetting firefox? 

***Caution*** you will lose all settings, cookies, saved passwords, etc

Delete the .firefox folder in your home directory (hidden)

---

### Post by nanotube on 2010-01-19
> **synapsys said:**
> Have you tried resetting firefox? 

***Caution*** you will lose all settings, cookies, saved passwords, etc

Delete the .firefox folder in your home directory (hidden)

two corrections: 
1. it's the .mozilla directory, not .firefox
2. instead of deleting it, just rename it, so that you can restore it if you need to.

---

### Post by synapsys on 2010-01-20
> **nanotube said:**
> two corrections: 
1. it's the .mozilla directory, not .firefox
2. instead of deleting it, just rename it, so that you can restore it if you need to.

what he said

---

### Post by cht1963 on 2010-01-20
Same results= "Application has been updated, but your version of SQLite is too old and the application cannot run."

---

### Post by cht1963 on 2010-01-20
I found the answer on mozilla
[https://support.mozilla.com/en-US/forum/1/507172](https://support.mozilla.com/en-US/forum/1/507172)
There are instructions for making and installing SQLite 
[http://www.sqlite.org/sqlite-amalgamation-3.6.20.tar.gz](http://www.sqlite.org/sqlite-amalgamation-3.6.20.tar.gz)
i used 
sudo make install

Once I did that, Firefox loads.  
This does not show up anywhere in synaptic, though.

---

### Post by wojox on 2010-01-20
So everything is good now? I've never seen that error before.

---

### Post by cht1963 on 2010-01-21
Yes, it is working just fine now.  
When nobody in this forum had heard of the problem, I assumed (my bad) that it was something peculiar to my system.  When I googled the message, i found(in the mozilla forums)  that quite a few others had this same problem, and that it was not limited to Ubuntu, it was happening across the board.  
Fortunately the posted solution works.
Thanks to all...

---

