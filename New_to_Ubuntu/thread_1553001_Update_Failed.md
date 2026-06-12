---
title: "Update Failed?"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Cha0sBG on 2010-08-14
Well something's wrong because it fails to update some critical system stuff as far as i can tell, because a red triangle appears in my task bar saying critical error files are not up to date or something like that. 

Screen:
[IMG]http://img12.imageshack.us/img12/7671/errn.png[/IMG]


Hope that someone could help.

---

### Post by SkyNet2029 on 2010-08-14
Hi There!
Your sources.list has a spelling error in it...
 
the line that says:
 
[http://ppa.lanchpad.net/kmess-packages/kmess-stabl](http://ppa.lanchpad.net/kmess-packages/kmess-stabl)
 
should read
 
[http://ppa.launchpad.net/kmess-packages/kmess-stable](http://ppa.launchpad.net/kmess-packages/kmess-stable)
 
 
The first line I don't know about as the repo you have listed doesn't appear to be valid...
You need to double check what it is you are trying to fetch and from where.
 
EDIT: I just noticed your user name...
Is that first line supposed to be pointing at a local repository?
If so you will need to ammend it to the correct repo host, not the ppa.

---

### Post by Cha0sBG on 2010-08-14
The only thing i have added there myself is the wine ppa :/
Edited the second line and doesn't give more errors, but first is just ...

---

### Post by sandyd on 2010-08-14
> **Cha0sBG said:**
> The only thing i have added there myself is the wine ppa :/
Edited the second line and doesn't give more errors, but first is just ...
can you post the output of 
```

ls /etc/apt/sources.list.d
```

---

### Post by Cha0sBG on 2010-08-14
```
cat: /etc/apt/sources.list.d: Is a directory
```

if u want to know what is in the folder:

```

/etc/apt/sources.list.d/cha0sbg-ppa-namec-lucid.list
/etc/apt/sources.list.d/cha0sbg-ppa-namec-lucid.list.save
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.save
/etc/apt/sources.list.d/kmess-packages-kmess-stable-lucid.list
/etc/apt/sources.list.d/kmess-packages-kmess-stable-lucid.list.save
/etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list
/etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list.save
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save
```

---

### Post by sandyd on 2010-08-14
> **Cha0sBG said:**
> ```
cat: /etc/apt/sources.list.d: Is a directory
```if u want to know what is in the folder:

```

/etc/apt/sources.list.d/cha0sbg-ppa-namec-lucid.list
/etc/apt/sources.list.d/cha0sbg-ppa-namec-lucid.list.save
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.save
/etc/apt/sources.list.d/kmess-packages-kmess-stable-lucid.list
/etc/apt/sources.list.d/kmess-packages-kmess-stable-lucid.list.save
/etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list
/etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list.save
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save
```
```

sudo rm /etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list[FONT=monospace]
sudo rm [/FONT]/etc/apt/sources.list.d/kmess-packages-kmess-stabl-lucid.list.save
```

---

