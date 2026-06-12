---
title: "[SOLVED] Where is the Wine?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-01-02
According to 

[http://www.simplehelp.net/2007/05/18/how-to-install-windows-programs-in-linux-using-wine/](http://www.simplehelp.net/2007/05/18/how-to-install-windows-programs-in-linux-using-wine/)

, there should be a "Wine File Browser", "Wine [cannot read]", and "Wine Notepad" in my "Applications">"Accessories" tab.

But it is not there. 

What do I do? I have tried reinstalling them, but these three files still do not appear.

Please assist. All useful advise will be greatly appreciated.

Thank you for your time.

Take take care,
RedStarYellowSun

---

### Post by sydbat on 2009-01-02
All my Wine stuff is at the bottom of the "Applications" menu just above "Add/Remove..."

---

### Post by donkyhotay on 2009-01-02
Usually it's right at the bottom of the applications but it might be disabled in your menu, go to:
system > preferences > main menu
and look for the wine entry. If you see it there just checkmark it so that it appears in the actual menu itself. If it isn't there at all you may need to add it manually using that system.

---

### Post by RedStarYellowSun on 2009-01-02
Really?
Then, that website is now obsolete, right?
How do I, then, install Windows programs using the new version?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by ubuntu27 on 2009-01-02
Read [this little guide]("http://www.psychocats.net/ubuntu/wine"). It should be updated already since the authors updates his page frequently.

[Using Wine on Ubuntu]("http://www.psychocats.net/ubuntu/wine")

---

### Post by howefield on 2009-01-02
> **RedStarYellowSun said:**
> Really?
Then, that website is now obsolete, right?

It is getting on for two years old, so probably refers to an earlier version of Ubuntu than you are running.

> How do I, then, install Windows programs using the new version?

Right click the .exe file and select install using wine application (something like that, I can't exactly remember) is probably the easiest way.

---

### Post by jerome1232 on 2009-01-02
To install windows programs you just double click on the windows executable, or you may have to right click it, open with, wine.

---

### Post by ajcham on 2009-01-02
> **RedStarYellowSun said:**
> Really?
Then, that website is now obsolete, right?
How do I, then, install Windows programs using the new version?

Thanks for your time.

Take care,
RedStarYellowSun

Just right-click on the .exe installer, and select ***Open with "Wine Windows Program Loader"***.

---

### Post by RedStarYellowSun on 2009-01-02
Thanks very much!
But, if need be, how would I uninstall Windows programs when there is no uninstall selection?

Thanks again for your time.

Take care,
RedStarYellowSun

---

### Post by ajcham on 2009-01-02
> **RedStarYellowSun said:**
> Thanks very much!
But, if need be, how would I uninstall Windows programs when there is no uninstall selection?

Thanks again for your time.

Take care,
RedStarYellowSun

Applications » Wine » Uninstall Wine Software (refer back to donkyhotay's post if this option isn't present).

Most programs install their own uninstall package anyway, so you can use those also.

---

### Post by RedStarYellowSun on 2009-01-02
Oh... 
Wow, that was easy.

Thanks for the help. I appreciate it.

Take care,
RedStarYellowSun

---

### Post by arvevans on 2009-01-02
Sounds like you may be already familiar with Windows-Program Files area. So, this might be of some help:

Linux has something called hidden files and hidden folders.  These are simply files or folders whos names start with a period (like .wine).  If you are using a file browser you can enable listing hidden files by typing CTRL-H 

If you go to your home directory (/home/user_name) and look for a folder or directory named ".wine", you can go there.  In that location you should find a "c-drive" and can go there.  In the c-drive location you will find most of the familiar windows directory names, including "Program Files".

If you use the Ubuntu menu editor, you can add windows .exe programs to the menu, or to any sub-menu grouping.  Just remember to prefix the "program_name.exe" with "wine" (i.e. "wine notepad.exe") so that wine will be called to execute the windows executable program.

---

