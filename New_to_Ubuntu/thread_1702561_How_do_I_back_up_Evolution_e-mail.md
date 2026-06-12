---
title: "How do I back up Evolution e-mail?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-08
How would I back up Evolution e-mail in case there is a hard drive crash?

---

### Post by slooksterpsv on 2011-03-08
Open Evolution, go to File -> Backup Settings... and save it to your backup solution (External hard drive, dropbox, etc.).

Then if you ever have to setup evolution again, just import the backup file you made and it should bring back everything. At least to my understanding.

---

### Post by dionysius on 2011-03-08
Or just copy everything that's in the 'hidden' Evolution folder in your home directory. 

/home/yourname/.evolution 

That's where everything is stored, email, signatures, etc.

---

### Post by slooksterpsv on 2011-03-08
> **dionysius said:**
> Or just copy everything that's in the 'hidden' Evolution folder in your home directory. 

/home/yourname/.evolution 

That's where everything is stored, email, signatures, etc.

But if you copy that back you still have to setup the accounts again... hmmm I wonder if you do if you have the restore file? I wouldn't think so (except passwords), but I could be wrong.

---

### Post by amauk on 2011-03-08
> **dionysius said:**
> Or just copy everything that's in the 'hidden' Evolution folder in your home directory. 

/home/yourname/.evolution 

That's where everything is stored, email, signatures, etc.

Careful,
Later versions of evolution have split the locations of general settings and account specific stuff

general settings are in ~/.evolution
account specific settings (including actual emails) are in ~/.local/share/evolution

---

### Post by dionysius on 2011-03-08
> **amauk said:**
> Careful,
Later versions of evolution have split the locations of general settings and account specific stuff

general settings are in ~/.evolution
account specific settings (including actual emails) are in ~/.local/share/evolution

Ah, I wasn't aware of that. But then I backup everything in /home so that would include stuff under ~/.local

Thanks.

---

