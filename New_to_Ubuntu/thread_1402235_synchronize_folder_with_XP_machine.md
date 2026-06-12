---
title: "synchronize folder with XP machine?"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by testmod on 2010-02-08
I am looking for a way to easily synchronize two folders through my LAN, one on my Ubuntu laptop and the other on my XP desktop.

Could someone please point me in the right direction? Thanks.

---

### Post by 416inversed on 2010-02-08
Probably an easier way, but I use Dropbox to sync folders between systems.

---

### Post by jflaker on 2010-02-08
On the XP system, create a new briefcase

Add to that briefcase any files or folders from your Linux system you want to keep synchronized.  If things change in either location, you will be shown which ones will be replaced.  Should a file change on both sides, you will be asked which way you want to synchronize and then said file will be replaced (careful on this, it is rare, but it happens)

NOW, to synchronize, right click on that briefcase and then choose update all and it will show which files will update.

not an automatic solution, but one that works for me.

---

### Post by testmod on 2010-02-09
> **jflaker said:**
> On the XP system, create a new briefcase

Add to that briefcase any files or folders from your Linux system you want to keep synchronized.  If things change in either location, you will be shown which ones will be replaced.  Should a file change on both sides, you will be asked which way you want to synchronize and then said file will be replaced (careful on this, it is rare, but it happens)

NOW, to synchronize, right click on that briefcase and then choose update all and it will show which files will update.

not an automatic solution, but one that works for me.

Do I need to do anything special to get my XP machine to see my Ubunutu laptop?

specifically:
1) my laptop uses ext4
2) do I find the laptop via Windows Network.. etc?

thanks

---

### Post by testmod on 2010-02-09
> **testmod said:**
> Do I need to do anything special to get my XP machine to see my Ubunutu laptop?

specifically:
1) my laptop uses ext4
2) do I find the laptop via Windows Network.. etc?

thanks


Okay, I've figured out #2, I am setting up Samba as we speak.

---

