---
title: "playing avi permission error"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by dimitriv on 2009-04-03
hi

I can play video's fine. If my second account attempts to play the same avi it fails giving the following error:

'Could not open location; you might not have permission to open the file' 

I have placed the file in the second account's home directory or desktop (neither work). I can't see any settings which would enable/disable the playing of such files for this account, any ideas?

Thank you

---

### Post by SunnyRabbiera on 2009-04-03
are the files DRM'ed?

---

### Post by MrWES on 2009-04-03
> **dimitriv said:**
> hi

I can play video's fine. If my second account attempts to play the same avi it fails giving the following error:

'Could not open location; you might not have permission to open the file' 

I have placed the file in the second account's home directory or desktop (neither work). I can't see any settings which would enable/disable the playing of such files for this account, any ideas?

Thank you


Open a terminal and navigate to the directory where the file is located and issue an ls -al command, post the results here.

Bill

---

### Post by dimitriv on 2009-04-03
SunnyRabbiera, no, pretty sure not & I can watch the video

Bill,
the machine's offline so i'm posting from another what i got running ls -al

total  321964
drwxr-xr-x 2 ac2 ac2 4096 date time .
drwxr-xr-x 29 ac2 ac2 4096 date time ..
-rw------- 1 root root size date time file.avi

following a sugggestion in another post about using gksudo nautilus to transfer files i tried copying another avi. I then ran ls -al and the new file looked like this
-rw------- 1 ac1 ac1 size date time 2ndfile.avi

ie. permissions were associated with my primary account not root.

Trying to play the second video file through ac2 generates the same error.

thanks

---

### Post by MrWES on 2009-04-04
> **dimitriv said:**
> SunnyRabbiera, no, pretty sure not & I can watch the video

Bill,
the machine's offline so i'm posting from another what i got running ls -al

total  321964
drwxr-xr-x 2 ac2 ac2 4096 date time .
drwxr-xr-x 29 ac2 ac2 4096 date time ..
-rw------- 1 root root size date time file.avi

following a sugggestion in another post about using gksudo nautilus to transfer files i tried copying another avi. I then ran ls -al and the new file looked like this
-rw------- 1 ac1 ac1 size date time 2ndfile.avi

ie. permissions were associated with my primary account not root.

Trying to play the second video file through ac2 generates the same error.

thanks

The avi file are read/write by the ONLY the owner root. Open a terminal; Applications | Accessories | Terminal and navigate to the directory where the avi file is:

```
sudo chown ac1:ac1 2ndfile.avi
```
and
```
sudo chmod 755 2ndfile.avi
```


you can use what ever chmod perms suits your needs. Remember

read=4
write=2
execute=1

Bill

---

