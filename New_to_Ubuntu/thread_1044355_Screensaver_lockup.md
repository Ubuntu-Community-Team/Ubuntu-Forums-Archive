---
title: "Screensaver lockup"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by PeterCat on 2009-01-19
I was looking at the different screensavers available, got to "Molecules", the screen showed text "Creating Molecule" or "building molecule", something like that.  That's it, locked up right there.  I had to do a hot restart.  Now if I go to System/Preferences/Screensaver, it opens on "Molecules" and locks up again.  I can't change it.  Can anyone help me with this?

I went to Ubuntu when Microsquiff decided that my product key for my XP was no longer valid.  Glad I did. Only inertia kept me from doing it long ago.

---

### Post by compiledkernel on 2009-01-19
3d Drivers installed correct? 

That specific screensaver is rather 3d dependent.

---

### Post by tra4d on 2009-05-06
I have the same problem - you can't open the screensaver gui to change it because it locks up.

What/where are the config files for the screensaver?  Can it be changed from a text config file?

-Scott

---

### Post by tra4d on 2009-05-06
Looks like this could be a bug or a hardware/driver issue (when running an intensive screen saver).

Found this bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/101943](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/101943)

Which may or may not be what we are experiencing, but they do have this solution (about 1/2 way down):

chmod -x /usr/lib/xscreensaver/${screensaver-to-disable}

In my case it was the molecule screensaver.

Also found this thread, which has the config file for the 'selected' screensaver:

[http://itknowledgeexchange.techtarget.com/itanswers/screensaver-lockup-in-ubuntu-804/](http://itknowledgeexchange.techtarget.com/itanswers/screensaver-lockup-in-ubuntu-804/)

The file is /home/<your-login>/.gconf/apps/gnome-screensaver/%gconf.xml

Hope this helps.

-Scott

---

