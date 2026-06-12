---
title: "jwgkvsq.vmx (conflicker) in recycling bin"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by cma37 on 2010-09-27
Hello- 
I am not too smooth with computers so bear with me:
I read around the forums a little bit and figured out that this virus probably is harmless on ubuntu.  I am, however, a little concerned that this file is just sitting in my recycling bin and that I cannot delete it.  Many people seemed to advise that wine not be used as root to make sure there is never any issue, but I do not know how to do this.  I changed the properties of the file to give it no default program with which to open- perhaps a meaningless gesture but it was just about the only thing I was allowed to do.  I also tried to comb through my wine system32 file for suspicious .dlls- some sites advised filtering by size? Anyhow, I know where I got the virus (never lending my sister my usb key again) and was just looking for any explanations. 
Thanks!

Chris

---

### Post by Old *ix Geek on 2010-09-28
> **cma37 said:**
> I am, however, a little concerned that this file is just sitting in my recycling bin and that I cannot delete it.WHY can't you delete it? How did you try--from the command line, a file manager, or what? What did you try--if at a command line, what command(s) did you use? Etc.
> Many people seemed to advise that wine not be used as root to make sure there is never any issue, but I do not know how to do this.Unless you were logged in as, or used **su** to change to, root prior to running wine, you weren't running it as root. And if you WERE logged in as, or **su**ed to root...well, you shouldn't have unless you're REALLY sure you know what you're doing.

---

### Post by cma37 on 2010-09-28
I finally removed it with sudo rm- the odd thing is I couldn't do so with gksudo nautilus-  I guess all this wouldn't be so mysterious if I knew more about linux commands- your response pushed me to browse around some of the great instructional threads here, where I should probably stay until I know my *** from a hole in the ground.
Thanks!

---

### Post by Old *ix Geek on 2010-09-28
Great! I'm glad the problem is solved. (You might want to mark the thread as solved.)

I can't stress strongly enough how powerful the *nix command line is. You can do amazing things there! Take some time to learn some basic commands, and next thing you know you'll want to learn more. :)

---

