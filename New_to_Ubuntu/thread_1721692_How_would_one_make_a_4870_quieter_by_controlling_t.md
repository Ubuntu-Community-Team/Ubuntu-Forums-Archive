---
title: "How would one make a 4870 quieter by controlling the fan?"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by watarbatar on 2011-04-04
Hello all. this is my first time using ubuntu and so far things are not going so badly :D. However my graphic's cards immense fan is definitely sullying the experience. I searched through some previous topics dealing with a similar issue and found that a user did indeed find a solution using the terminal in this thread right here 

[http://ubuntuforums.org/showthread.php?t=1493880](http://ubuntuforums.org/showthread.php?t=1493880).

The user used the code 

aticonfig --pplib-cmd "set fanspeed 0 31"

to set the fan speed lowe.

I already installed the latest catalyst drivers and when entering that into the terminal, I get this error message

"No layout section was found in the file: '/etc/X11/xorg.conf'. Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again."

I'm not really sure what that means or how to fix it, so I really appreciate all the help .

Thanks

---

### Post by sandyd on 2011-04-04
> **watarbatar said:**
> Hello all. this is my first time using ubuntu and so far things are not going so badly :D. However my graphic's cards immense fan is definitely sullying the experience. I searched through some previous topics dealing with a similar issue and found that a user did indeed find a solution using the terminal in this thread right here 

[http://ubuntuforums.org/showthread.php?t=1493880](http://ubuntuforums.org/showthread.php?t=1493880).

The user used the code 

aticonfig --pplib-cmd "set fanspeed 0 31"

to set the fan speed lowe.

I already installed the latest catalyst drivers and when entering that into the terminal, I get this error message

"No layout section was found in the file: '/etc/X11/xorg.conf'. Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again."

I'm not really sure what that means or how to fix it, so I really appreciate all the help .

Thanks
run
```

sudo aticonfig --initial
```
first.

---

### Post by watarbatar on 2011-04-04
Oh wow, that worked. I can believe it was that simple! Thank you for the solution.

---

