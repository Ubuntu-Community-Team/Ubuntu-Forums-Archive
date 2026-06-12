---
title: "Where is my /usr/bin ?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-04-29
Hi guys,

I am trying to point the "mailto" command in Firefox to Thunderbird. My /usr/bin is nowhere to be found -gulp- . I have unhidden the files in my /home folder. Can someone help me?

---

### Post by CatKiller on 2009-04-29
Your /usr/bin is at /usr/bin. Your Home folder is at /home/<username>.

You need to go up a couple of levels, to /, then usr, then bin.

---

### Post by Tobine on 2009-04-29
When in your home folder go 'Up' twice to Filesystem. /usr will be in there

---

### Post by Monotoko on 2009-04-29
It wont be in your home folder, your home is located at /home/(username here)

Think of it this way, its C:\users\(username here) on Windows Vista, your after "C:\" except in linux its differant.

All files are located at root, root is defined by one character: /

If you want to open the file manager at root, its pretty simple to do, but if you want to edit anything, you will need to be the root account.

To open the file manager in the root account run the following in your terminal (Applications -> Accessorys -> Terminal) (Be careful with this, deleting a wrong file or folder can screw up your entire system, its always advised to use the normal account unless you need to do something with the system and know exactly what your doing!!)

```
sudo nautilus /
```

---

### Post by tahitiwibble on 2009-04-29
> **Tobine said:**
> When in your home folder go 'Up' twice to Filesystem. /usr will be in there

Oh wow! simple as that! Thanks for that, I was thinking "Oh oh, here we go again".

Thanks again.

---

### Post by Didius Falco on 2009-04-29
You can do that without messing about in your system files.

In Firefox, open the Tools menu, go to Preferences, the Applications tab and scroll down to MailTo. There will be a drop-down box that you can set to "Use Thunderbird - default".

---

### Post by tahitiwibble on 2009-04-29
Monotoko, thank you for the extra info. Much appreciated!

---

### Post by tahitiwibble on 2009-04-29
> **Didius Falco said:**
> You can do that without messing about in your system files.

In Firefox, open the Tools menu, go to Preferences, the Applications tab and scroll down to MailTo. There will be a drop-down box that you can set to "Use Thunderbird - default".

Even simpler! Thank you so much.

---

### Post by Didius Falco on 2009-04-29
Glad to help.

---

