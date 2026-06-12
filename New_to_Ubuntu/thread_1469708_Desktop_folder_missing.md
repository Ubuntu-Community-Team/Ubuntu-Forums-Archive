---
title: "Desktop folder missing"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by freesitebuilder on 2010-05-02
About a month ago I was using  Open Office, and when I closed it the couple of files I keep on my Desktop for quick ref had gone, and all my folders/files from my home were displayed. My Desktop folder had gone.

I couldn't solve it, so decided to wait for 10.04 and do a clean install. Now I can't decide what to do - I'd rather upgrade, but will this recreate my Desktop?

I'm planning to delete an old XP partition and add it to my /home, and I've got backups of /home using grsync plus sep backups of Evo, and a couple of other important data files - if I do a clean install, is it simply a case of restoring my /home from grsync, and does it matter that it will be a larger partition?

TIA

---

### Post by Diabolis on 2010-05-02
Yes, you can do a clean install and restore your home folder from a backup. It doesn't matter if its bigger or smaller. Your home folder has nothing special, is just a folder in a different partition.

Did you try to make the Desktop folder again? I'm guessing Gnome would pick it up again.

---

### Post by freesitebuilder on 2010-05-02
Yes, I created a "Desktop" folder, but I'm guessing that it needs special settings or something to be a real Desktop folder as it appears as an ordinary folder along with all the others. I may play about to see if I can fix it if I decide to restore anyway.

---

### Post by Diabolis on 2010-05-02
I checked my Desktop folder and the only difference I see from other folders is its permissions. Try to set the permissions of the folder like this from a terminal:
```

chmod 777 Desktop/

```

---

### Post by Seal Daemon on 2010-05-02
*Desktop *folder really is just a directory and nothing else - you can delete or create it as you wish.

---

### Post by freesitebuilder on 2010-05-05
Did a clean install, but had to do a clean install with format (forgot that the first time!) to recreate my Desktop. I only wish I new how I destroyed it in the first place so I could avoid doing it again!

---

