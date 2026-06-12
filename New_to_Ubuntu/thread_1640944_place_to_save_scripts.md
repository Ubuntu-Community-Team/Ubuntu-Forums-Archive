---
title: "place to save scripts"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-08
Is there an app or anywhere on ubuntu I can use to save and store scripts ...I really ned it for saving scripts I use to push programs to my phone and also for other handy scripts ..any ideas?

---

### Post by wojox on 2010-12-09
Create a folder in your Home Directory called bin. Put your scripts in there.

---

### Post by rburkartjo on 2010-12-09
gmen or could could save your scripts in

/home/xxx/.gnome2/nautilus-scripts

where xxx is your user name

that is where i have mine. but woj idea is great. i save mine in the above because i have to or i cant use the program scheduled tasks for my cron jobs.

---

### Post by gmenfan83 on 2010-12-09
Thank you guys for the help and replies I will try woj idea ....it just gets confusing for me as im new to this to remember so many various scripts

---

### Post by QLee on 2010-12-09
The "generic" answer is that you can save them in any folder (with appropriate permissions) that is in the path of the user or users who you want to be able to run them by entering the name in a terminal. Be sure they have unique names, none with script names already used on the system or which might be added at a later time.

Wojax's reply is a good choice in my opinion.

---

### Post by gmenfan83 on 2010-12-09
Ok so if I put a folder in my home directory called bin then is there a script I can use in terminal to type that will show my scripts that are in that folder so I can have them show up in terminal while in terminal?

---

### Post by QLee on 2010-12-10
[QUOTE=gmenfan83]Ok so if I put a folder in my home directory called bin then is there a script I can use in terminal to type that will show my scripts that are in that folder so I can have them show up in terminal while in terminal?[/QUOTE]
I, for one, don't understand your question, presumably no one else does either since no one replied.

You can use your file browser to see the files in /home/"your username"/bin, just like you would in any other folder (directory).

Or you could enter the command, ls, while in the directory, which will list the contents.

---

