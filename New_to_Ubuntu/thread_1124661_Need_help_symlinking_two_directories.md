---
title: "Need help symlinking two directories"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-04-13
I use both Wine and Cedega as each one runs some games better than others... the only issue is alot of my games are installed VIA steam, so instead of having two installs I'd like to create a symlink in my cedega directory that simply points to the steam files in my wine directory.

Here is what I tried doing:

```
ln --symbolic .wine/drive_c/Program\ Files/Steam .cedega/Steam/c_drive/Program\ Files/Steam
``` How ever this simply creates a file called "steam" in my cedega directory, can I use symlink to create a direct link to the .wine files?

~Jeff

---

### Post by moredhel on 2009-04-13
ln -s ~/.wine/drive_c/Program\ Files/Steam ~/.cedega/Steam/drive_c/Program \Files/Steam *should* work.

---

### Post by oobe-feisty on 2009-04-13
moredhel reply should work FYI the reason your link did not work is because the symlink was broken due to the fact it needs the entire path it does not make the link for you even if you are in the same directory as the paths and files you are linking

i.e you are in your home dir 

and you typed 

ln --symbolic .wine/drive_c/Program\ Files/Steam .cedega/Steam/c_drive/Program\ Files/Steam

but it took it in a literal sense and required the full path of 

ln --symbolic /home/someuser/.wine/drive_c/Program\ Files/Steam /home/someuser/.cedega/Steam/c_drive/Program\ Files/Steam

---

### Post by moredhel on 2009-04-13
I would still use ln -s rather than --symbolic, it's quicker ;)

---

### Post by oobe-feisty on 2009-04-13
> **moredhel said:**
> I would still use ln -s rather than --symbolic, it's quicker ;)


indeed i was merely quoting the man

---

