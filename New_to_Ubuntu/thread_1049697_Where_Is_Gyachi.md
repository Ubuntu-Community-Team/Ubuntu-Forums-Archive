---
title: "Where Is Gyachi?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-24
I've had to rebuild my laptop from a clean install AGAIN. Last time I did this was earlier this month, and I found Gyachi on either Add/Remove or Synaptics Package Manager. But it's not there now. I don't know how to install it from tar.gz. I'd rather find the package, but it's not in the same place it was a couple of weeks ago.

Does anyone know where to find it?

---

### Post by KIAaze on 2009-01-24
Doesn't seem to have ever been in the official repositories.
Couldn't find it on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

But here are .debs: [https://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](https://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)
(linked to from the official site under downloads!)

---

### Post by ubuntu27 on 2009-01-24
**EDIT:** PLEASE REFER TO [THE NEXT POST]("http://ubuntuforums.org/showpost.php?p=6611929&postcount=4") for a better answer


****************
If you go to the [Download page]("http://gyachi.sourceforge.net/download.shtml") of [GYachi]("http://gyachi.sourceforge.net/"), there is a sentence that says "[All other packages and plugins]("http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575")" 
Clicking on that it transfer to the SourceForge.net site where you can download the application in different formats.


I see that there are deb packages for the _older version_ of Ubuntu.

I think that you will need to add the Ubuntu Gutsy repositories and then install GYachi in order to satisfy dependencies.

_Do NOT update or upgrade any packages_ while you have Gutsy Repo. It could break your system.

After installing Gyachi, _delete the Gutsy repository_. 

Enjoy.

---

### Post by loell on 2009-01-24
current version(s) is in this thread
[http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")

---

### Post by MooseMagnet on 2009-01-24
loell !! That's it:

[http://ubuntuforums.org/showthread.php?t=773802](http://ubuntuforums.org/showthread.php?t=773802)

I was wrong - not repositories - but simplified by a good-will genius.

Thank you, thank you, thank you.

---

### Post by loell on 2009-01-24
np :), if you also like there is also a repo (my PPA), at my sig. :D

---

### Post by MooseMagnet on 2009-01-31
loell: They are gone from the launchpad links. My machine crashed AGAIN, and I need Gyachi again. Please. Thank you.

---

### Post by MooseMagnet on 2009-01-31
Found it on your PPA. Thank you much, again.

---

