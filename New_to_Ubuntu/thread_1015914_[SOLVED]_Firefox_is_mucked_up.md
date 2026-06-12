---
title: "[SOLVED] Firefox is mucked up"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by laurielegit on 2008-12-19
Basically firefox is f/mucked up. See below for details.

I was doing something or other in a /usr/share folder when I accidentally clicked a xml file. It opened it in firefox, so I closed it. I was using sudo nautilus for this (I know, I should of used gksudo). When I started firefox later on I had lost all of my bookmarks, settings, history and the back, forward, stop and reload buttons had stopped working. The address bar worked in a very strange way. It did not load a homepage. The history tab is still empty despite my browsing.

Does anyone now I can get back to what I had before (with or without my original settings)

Thanks,

Laurie


Solutions:

Create new profile with ```

firefox -ProfileManager
```

---

### Post by Elfy on 2008-12-19
Can you run this in a terminal, see if it's been changed

```
ls -al .ICEauthority
```

It should afaik be owned by you not root.

---

### Post by laurielegit on 2008-12-19
```
laurie@Edgar:~$ ls -al .ICEauthority
-rw------- 1 laurie laurie 8387 2008-12-19 18:54 .ICEauthority
laurie@Edgar:~$ 
```

I haven't a clue what that did. Could someone explain what that command did, so I may learn something out of this tragedy (apart from using gksudo not sudo).

Thanks,

Laurie

---

### Post by Elfy on 2008-12-19
I wanted to check that the file was still owned by you, which it is - that can be one of the consequences of using sudo.

There is a manual for most commands - accessed througha terminal, for instance man ls

ls - is a command which will list directory contents, I was only interested in the one file though - try it in a terminal on your home by running ls

-al are options - a for showing all not ignoring any hidden files and the l is for long format

As it is the file appears to be ok. You can try and restore the bookmarks etc form a backup.

Open firefox, then Bookmarks, Organise Bookmarks - then in the new window Import and Backup - Restore - if there are any backups there see if any brink your bookmarks back.

---

### Post by laurielegit on 2008-12-19
> **forestpixie said:**
> Open firefox, then Bookmarks, Organise Bookmarks - then in the new window Import and Backup - Restore - if there are any backups there see if any brink your bookmarks back.

I did this and was told that it was "Unable to process the backup file." I am less concerned about that than the fact that firefox cannot do most of the basic functions I use it for. When I opened it using gksudo firefox I got a default setup, yet when I open it as a normal user it cannot do many basic functions. I have my bookmarks backed up with foxmarks so they do not matter as much. It is getting a working firefox that I would like.

Thanks,

Laurie

---

### Post by AlanR8 on 2008-12-19
Had exactly the same issue today. I'm running Kubuntu with KDE 4.2 Beta. An update today caused the exact same symptoms.

Have not sorted it but the workaround was to install Opera and import my bookmarks from Foxmarks! Sorry if that doesn't help you!

I tried a full remove and replace of FF but the symptoms persist.

Any help would be appreciated but I'm begining to like Opera....

---

### Post by laurielegit on 2008-12-19
> **AlanR8 said:**
> Had exactly the same issue today. I'm running Kubuntu with KDE 4.2 Beta. An update today caused the exact same symptoms.

Have not sorted it but the workaround was to install Opera and import my bookmarks from Foxmarks! Sorry if that doesn't help you!

I tried a full remove and replace of FF but the symptoms persist.

Any help would be appreciated but I'm begining to like Opera....

I did the same, except I'm using "Sea-monkey" and I don't like it. I might try opera though. Christmas hols, and I've got plenty of time to try this opera lark.

Laurie

---

### Post by AlanR8 on 2008-12-19
Give Opera a go!

It's not the same as FF but is nice to look at and works well. If you had all your media plugins in FF they should come over to Opera.

Sitll ont found the sepll cheque

---

### Post by jay li on 2008-12-19
Have you try run firefox in safe mode (code: "firefox -safe-mode) and see his behavior?

---

### Post by Elfy on 2008-12-20
Or make a new profile - from a terminal start firefox with

```
firefox -ProfileManager
```

---

### Post by Zeedok on 2008-12-20
I think I have had this problem with Firefox before (on Windows if memory serves) and I think that your localstore.rdf is probably corrupted.  When this happens the bookmarks, some extensions and things like your homepage etc stop working properly.  Maybe when you opened and closed firefox quickly it corrupted the localstore.rdf??  [Here's a wiki page from Mozillazine]("http://kb.mozillazine.org/Corrupt_localstore.rdf") with instructions on how to fix it.

---

### Post by laurielegit on 2008-12-20
> **forestpixie said:**
> Or make a new profile - from a terminal start firefox with

```
firefox -ProfileManager
```

This worked, thanks. Opera is nice, but I still prefer ff.

Thanks again,

Laurie

Edit: Lots of other replys but I'm happy with what I've got. Thanks all

---

### Post by AlanR8 on 2008-12-20
Worked for me as well, thanks

---

### Post by presence1960 on 2008-12-20
Laurielegit, you never again have to worry about firefox  settings being lost again. I have been using my first and only Firefox & Thunderbird profiles created a few years ago. Check out my post on this link [http://ubuntuforums.org/showthread.php?t=1016719&page=2]("http://ubuntuforums.org/showthread.php?t=1016719&page=2") Whether your current profile gets corrupted, you upgrade or reinstall your OS or whatever the case this will insure your Firefox & Thunderbird settings, bookmarks, emails, add-ons etc will always be available when you need them.

---

