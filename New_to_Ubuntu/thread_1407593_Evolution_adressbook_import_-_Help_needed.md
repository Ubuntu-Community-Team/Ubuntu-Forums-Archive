---
title: "Evolution adressbook import - Help needed"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Tanayar on 2010-02-15
Hello everybody!
I'm very sorry if I'm stealing your time, but I've spent my day searching for help without any luck.

And here comes my problem:
I wish to import my adressbook that I've exported to .vcf format into Evolution. I can't find any menues at all and I'm starting to feel pretty stupid ](*,)

Any help appreciated ^^
/Tanayar

---

### Post by hemimaniac on 2010-02-15
in evolution on the bottom left there are 4-5 icons, Mail, Contacts, Schedule, tasks, notes. click the contacts icon, the adress book will open up, click file > import

---

### Post by Tanayar on 2010-02-15
Well, I pressed the contacts icon and the file menu doesn't show up (I uploaded a picture, to make things clear).
I suppose that the menu is hidden, how do you make it visible?

Thanks for replying btw (:

---

### Post by hemimaniac on 2010-02-15
wow, thats way different then the usual default setup, on the main page of evolution there is an import feature as well, in your case you may need to default to a more standard theme (if that is not OSX) if it is im lost and if unanswered here, you may have to hit up the evo forums

---

### Post by Tanayar on 2010-02-15
Thanks for the tip! I would never figure out that my desktop theme may be the source of my problem (:

Wow, that's weird o:
I realised that I installed Gnome Global Menu today, but didn't like it. So I removed it from my panel, but now I added it again to my panel. And there was my import function :D

Thanks for help (:

I will update on it later if uninstalling it make it come back (:

---

### Post by hemimaniac on 2010-02-15
In addition (glad you're sorted) it some times helps when giving/receiving instructions or help to revert to the stock themes as they are more familiar and most tutorials are written, or given with them in mind. You can always switch back to the preferred theme after troubleshooting/repairing

---

### Post by Tanayar on 2010-02-15
Now, I knew what to search for. Finding a solution was easy :biggrin:

I found a solution [here]("http://ubuntuforums.org/showthread.php?t=987341"):

> **cIIIz said:**
> it's easy:

open gconf-editor
```
gconf-editor
```

and then go to this path
```
/apps/gnome_settings_daemon/gtk_modules
```

There you see the entry for "globalmenu-gnome", just un-check it and it's back to normal. :KS

Thanks for the support (:

---

