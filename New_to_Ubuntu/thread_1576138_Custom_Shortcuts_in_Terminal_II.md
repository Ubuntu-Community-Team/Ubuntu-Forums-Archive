---
title: "Custom Shortcuts in Terminal II"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by de Bacon on 2010-09-16
Having read the thread "Custom Shortcuts in Terminal?" I want to take that one step farther if I can.  It seems that I am often changing directories, and now with 10.04 the drives listed in "/media" have unique alpha-numeric strings that are quite long, impossible to remember.  So I tried the template provided by uRock in that thread, 
> 
rabbit@rabbit-desktop:~$ alias now=date
rabbit@rabbit-desktop:~$ now
Thu Sep 16 15:41:26 PDT 2010
rabbit@rabbit-desktop:~$ 
by doing the following
zip@zirp:$ alias 457=cd /media/12121212121-fkfi15151
to find that it didn't work.  Something to do with the space in the command between cd and /, though I could be totally mistaken.  
I do know. It would be nice to have a shorter ID set or unique symbolic names for all my HDDs on the system at times rather than these long strings of nonsense but logical characters.

---

### Post by sisco311 on 2010-09-16
You have to quote the command:
```
alias 457='cd /media/12121212121-fkfi15151'
```

But, labeled devices that are automatically mounted will be mounted in the /media directory using their label as the mount point, /media/<label>. 

To change the label of a partition, go to System -> Administration -> Disk Utility.

---

### Post by de Bacon on 2010-09-16
Well that is great, thank you.

I just read the story of sisyphus as presented in wikipedia (a very abridged version). I am not a reader having a learning disability, but I can have the computer read for me.  That is a great story in short form.  Thanks for putting that link in your signature.
And thanks again for the tips.  I will investigate changing the disk names, that would be probably the easiest method for the long haul.  
:)

---

### Post by sisco311 on 2010-09-16
You're welcome!

*One must imagine Sisyphus happy* is the unofficial motto of the [thread=1125860]Count to 200 - BEFORE MOD RESETS BACK TO ONE![/thread] thread. My favorite game. :)

---

### Post by uRock on 2010-09-16
> **de Bacon said:**
> Well that is great, thank you.

I just read the story of sisyphus as presented in wikipedia (a very abridged version). I am not a reader having a learning disability, but I can have the computer read for me.  That is a great story in short form.  Thanks for putting that link in your signature.
And thanks again for the tips.  I will investigate changing the disk names, that would be probably the easiest method for the long haul.  
:)
I remember Xena doing an episode about Sisyphus.:)

---

