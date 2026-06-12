---
title: "Where did songbird go?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Bandanna on 2009-01-19
After installing packages and other software that I want to use often,
I don't understand where it goes so that I am able to run it...
i,e; desktop icon or a tab under applications.
songbird is just not accessible to me right now because I do not know where it's located.

---

### Post by perlluver on 2009-01-19
> **Bandanna said:**
> After installing packages and other software that I want to use often,
I don't understand where it goes so that I am able to run it...
i,e; desktop icon or a tab under applications.
songbird is just not accessible to me right now because I do not know where it's located.

It is usually located under, Applications>Sound & Video> Songbird.  Most programs you install will be located under Applications.

---

### Post by Elfy on 2009-01-19
If you installed it with a deb then it probably installed to /usr/bin - or at least the exec, you should be able to find things which you wnat to run with

```
whereis songbird
``` for instance, it should have put an entry in the menu - if it's not there - rioght click your menu, edit menu and check for an entry in sounds sub menu.

If it has installed properly, then you could run it from a terminal to check

```
songbird
```

If however you downloaded and extracted the tar file form the songbird site, then it's likely that the excec is still in the folder.

---

### Post by chriswyatt on 2009-01-19
How did you install it?  I got it from GetDeb and it put it in Sound & Video.  Maybe if you used a different install method e.g. compiling it didn't install to Applications menu but just went to /usr/bin/songbird or something similar.  Try this in a terminal and see what comes up:

```
sudo updatedb
locate songbird
```

EDIT: Sorry, too slow to reply, what he said :)

---

### Post by chriswyatt on 2009-01-19
Another thing I'd liked to mention, before I've found that the applications menu doesn't update straight away when I've installed new things, you could try logging out and logging back in to see if it appears under Sound & Video then.

---

### Post by Bandanna on 2009-01-19
Um yea, Downloaded a tar folder and the exec is still in the folder thats how I ran it the first time.
its also got a .png icon within the folder, I'm assuming there is a way I can set this up to where the .png file of abird can turn into a shortcut associated with the songbird executable file.
And it is not within applications>sounds and video Im assuming because it's still in its folder.

after I extracted the package the folder was on my desktop and I dragged and dropped it into the documents folder. 

But I do not want to have to go to 
Places>Documents>Songbird>songbird
Every time I would like to run it.

I do not understand how to use the edit menu feature after right clicking applications.

---

### Post by glotz on 2009-01-19
Right click menu > edit. Then navigate to the sound folder and click on new item. Name is songbirdie and command is the path to the exec. Then finally click on the icon and point to the .png.

It's not difficult, promise.

---

