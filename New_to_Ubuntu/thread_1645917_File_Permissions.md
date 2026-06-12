---
title: "File Permissions"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Blue Summer on 2010-12-15
My WoW repair program is telling me to change file permissions, i've tried right clicking and allowing it but it seems to revert back, i've heard of chmod but it seems a little complicated.

How would I change the folder /home/rej3kt/.wine/drive_c/Program Files/world of warcraft to be able to read and write?


edit: Just tried this but it's giving me an error:
```
chmod chmod a+rw  /home/rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe
```

error:
```

chmod: cannot access `/home/rej3kt/.wine/drive_c/Program': No such file or directory
chmod: cannot access `Files/World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft/repair.exe': No such file or directory
rej3kt@Rej3kt:~$ chmod a+rw /home/Rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe
chmod: cannot access `/home/Rej3kt/.wine/drive_c/Program': No such file or directory
chmod: cannot access `Files/World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft/repair.exe': No such file or directory

```

so do I have to change the name of the folders to not include spaces?

---

### Post by NCLI on 2010-12-15
> **Blue Summer said:**
> My WoW repair program is telling me to change file permissions, i've tried right clicking and allowing it but it seems to revert back, i've heard of chmod but it seems a little complicated.

How would I change the folder /home/rej3kt/.wine/drive_c/Program Files/world of warcraft to be able to read and write?


edit: Just tried this but it's giving me an error:
```
chmod chmod a+rw  /home/rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe
```

error:
```

chmod: cannot access `/home/rej3kt/.wine/drive_c/Program': No such file or directory
chmod: cannot access `Files/World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft/repair.exe': No such file or directory
rej3kt@Rej3kt:~$ chmod a+rw /home/Rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe
chmod: cannot access `/home/Rej3kt/.wine/drive_c/Program': No such file or directory
chmod: cannot access `Files/World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft/repair.exe': No such file or directory

```

so do I have to change the name of the folders to not include spaces?

Run this:
```
chmod -R u+x '/home/Rej3kt/.wine/drive_c/Program Files/World of Warcraft/*'
```

---

### Post by NIT006.5 on 2010-12-15
> **Blue Summer said:**
> 
so do I have to change the name of the folders to not include spaces?

You need to "escape" the spaces, using one of the methods below:

```

chmod a+rw  /home/rej3kt/.wine/drive_c/Program\ Files/World\ of\ Warcraft/repair.exe

```

That escapes each space by placing a \ before it. OR...

```

chmod a+rw  "/home/rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe"

```

by enclosing the entire path in double quotes.

---

### Post by NCLI on 2010-12-15
> **NIT006.5 said:**
> You need to "escape" the spaces, using one of the methods below:

```

chmod a+rw  /home/rej3kt/.wine/drive_c/Program\ Files/World\ of\ Warcraft/repair.exe

```

That escapes each space by placing a \ before it. OR...

```

chmod a+rw  "/home/rej3kt/.wine/drive_c/Program Files/World of Warcraft/repair.exe"

```

by enclosing the entire path in double quotes.

Single quotes work too ;)

---

### Post by Blue Summer on 2010-12-15
I copied and pasted all 3 of them and none of them worked. I just ended up setting read and write permissions for the whole wine folder I think. Thanks anyways.

The WoW repairer is saying : " Repair is unable to fix your folder permissions. Please change your install path to allow write prvalges and try again."

---

### Post by john77eipe on 2010-12-15
Warcraft worked perfectly for me but it was darn slow...in Ubuntu. So I kept Win 7 just for playing games :)

---

### Post by Blue Summer on 2010-12-15
Haha, I really don't like windows 7 ^_^.

Had it working perfectly then this patch came along and it's only hot fixes and it's messed me up, it's so annoying it's unreal!

---

### Post by NCLI on 2010-12-15
> **Blue Summer said:**
> I copied and pasted all 3 of them and none of them worked. I just ended up setting read and write permissions for the whole wine folder I think. Thanks anyways.

The WoW repairer is saying : " Repair is unable to fix your folder permissions. Please change your install path to allow write prvalges and try again."
Run this, then try again:
```
chmod -R u+rwx '/home/Rej3kt/.wine/drive_c/*'
```
If this doesn't work, it's a Wine bug.

---

