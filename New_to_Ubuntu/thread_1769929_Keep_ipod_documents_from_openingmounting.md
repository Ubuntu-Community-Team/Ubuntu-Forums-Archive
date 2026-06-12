---
title: "Keep ipod documents from opening/mounting?"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by chromatica86 on 2011-05-28
I'm using ubuntu 11.04 and whenever I plug in my ipod touch, it mounts as "ipod" and a seperate "ipod documents" which opens a folder automatically.
To me this is very annoying, cause I have to close the folder every time. 
I just made the switch from 10.10 for the second time. Please help me from reverting back again.:p

---

### Post by mishathegoat on 2011-05-31
Heya. You can keep things from auto-mounting by modifying your fstab file.

Here's what I would do:

**One:**

Plug in your iTouch and wait for the unwanted directory to automatically open.

**Two:**

Open your File Manager and navigate to /media/

**Three:**

Look for the name of the iPod Documents folder. Easy as just opening /media/ and seeing what's there. If you see a directory called, "iPod_Documents" or similar then that's the name you need to write down. It's important that you write this down *exactly* as you see it. Remember, linux is case sensitive.

For now, let's just say it's called "iPod_Documents" (though I'm not sure exactly what it's called, be sure to find for yourself!)

**Four:**
Open your fstab file. This configuration file manages how devices/file-systems are mounted. In the Terminal use:

```
sudo gedit /etc/fstab
```

**Five:**
Add the following line to the end of your fstab file:
```
LABEL=iPod_Documents /media/iPod_Documents auto rw,suid,dev,exec,**noauto**,nouser,async 0 0
```


Now after your next restart, it should now no longer automatically mount the iPod Documents partition. Normally would not use LABEL with fstab, but instead use UUID. However this was the most "user-friendly" way I could think of.

---

