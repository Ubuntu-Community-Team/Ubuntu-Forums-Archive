---
title: "Automated Deletion Of Files On Boot"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by ryan_wilson on 2009-01-17
Hi,
I moved from windows 2000 to Ubuntu, so far the transition has been quite good. I mainly use my laptop for development work. While working on source code i make temp backups of all the code i'm working on if i am unsure if i will be able to revert back to my old code using good old Crtl + Z. Now i know this is bad practice but its gotten to be a habbit. On my windows 2000 system i had a small batch file that would clean my tempBackups folder so i always have a clean area to start off with in my startup folder (meaning it would execute on boot). This for me was really convienint. I was wondering how i would achieve this on ubuntu. The folder i am wanting to clean is /home/Ryan/tempBackups/
So basically what i am asking is how to delete all the files in this folder when ubuntu starts up.
Thanks beforehand,
-Ryan

---

### Post by northern lights on 2009-01-17
Navigate to "System > Preferences > Sessions" and under the "Startup Programs" tab choose "+ Add". In the command box type```
rm -rf ~/tempBackups/*
```Save.

Now /home/Ryan/tempBackups/ will be emptied at every system start.

---

### Post by sdennie on 2009-01-17
Another option would be to make your temp folder be a symlink to /tmp.  That will assure that the files don't persist across a reboot.

```

rmdir ~/tempBackups
ln -s /tmp ~/tempBackups

```

---

### Post by ryan_wilson on 2009-01-19
Thanks,
You's guys are awesome :D
-Ryan

---

### Post by ryan_wilson on 2009-01-19
hmm just a thought, does this also delete "sudo" protected files?

---

