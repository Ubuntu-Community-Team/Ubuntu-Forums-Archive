---
title: "Empty Hard Drive showing as half full"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Hans-Black on 2010-05-06
after some problems mounting and taking ownership of two empty Hard drives see the link for how it was solved

[http://ubuntuforums.org/showthread.php?t=1472845&page=1](http://ubuntuforums.org/showthread.php?t=1472845&page=1)


now one of them (an IDE drive) is showing as half full its a 500gb drive empty, apart from the lost+found" folder and the property's tab only says that is 16kb big but it is also showing 234.7 Used and 223.7 free I have copied stuff to the drive and then moved it off so could it be that ubuntu hasn't updated the TOC if this is the case how do i fix this? would formating change the UUID?

Thanks

Hans

---

### Post by Silent Warrior on 2010-05-06
Hm, are you browsing it while showing hidden files? (Ctrl+H in Nautlius, I believe.)
I'm not sure if checking folder-properties gives you the best information. Try Disk usage analyser or whatever it's called, see what that tells you.

I doubt formatting would change the UUID, but I don't know for sure. Maybe you should, like, not experiment? :)

---

### Post by -humanaut- on 2010-05-06
could you put type this in a terminal and post back sudo fdisk -l

---

### Post by Hans-Black on 2010-05-06
I have checked my hiden files and i have a trash folder that is 211gb big. the folder name is .trash-1000 is it safe to just delete this folder? 


and before anyone asks yes i have tried emptying the Deleted items from the desk top :P

---

### Post by Silent Warrior on 2010-05-06
Ah, that Trash-folder would be it, then. It's technically safe to remove - not a system-file - but with that amount of data, I hope you're sure you want to remove it.
Like I said, though, you won't hurt the OS one bit by removing it.

---

### Post by Hans-Black on 2010-05-07
Thanks, I deleted the Trash folder it was a strange Zenish feeling putting the trash folder into the trash folder, i thought i heard the sound of one hand clapping as i was doing it :P

---

### Post by Silent Warrior on 2010-05-08
:D Good one!

---

