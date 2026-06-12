---
title: "Chaning the default locations?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-12-11
Hello all,

I'm running Intrepid x64 and Windows XP x64, with a separate hard drive for storing my personal files, which I share between the two OSes. 

For obvious reasons, I didn't want to give Windows access to my home folder, so that's on another partition altogether. The thing is, it's really annoying to have to navigate to data/* to open or save anything when Ubuntu already defaults to /home/paulo/*. Is there a way to bind some of the folders in my home folder so that when I go to ~/Documents I'm actually going to /data/Documents, etc, without effectively turning my data partition into my home partition? Or is there a way to do that, but keep all my configuration files elsewhere so that Windows won't screw them up?

This problem might seem like a minor inconvenience but just try doing all this clicking routine over 50 times per day when Ubuntu is clearly telling me that it knows where the files should be... except it ends up not being helpful at all since I keep my files elsewhere.

---

### Post by wizard10000 on 2008-12-11
> **GepettoBR said:**
> Hello all,

I'm running Intrepid x64 and Windows XP x64, with a separate hard drive for storing my personal files, which I share between the two OSes. 

For obvious reasons, I didn't want to give Windows access to my home folder, so that's on another partition altogether. The thing is, it's really annoying to have to navigate to data/* to open or save anything when Ubuntu already defaults to /home/paulo/*. Is there a way to bind some of the folders in my home folder so that when I go to ~/Documents I'm actually going to /data/Documents, etc, without effectively turning my data partition into my home partition? Or is there a way to do that, but keep all my configuration files elsewhere so that Windows won't screw them up?

This problem might seem like a minor inconvenience but just try doing all this clicking routine over 50 times per day when Ubuntu is clearly telling me that it knows where the files should be... except it ends up not being helpful at all since I keep my files elsewhere.

Why not just stick a symlink to /data/Documents in your home directory?

Can't think of a reason this wouldn't work but you might wanna test it first - try this:

```
mv /home/paulo/Documents /home/paulo/Documents-old

ln -s /data/Documents /home/paulo/Documents
```

Hope this helps -

---

### Post by sisco311 on 2008-12-11
or add this line to the fstab:
```
/data/Documents /home/paulo/Documents auto bind
```

---

### Post by Sarmacid on 2008-12-11
You can drag the folder to the lower left frame of nautilus and it will be 1 click away from any folder.

---

### Post by scorp123 on 2008-12-11
> **GepettoBR said:**
> The thing is, it's really annoying to have to navigate to data/* to open or save anything when Ubuntu already defaults to /home/paulo/*. Please read this:

[http://ubuntuforums.org/showthread.php?p=6333743#post6333743](http://ubuntuforums.org/showthread.php?p=6333743#post6333743)

---

