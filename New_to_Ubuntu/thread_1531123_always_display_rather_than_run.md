---
title: "always display rather than run"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by g3k0 on 2010-07-14
I installed ubuntu at work and I deal with tons of js and php files.  Every time I double click them it asks whether I want to display or run the file.  How can I make it always display the file?  I am tired of clicking display every time.

---

### Post by belkinsa on 2010-07-14
This Lifehacker link might help you: [http://lifehacker.com/5545319/nautilus-elementary-simplifies-file-browsing-in-linux](http://lifehacker.com/5545319/nautilus-elementary-simplifies-file-browsing-in-linux)

It might be the settings of the normal one also.  Edit>Preferences> Behavior is where it's in.

---

### Post by NoBugs! on 2010-07-14
The problem is those files are marked executable, that's why it asks if you want to run, or display. Right click, go to properties, permissions, and uncheck executable, and it shouldn't ask if you want to run it.

You can also drag the file onto the program's icon to open with the program directly.

---

### Post by g3k0 on 2010-07-14
Ah it is in the normal one's preferences.  Thanks

---

### Post by widda on 2010-07-16
I find this pretty pesky too.It seems to be answered, but:
Is the solution offered above "fix each file as it comes up", in other words, no *overall* solution?
What does "the normal one" mean in this context please.

---

### Post by g3k0 on 2010-07-18
> **widda said:**
> I find this pretty pesky too.It seems to be answered, but:
Is the solution offered above "fix each file as it comes up", in other words, no *overall* solution?
What does "the normal one" mean in this context please.

Hi Widda,

The two solutions mentioned are different approaches to the issue I had.  The first solution was to set nautilus to always display the file rather than prompt me.  This would be an overall solution.  By "normal one" we were referring to the nautilus that comes default on ubuntu rather than the simple nautilus link he gave me.  So all I had to do was go into the menu and change the setting.

The second solution was attacking the root of the issue.  A number of my files are marked as executable which is why I was getting the prompt.  I'm not sure if it is the way I am mounting my other partition or if it is the way ubuntu sees windows files (probably the former), but I found the easy fix for me was to go with the first solution since I can't think of an instance where I would want to have an executable text file.  If I ever do I would probably run it from the terminal anyway.  Sorry for a late response.

---

### Post by widda on 2010-07-19
thanks gdk, yes I know not why or which files open with that prompt, but my abiword docs seem to, and others...
looking forward to blitz method 1!

---

