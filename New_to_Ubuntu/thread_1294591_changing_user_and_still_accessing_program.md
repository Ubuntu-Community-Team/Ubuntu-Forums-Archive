---
title: "changing user and still accessing program"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by jmpallen on 2009-10-18
Hi I recently bought a dell laptop and have been introduced tot he world of Ubuntu. I needed to install microsoft office for my daughter (10) and school projects which I managed to do sucessfully by first installing wine.
 
I did all this through the administrator login and now my daughter has logged in and we cannot see Office within the wine menu as it is under administrator.
 
How do I give my daughter access? is there some way to simply add it to her wine menu ?
 
Thanks
 
Jon

---

### Post by Norm24 on 2009-10-18
This won't answer your question but why not use OpenOffice instead of MS Office?

---

### Post by jmpallen on 2009-10-18
Thanks Norm - I have tried this but it is quite different and was very slow and at aged 10 this makes a big difference

---

### Post by saidinesh5 on 2009-10-18
hie,
before i tell you how to do the thing you wanted, here are 3 basic things that you need to know:
1) /home/<username> is similar to C:\Users\<username> of windows vista, so /home/Administrator is your administrator's (home)folder

1.5) in linux prepending a "." to a filename makes it hidden. to view all the hidden files and folders, in the file manager> VIEW> Show Hidden files

2) you already know this, but still, MS office doesnt by default run on ubuntu, so we run it using wine out here... and wine stores all the files
installed by a user in his/ her home folder itself

now most probably(if you didnt change any settings while installation), the MS office installed by you will be stored in /home/Administrator/.wine/drive_c/program files/

once you found the .exe files of word , you can run them by using "wine <filename.exe>" on the command line or "open with wine" right clicking on the file. 

P.S you might be needing to change the file's read write permissions , so if you get stuck at any point, we are here to help you :)

good luck
and happy diwali :)

---

### Post by jmpallen on 2009-10-18
Thanks for your help but to show my real ignorance - I can't find file manager on any menu?  any clues? thanks again

---

### Post by saidinesh5 on 2009-10-18
its okay :) , the file manager (like windows explorer) in ubuntu is called nautilus. in the upper bar, simply go on Places>Computer>Filesystem>home> <the user which you want to view>

---

### Post by jmpallen on 2009-10-18
great thanks I can at least see it now when logged on as my daughter.  I have now gone through the productivity folder to add a shortcut but it still doesn't work and the screen has frozen.  what is the equivalent to cntl-alt-del? and then is there a trick to getting it to run within this screen?
 
thanks again

---

### Post by starcannon on 2009-10-18
> **jmpallen said:**
> great thanks I can at least see it now when logged on as my daughter.  I have now gone through the productivity folder to add a shortcut but it still doesn't work and the screen has frozen.  what is the equivalent to cntl-alt-del? and then is there a trick to getting it to run within this screen?
 
thanks again

[LIST]
[*]There are some methods for trying to soft reboot a frozen linux desktop.
[LIST]
[*][http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)
[/LIST]
[*] Here's a link on installing applications with Wine, for multiple users.
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=917422](http://ubuntuforums.org/showthread.php?t=917422)
[/LIST]
[/LIST]
       
GL and HF

---

### Post by saidinesh5 on 2009-10-18
i could not really follow your question when you meant "the productivity folder" , and ya there is a task manager, which more or less looks the same as the windows task manager. it is called  "gnome-system-monitor". you can run it via.

1) Press Alt + F2 (this will give you a dialogue box like the Run Dialog box)
2) in there type "gnome-system-monitor" (without quotes) to open the task manager

---

### Post by ajgreeny on 2009-10-18
It may be easiest for you to install MS Office again as your daughter's username, though that could mean that you will have to add her to the admin group, and then after installing wine, remove her from that group, if you want to keep her away from admin tasks.

This may sound like a load of hassle, but it will be really quite simple to do.  Come back again if you need to for more info.

---

