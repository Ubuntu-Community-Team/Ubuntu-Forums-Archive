---
title: "/tmp no longer used for media?"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-03-23
Hello,

I used to grab videos and music from websites very easily because they were downloaded and stored locally in the /tmp folder. This method was outlined in this post:
[http://ubuntuforums.org/showthread.php?t=547848](http://ubuntuforums.org/showthread.php?t=547848)

I tried to do this recently, and it seems that there is no longer a .flash file created for the temporary storage of media. Anyone know where it went?

Thanks,
Kurt

---

### Post by Script Warlock on 2011-03-24
due to some copyright issues, you may use clipgrab or minitube.

---

### Post by mcduck on 2011-03-24
> **jkurtisr32 said:**
> Hello,

I used to grab videos and music from websites very easily because they were downloaded and stored locally in the /tmp folder. This method was outlined in this post:
[http://ubuntuforums.org/showthread.php?t=547848](http://ubuntuforums.org/showthread.php?t=547848)

I tried to do this recently, and it seems that there is no longer a .flash file created for the temporary storage of media. Anyone know where it went?

Thanks,
Kurt

The latest Flash plugin versions cache videos in the same place where your web browser keeps it's cache for all other files.

If you use Firefox, the location is ~/.mozilla/firefox/*yourprofile*/Cache/

---

### Post by jkurtisr32 on 2011-03-24
> **mcduck said:**
> The latest Flash plugin versions cache videos in the same place where your web browser keeps it's cache for all other files.

If you use Firefox, the location is ~/.mozilla/firefox/*yourprofile*/Cache/

You're right. This helped a lot. Thanks very much.

-Kurt

---

