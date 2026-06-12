---
title: "Need help installing an app"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-11-14
I am trying to install Kochmorse, a morse code tutor program.

I downloaded it, in a .tar.gz format.

There is an "install" file but it's just the following text:

Just the canonical way:

> sudo python setup.py install

The tutor should be started by calling
> kochmorse

So I tried the sudu python command but the system could not find the file.  So.. do I need to make a folder and copy all of the files in the tar to that folder?  If so, do I then change to that folder and execute the install?

Where is the right place to create a folder to hold an application?

thanks.  using 10.04lts

---

### Post by Foxheadz on 2010-11-14
Did you cd into the folder first?

---

### Post by anewguy on 2010-11-14
You need to _**untar**_ the file into a folder, then execute the sudo....

You may need to change permissions on the setup.py install
to include execute - possibly the same on the kochmorse
program as well.

Dave ;)

EDIT:  If you wouldn't mind, after you get this working, drop me a Private Message and let me know how it is.  I've tried off and on for decades (quite literally) to learn morse to at least get the old-style HAM licenses.  I understand now that at least for some, Morse isn't a requirement anymore, but I'd rather do the whole deal.  One more try couldn't hurt me!

---

