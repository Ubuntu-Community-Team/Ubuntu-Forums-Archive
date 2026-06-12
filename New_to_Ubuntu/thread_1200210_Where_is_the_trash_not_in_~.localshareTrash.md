---
title: "Where is the trash? not in ~/.local/share/Trash"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by jadu on 2009-06-29
Hello,

I just installed bleachbit (that I read about on this forum). I mostly installed it to do what "fileshredder" does in Windows. I read here that there's a command in the terminal to do the same thing, but I want to install something more user-friendly, since  people who don't know Ubuntu will also use this computer. 
The thing is, I can't find the trash. I go to Shred Files in Bleachbit and type trash:/// and it doesn't find it. I saw here that it should be in home/user/.local/share/trash. But in my user folder, there's no .local folder. and when I to to navigator and type  ~/.local it doesn't find it. I know how to get there from the panel, but not from bleachbit.
Any ideas? 
Also, besides shredding specific programs, does Bleach bit do what "fileshredder" does, finding any stray bits of old deleted documents and making them unrecoverable? (I don't know the technical language to explain that). Or is that not even necessary in Ubuntu? Though I do need a  way of deleting that's completely unrecoverable, by anybody.
thanks for any ideas.

---

### Post by Pinball Wizard on 2009-06-29
I was in the same boat. I accidently deleted instead of copying the admin user's keychain files. I could go into the recovery menu and login as root but couldn't find the user trash folder. I ended up having to reinstall the system.

---

### Post by jadu on 2009-06-30
hmm, it's possible that someone deleted the "admin user's keychain files" (though I don't know what that is), since different people use this computer. But I don't know if that's it, since I still can get to the trash from the panel. Any ideas?

---

### Post by jadu on 2009-06-30
hello, I figured out how to find the trash! I had to do control H to show hidden files, to show the .local.
I still have a couple of questions: 
from above:
> Also, besides shredding specific programs, does Bleach bit do what "fileshredder" does, finding any stray bits of old deleted documents and making them unrecoverable? (I don't know the technical language to explain that). Or is that not even necessary in Ubuntu? Though I do need a way of deleting that's completely unrecoverable, by anybody.
thanks for any ideas. 
and also, once I'm in the trash, is there a way to clear all of the trash at once, instead of entering into each folder that's there, and clearing files?
thanks

---

### Post by Pinball Wizard on 2009-06-30
> **jadu said:**
> hmm, it's possible that someone deleted the "admin user's keychain files" (though I don't know what that is), since different people use this computer. But I don't know if that's it, since I still can get to the trash from the panel. Any ideas?

No, if you delete those keychain files then you wouldn't be able to log in through the GUI.

---

