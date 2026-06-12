---
title: "[SOLVED] How to rename files to time/date"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Jab0rnal on 2008-12-04
Hello,

I have an application that creates a file in a folder every five minutes. The problem is the application overwrites this file each time. I can get the application to run a command every five minutes as well.

So what I'm after is a command that i can enter that will rename a specific file name to the current date and time (to keep it unique). I can then schedule that command to run to change the file name before the file is overwritten.


Many thanks for you help.
Jab0rnal

P.S I guess the filename doesn't have to be date and time it just has to be unique, so renaming it incrementally would also work.

---

### Post by nixforme on 2008-12-04
Can you post the code here?

---

### Post by __Ryan__ on 2008-12-04
try this:

```
touch $(date +%h_%d_%H_%M_%S)
```

This will create a file with Month_Day_Hour_Minute_Second. Swap the touch command for whatever you are using.

Good Luck

---

### Post by Idefix82 on 2008-12-04
> **Jab0rnal said:**
> 
So what I'm after is a command that i can enter that will rename a specific file name to the current date and time (to keep it unique). I can then schedule that command to run to change the file name before the file is overwritten.


```
mv myfile $(date +%H_%M_%S)
```
will rename the file 'myfile' into the current time of the day inthe format 'hour_minute_second'. Type in
```
man date
```
to see further formatting options.

---

### Post by Jab0rnal on 2008-12-04
Thank you very much Idefix82. that works nicely after I've played around with it.

```

mv /home/Jab/MyDownloads/webcam/file.jpg /home/Jab/MyDownloads/Webcam/renamed/$(date +%H_%M_%S).jpg
```

This simply renames it to another folder instead of my home folder.

However, and i don't know why, it is only renaming to the time. For example the file is renaming to "18_54_54.jpg" with no date expression before.

Any ideas?

---

### Post by Idefix82 on 2008-12-04
> **Jab0rnal said:**
> 
However, and i don't know why, it is only renaming to the time. For example the file is renaming to "18_54_54.jpg" with no date expression before.

Yes, that was just an example. That was why I gave you a reference to the manual pages of the date command, so you could adjust the formatting and the output of it. For example, if you want the full date and the time you can do
```
mv /home/Jab/MyDownloads/webcam/file.jpg /home/Jab/MyDownloads/Webcam/renamed/$(date +%F_%H_%M_%S).jpg
```

---

### Post by Jab0rnal on 2008-12-04
Thanks again,

Thats my problem solved.

Cheers,
Jab0rnal

---

