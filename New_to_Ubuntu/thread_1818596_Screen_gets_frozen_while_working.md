---
title: "Screen gets frozen while working"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by techno.geek on 2011-08-05
I have been facing this problem for quite some time now. While I am running some applications on Ubuntu 11.04 my screen suddenly freezes/hangs. 
Now there have been two cases::
1. GUI is frozen however u can hover the mouse but mouse clicks won't work. However u can start and close the applications using keyboard shortcuts.
2. This one is a very serious problem. Complete screen is frozen no mouse hovering, no keyboards shortcuts nothing. I have to restart everytime. Real problem comes when I am writing the code and it hangs before I could even save it.

Now what I have been trying for some time is to use Alt+Ctrl+F* then go into terminal mode and identify the process that is making it to hang/freeze and then kill it but with no luck. Can anyone help me in this method or any other method to unfreeze the screen??

Thanks!

---

### Post by Aitashan on 2011-08-05
you could try removing unity 3d and try installing unity 2d instead and do the updates

---

### Post by techno.geek on 2011-08-05
I am working on Ubuntu Classic.. no unity

---

### Post by Aitashan on 2011-08-05
have you done the updates

---

### Post by Aitashan on 2011-08-05
switch to unity 2d

---

### Post by techno.geek on 2011-08-05
Yup done all the updates..

---

### Post by Aitashan on 2011-08-05
```
sudo apt-get install unity-2d
```

---

### Post by techno.geek on 2011-08-05
Same result with unity 2d. btw Thanks!

Problem is solved. Actually there was some process that was causing it to hang.

For those who are having the same problem. What I did is :-
Press Alt+Ctrl+F* login as root then see all the processes that were running using 
```
 ps -A 
```
```
 top 
```
then here in my case it was this specific process xyz so i did 
# pidof xyz
now kill it using # kill (pid)

```
 exit 
```

Press Alt+Ctrl+F7

---

