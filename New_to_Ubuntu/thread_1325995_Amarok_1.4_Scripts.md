---
title: "Amarok 1.4 Scripts"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-14
I am still using amarok 1.4 (using an old repository that someone keeps alive).

I want to install two scripts, however, I am unable to do so as errors pop-up when I try and use them.

First, there is the [Amarok Desktop Script]("http://www.kde-apps.org/content/show.php/amaroK+Desktop+Script?content=20293").

It says it requires pyqt and pykde. So, I have installed pyhton-kde4 and python-qt3 packages. However, I get the following error when running it in Amarok 1.4

```

The script 'desktop.py' exited with error code: 1

sh: kdialog: not found
Traceback (most recent call last):
File "/home/abhiroop/.kde/share/apps/amarok/scripts/desktop/desktop.py", line 31, in <module>
from qt import *
ImportError: No module named qt
```

Second, script is  [Amarok ScreenSaver]("http://www.kde-apps.org/content/show.php/AmarokScreenSaver?content=46488"). It is suggested that KScreensaver is installed (which I have done so).

I get the following error when running it:
```

The script 'AmarokScreenSaver' exited with error code: 1

cp: cannot stat `/home/abhiroop/.kde/share/config/kslideshow.kssrc': No such file or directory
cp: cannot stat `/home/abhiroop/.kde/share/config/kdesktoprc': No such file or directory
Traceback (most recent call last):
  File "/home/abhiroop/.kde/share/apps/amarok/scripts-data/AmarokScreenSaver/configdialog.py", line 3, in <module>
    from configdialog_ui import configDialog
  File "/home/abhiroop/.kde/share/apps/amarok/scripts/AmarokScreenSaver/configdialog_ui.py", line 11, in <module>
    from qt import *
ImportError: No module named qt
/home/abhiroop/.kde/share/apps/amarok/scripts/AmarokScreenSaver/AmarokScreenSaver.sh: line 258: */100: syntax error: operand expected (error token is "*/100")
/home/abhiroop/.kde/share/apps/amarok/scripts/AmarokScreenSaver/AmarokScreenSaver.sh: line 258: */100: syntax error: operand expected (error token is "*/100")
call failed
rm: cannot remove `/home/abhiroop/.kde/share/apps/amarok/scripts-data/AmarokScreenSaver/final/*.png': No such file or directory
Traceback (most recent call last):
  File "/home/abhiroop/.kde/share/apps/amarok/scripts-data/AmarokScreenSaver/configdialog.py", line 3, in <module>
    from configdialog_ui import configDialog
  File "/home/abhiroop/.kde/share/apps/amarok/scripts/AmarokScreenSaver/configdialog_ui.py", line 11, in <module>
    from qt import *
ImportError: No module named qt
/home/abhiroop/.kde/share/apps/amarok/scripts/AmarokScreenSaver/AmarokScreenSaver.sh: line 258: */100: syntax error: operand expected (error token is "*/100")
cp: cannot stat `/home/abhiroop/.kde/share/config/kslideshow.kssrc_orig': No such file or directory
cp: cannot stat `/home/abhiroop/.kde/share/config/kdesktoprc_orig': No such file or directory
call failed

```

I'm guessing both problems stem from the fact that certain kde directories are required to make these scripts work. I have no problem installing and configuring these packages and directories if someone would be kind enough to help me figure out what they were.

Thanks!

---

### Post by abhiroopb on 2009-11-14
Bump!

---

### Post by abhiroopb on 2009-11-22
bump

---

### Post by morganpatrick on 2009-11-25
I'm having similar problems with missing helper applications that pertain to amarok. To address your issue, I installed weekalarm, an alarm clock script, and i was getting errors. I went to the page that hosted the script and it told me what dependencies I needed to run it, then i installed them and it worked.

You can also go to the script and click on about and this should tell you what your dependencies are.

---

### Post by abhiroopb on 2009-11-25
I have installed all the required dependencies but it still didn't seem to work. Would you mind trying out the two scripts and letting me know what dependencies were required please.

---

### Post by statmonkey on 2009-12-05
You might want to [check this thread]("http://ubuntuforums.org/showthread.php?t=157283").  I am having similar issues with different scripts (I am running Jaunty but sure it is the same)I am pretty sure it has something to do with the kde setup on your machine.  On a side note glad to see 1.4 still works in Koala makes me more likely to upgrade.  

I am testing some scripts for amarok now and if I come to any conclusions will post it here.

Well that was quick!

Yes, I can confirm that the answer is as posted in the other thread.  "sudo apt-get install kdebase-bin" without the quotes of course.

---

### Post by abhiroopb on 2009-12-30
Thanks for the help. I'm getting this error now, for the desktop script:

```

PyKDE (KDE bindings for Python) is required for this script

```
I have installed Python-KDE4 (which I assume is the same thing).

The screensaver script installs fine, but I'm not really sure how to launch it. I installed kscreensaver but I'm not sure how to use it. there is no menu entry and putting kscreensaver in the terminal displays that the command is not found.

Thanks!

---

