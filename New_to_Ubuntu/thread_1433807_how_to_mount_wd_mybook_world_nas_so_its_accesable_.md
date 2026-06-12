---
title: "how to mount wd mybook world nas so its accesable in all apps"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by shaunandej on 2010-03-19
how can i mount my wd mybook world nas so its accesable in all apps 

for example when im in transmision and brows for a save directory it does not show up but when i browse in places its there to explore

---

### Post by JerichoKru on 2010-03-19
Typically, everything that isn't part of the root filesystem is mounted in /media/

So, in transmission, browse menu -> root (/) -> media. It should be there IF you mounted it.

---

### Post by Morbius1 on 2010-03-19
I'm guessing you're using Nautilus to access the NAS.

When you use nautilus it creates a mount point automatically but it's in a hidden directory . It's at /home/your_user_name/.gvfs. You have to enable Nautilus to "see" that directory by going to:

**Nautilus > Edit > Preferences > View > Show hidden and backup files**

If your application cannot access the hidden directory you can create a symbolic link to a non-hidden directory. For example:

Open **Terminal**
Type **mkdir /home/your_user_name/NetShares**
Type [B]ln -s /home/your_user_name/.gvfs /home/your_user_name/NetShares

[/B] Then your app can browse to /home/your_user_name/NetShares

---

### Post by shaunandej on 2010-03-19
> **Morbius1 said:**
> I'm guessing you're using Nautilus to access the NAS.

When you use nautilus it creates a mount point automatically but it's in a hidden directory . It's at /home/your_user_name/.gvfs. You have to enable Nautilus to "see" that directory by going to:

**Nautilus > Edit > Preferences > View > Show hidden and backup files**

If your application cannot access the hidden directory you can create a symbolic link to a non-hidden directory. For example:

Open **Terminal**
Type **mkdir /home/your_user_name/NetShares**
Type [B]ln -s /home/your_user_name/.gvfs /home/your_user_name/NetShares

[/B] Then your app can browse to /home/your_user_name/NetShares

thanks this worked like a charm well worked after i typed ln rather than in but i went onto a linux comd wiki so lernt a few new things

---

### Post by Nibbos on 2010-05-31
I've been desperately trying to make my WD MyBookWorld visible to Transmission for days - but all I get is 'access denied' - I tried your suggested method above but the 'access denied' is all I get.

If anyone can help me get my WD box to be visible by apps on my Ubuntu machine I would be extremely happy (and so would my wife and daughter)!

Thanks in advance.

Nibbos

---

