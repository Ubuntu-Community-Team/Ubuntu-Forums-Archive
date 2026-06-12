---
title: "Getting wine to work"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by josephusnd on 2009-01-10
I have just switched for windows vista to ubuntu and I need to use word 2003. I have wine and it's working but it won't install word.

Also need pythony 2.6 to work too.

---

### Post by Oak37 on 2009-01-10
What are the error(s) that appear when you try to get it to work?

---

### Post by josephusnd on 2009-01-10
It doesn't open in wine, a box pops up saying "This medium contains software intended to be automatically started. Would you like to run it?"
i press run and it says it can't find autorunner.

---

### Post by Oak37 on 2009-01-11
You'll need to navigate into the directory containing the software, presuming the software is on a cd that location should be in /media/cdrom or /media/cdrom0.
```
cd /media/cdrom
```

Use the ls command to see the contents of the cd
```
ls
```

You should be looking for a file like setup.exe or install.exe, then run
```
wine install.exe
``` or
```
wine setup.exe
```

This should start the installer and hopefully install it without any problems!

---

### Post by josephusnd on 2009-01-11
Thanks a ton!:D Every thing worked out perfectly.

---

### Post by Kellemora on 2009-01-11
Hi Joseph

I'm a small (very small) publishing company, we do a few of those advertising pamphlets you see for tourist traps.

We switched from msWord over to Open Office Writer, and after a very short learning curve, productivity levels zoomed upward.  Because we don't have all those problems we had with msWord, like images jumping around just as were ready to go to print, etc.

New users not familiar with msWord learn Open Office much faster, because everything is LOGICAL.
For Example:  If you want to change the margins on your page, you look under FORMAT, since page margins is a Formatting Operation.
In msWord, you have to look where you would do File Operations, under FILE to find the Formatting Options for a Page in a Document.  Ridiculous!
But for those experienced in msWord, when trying to use Open Office Writer and they look in the WRONG PLACE for something, I just tell them, lean back and think, where is the LOGICAL place to find that command.  Forget about where Windows put it!  It probably wasn't where it belonged and took you a long time to get used to it NOT being where it SHOULD BE............

Open Office is much more Powerful than msWord too!

So you should at least give it a try!

Especially since msOffice Ultimate is $679.95 and
Open Office is FREE...........

TTUL
Gary

---

### Post by josephusnd on 2009-01-13
Well, the only reason i need word is because my school uses it. Other than that I am deftly going to be using Open Office.:)

---

