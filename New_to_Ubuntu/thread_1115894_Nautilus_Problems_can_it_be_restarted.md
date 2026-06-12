---
title: "Nautilus Problems: can it be restarted?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2009-04-04
Hello,

 I'm experiencing a tedious bug on my Ubuntu 8.04. I've been using it for about an year now, with no problems whatsoever, but this week something started going wrong.

It happens that, sometimes, while I am copying a file to a folder by cutting and pasting it, Nautilus freezes and it won't display anything.

I force quit it and then I try to go back to seeing the folder, but the same problems comes back: anytime I try to reopen the "infected" folder, I have to quit it.

Now, I can still access the folder from a terminal and so I can copy all of the files in a different folder, then kill this folder and then all is well.

However, it has already done this to me three times this week and I would like to find a solution.

Is it possible to restart Nautilus? Otherwise, what could I try?

Thanks!

Cheers

---

### Post by kanikilu on 2009-04-04
I'm not sure if this applies in your case, but a common cause of nautilus locking up seems to relate to having file previews turned on. Can you try turning it off and see if that works?

Open nautilus and go to Edit > Preferences > Preview tab, change all the options to Never.

---

### Post by Peter09 on 2009-04-04
Also nautilus can be restarted from a terminal - 

```
nautilus&
```

---

### Post by futuroimperfetto on 2009-04-04
> **kanikilu said:**
> 
Open nautilus and go to Edit > Preferences > Preview tab, change all the options to Never.

kanikilu, yes it worked beautifully. I have no explanation as to why this happens, but somehow the problem was caused by PDF files I had in a folder, coming from 2 different computers.

Anyway, disabling the preview really does the job and I don't have problems anymore.

Also, thanks Peter09 for the command to restart Nautilus.

I'll have to understand better if the file is corrupted or something (it opens normally, but it annoyes Nautilus).

Thanks everybody

---

