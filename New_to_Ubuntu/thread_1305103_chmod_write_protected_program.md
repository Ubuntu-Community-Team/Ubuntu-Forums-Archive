---
title: "chmod write protected program"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by rickoic on 2009-10-29
I used wget to get a program and when I try and make it runable with 'chmod +x fah6' it tells me that the action isn't allowed. If I try and remove the program it asks about removing write protection, so I'm assuming the program is write protected.
 
How can I at least temporially remove the write protection so to make program runnable?
 
Tks
Rick

---

### Post by dvlchd3 on 2009-10-29
Where did you store the file?

Does ```
sudo chmod a+x fah6
``` work?

Can you give us the results of:
```
ls -sail | grep fah6
```

---

### Post by rickoic on 2009-10-29
The chmod a+x fah6 worked just fine.
 
afraid this is after the change
 
264094 1080 -rwxr -xr -x 1 root root 1103664 2009-07 02 10:00 fah6
 
Got the program running and it's starting to fold.
 
Tks
Rick

---

