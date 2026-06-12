---
title: "Broke My Ubuntu"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by soldier4jesus on 2009-09-23
Has anyone ever been trying to do something and was installing stuff and uninstalling stuff to the point where it seems like your Ubuntu may be "broken"?  I was trying to get my computer to play a movie, but never could get it to work.  I have checked out different threads and have tried installing stuf, uninstalling stuff, and typing stuff in the terminal to the point of where, now, if I try to go under the Synaptic Package Manager, I get an error message that tells me that I have another program running in the background and to quit that one first.  I may have to start over and reinstall everything.  I was just wondering if anyone else had had this kind of trouble when they first started on Ubuntu, or am I just an exception to the rule?  

God Bless!!
Wesley

---

### Post by credobyte on 2009-09-23
Restart your computer and this error will disappear.

---

### Post by soldier4jesus on 2009-09-23
Thanks Credobyte.

God Bless!!
Wes

---

### Post by Bucky Ball on 2009-09-23
It usually means Synaptic Package Manager is already open.

---

### Post by MelDJ on 2009-09-23
> **soldier4jesus said:**
> Has anyone ever been trying to do something and was installing stuff and uninstalling stuff to the point where it seems like your Ubuntu may be "broken"?  I was trying to get my computer to play a movie, but never could get it to work.  I have checked out different threads and have tried installing stuf, uninstalling stuff, and typing stuff in the terminal to the point of where, now, if I try to go under the Synaptic Package Manager, I get an error message that tells me that I have another program running in the background and to quit that one first.  I may have to start over and reinstall everything.  I was just wondering if anyone else had had this kind of trouble when they first started on Ubuntu, or am I just an exception to the rule?  

God Bless!!
Wesley

were  you running apt or aadd remove when you tried running synaptic? that could have made synaptic give that error. you cant run another instance of it and open it
edit: as said by bucky ball

---

### Post by soldier4jesus on 2009-09-23
To be honest, I don't remember what all I had done.  I had tried some things in the Add/Remove Package, but then that didn't work, so I had keyed some stuff in the terminal that still didn't seem to get my video to working.  I'm going to see if I can get this all corrected and see if I can get the video to work.  Thanks so much for everyone's replies.

God Bless!!
Wesley

---

### Post by Bölvaður on 2009-09-23
Next time have less vague title on your thread.
And also provide the errors that come up, every single word, along with an explanation on what you where trying to do and how you tried to do it.

---

### Post by corncob on 2009-09-23
For getting video to work [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) is a good tutorial providing code you can paste into terminal.

---

### Post by Bucky Ball on 2009-09-23
If you had 'Add/Remove Programs' already open and you tried to open Synaptics you would have got exactly the error message you described in your first post.

[QUOTE=soldier4jesus]I get an error message that tells me that I have another program running in the background and to quit that one first.[/QUOTE]

---

### Post by LewRockwell on 2009-09-23
> **soldier4jesus said:**
> I was just wondering if anyone else had had this kind of trouble

yes

.

---

### Post by nhasian on 2009-09-23
i believe the two biggest issues with new Ubuntu users is trying to get DVDs to play and adobe flash on websites.  Its a shame that it doesnt work "out of the box" but it is easy enough to install afterwards with:

```
sudo apt-get install ubuntu-restricted-extras
```

then:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

for more info see:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

