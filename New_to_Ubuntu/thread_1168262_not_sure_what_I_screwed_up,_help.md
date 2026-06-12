---
title: "not sure what I screwed up, help?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by a77ssii on 2009-05-23
trying to download my camera so ended up with gphoto2 which it seems my camera is not compatible with so ended up getting a card reader which is working fine.  I now want to remove gphoto2 from the hdd and it keeps telling me access is denied that it is a root file and I do not have sufficient privileges to delete.  what I am unsure of is using the sudu command with its location which is usr/share/doc/gphoto2

---

### Post by taurus on 2009-05-23
Either run nautilus with root privilege

```
gksudo nautilus
```
or remove it with sudo from a terminal.

```
sudo rm /usr/share/doc/gphoto2
```

---

### Post by 3rdalbum on 2009-05-23
How did you install gphoto and how are you trying to remove it?

---

### Post by Mr-Biscuit on 2009-05-23
dpkg --purge <name of app>  ?

chown 777 /name/of/file ?

/usr/share/doc usually has sub directories within sub directories or a few files.

---

### Post by asmoore82 on 2009-05-23
if you installed it from the Repos, uninstall it from the same way from a package manager,

if you installed from source with a process of
```
./configure
make
sudo make install
```
^if this is the case, you can usually go back to that same source folder and
```
sudo make uninstall
```

---

### Post by a77ssii on 2009-05-24
A big thank you to all that replied.  I used the nautilus command and it worked out fine.  Now can anyone explain what exactly nautilus is?  20 years ago I ran about 95% in the DOS environment trying desperately to avoid windows 3.1 then ended up having to use it at work, it appears I'm now back into the command prompt environment so now I just have to get used to not pointing and clicking 100% of the time and start relearning the code.  Have any of you used the Linux for Dummies book?  If you have is it worth the $$?  I just hate having to rely on others for what I consider stupid simple issues I don't know how to handle.

---

### Post by Didius Falco on 2009-05-24
> **a77ssii said:**
> A big thank you to all that replied.  I used the nautilus command and it worked out fine.  Now can anyone explain what exactly nautilus is?  20 years ago I ran about 95% in the DOS environment trying desperately to avoid windows 3.1 then ended up having to use it at work, it appears I'm now back into the command prompt environment so now I just have to get used to not pointing and clicking 100% of the time and start relearning the code.  Have any of you used the Linux for Dummies book?  If you have is it worth the $$?  I just hate having to rely on others for what I consider stupid simple issues I don't know how to handle.

If you used the Dos command line,you'll soon get back into the groove.

Personally, I think the whole "Dummies", Idiots", etc. line is more suited to those with absolutely no computer experience, though I'd never buy one. Something about giving someone money to call me dumb just rubs me the wrong way. <G>

Here are some good resources to get started:

Here on the forum, there is a whole section devoted to HowTo guides lots of good stuff in there:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

There is also a lot of Community-written documentation available here:

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

A good way to search the forums is this Google search page set up for just that purpose:

[http://www.google.com/search?hl=en&edition=us&q=+++site%3Aubuntuforums.org&btnG=Search](http://www.google.com/search?hl=en&edition=us&q=+++site%3Aubuntuforums.org&btnG=Search)

For a wider Ubuntu-related search, this site is very good:

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

Check out this: 

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

It's a whole pocket guide in PDF format for free. If you like it, you can always buy a physical copy.

Some other resources:

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www.shelldorado.com/](http://www.shelldorado.com/)


[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)

That should get you started. ;)


Regards,

Didius

---

