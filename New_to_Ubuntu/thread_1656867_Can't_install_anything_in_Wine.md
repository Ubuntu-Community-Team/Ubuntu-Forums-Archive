---
title: "Can't install anything in Wine"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by nifty542 on 2010-12-31
Hi, all

I am having problems trying to install Omnipage using Wine. I don't think I understand the information in the documentation. 
I think I shall need this as all the Open Source OCR programs I have tried are just not accurate enough- though I would love to be proved wrong, if anyone has a suggestion.
In particular, it say CD in the directory. What does this mean?
Regards
Nifty.
PS Happy New Year

---

### Post by SuaSwe on 2010-12-31
To "cd into a directory" means to browse it. 

Where is this directory? 
Are you able to post a link for the instructions you're trying to follow? 
Is Wine already installed on your computer? 

Normally when installing things in Wine, you'd download the .exe file as you would in Windows, right-click and select "Run in Wine" or something like that - cd-ing into directories the Linux way should not be required, at least not from my experience!

---

### Post by nifty542 on 2010-12-31
Hi
Thanks for the reply. When I try to click on the .exe file in the cd, I get a message telling me that it's not marked as executable.
The documentation I have tried is [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I have tried copying the contents of the cd to a folder I created in the search c drive submenu in Wine. I labelled it Omnipage, then tried to double click on the AutoRun.exe, but still get the same message.
I am using an early 64 bit system with an ATI 512Mb graphics card. AMD 3600 processor and 3Gb of ram. Dunno if that helps any
Regards
Nifty

---

### Post by Verbeck on 2010-12-31
after you copy it to the hard disk, right click the .exe>properties>permissions>check 'allow executing file as a program'

edit: the application rating doesn't look good
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1875](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1875)

---

### Post by nifty542 on 2010-12-31
Hi

Thanks. That has done the trick!

Can't get it to talk to my scanner, but I'll keep trying. It's an Epson DX8400

Thanks for the replies
Regards

Nifty

---

### Post by sandyd on 2010-12-31
> **nifty542 said:**
> Hi

Thanks. That has done the trick!

Can't get it to talk to my scanner, but I'll keep trying. It's an Epson DX8400

Thanks for the replies
Regards

Nifty
will likely not work, check out
[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)
if your using USB.

---

