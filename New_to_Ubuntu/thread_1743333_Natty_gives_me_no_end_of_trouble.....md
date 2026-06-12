---
title: "Natty gives me no end of trouble...."
date: 2011-04-29
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-04-29
Now I have to another issue. Not sure how to describe it, so I'll leave a screenshot. As you can see, when I resize the window, The top border disappears! This happened right after playing with ccsm, but reversing my changes does not fix the problem.

Another issue is, after trying some updates I get an error message saying it can't install them because they're coming from an untrusted restricted source. I think it's medibuntu....How can I find out if it is and fix it? As far as I know, I installed medibuntu properly..

Thanks

---

### Post by cariboo on 2011-04-29
From the looks of it, compiz crashed, open a terminal and type:

```
compiz --replace
```

to restart it.

As far as the Medibuntu error is concerned, there may not be a natty repository yet, so you may have to change it back to maverick in your /etc/apt/sources.list

---

### Post by ivanovnegro on 2011-04-30
Medibuntu is available for Natty but the servers seem to be down lateley.
Just wait a little bit.

Look at my sig.

---

### Post by skyzthelimit230 on 2011-04-30
> **cariboo907 said:**
> From the looks of it, compiz crashed, open a terminal and type:

```
compiz --replace
```

to restart it.

As far as the Medibuntu error is concerned, there may not be a natty repository yet, so you may have to change it back to maverick in your /etc/apt/sources.list

Hey, I reset compiz, but it just made the issue worse. Now the global menu dosen't even appear :| 

Is there a way I can reset Unity?

---

### Post by sikander3786 on 2011-04-30
Try resetting Compiz and/or Unity as mentioned here.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Hope it helps.

---

### Post by skyzthelimit230 on 2011-05-02
Thanks everyone. Resetting Compiz or Natty dosen't fix the issue, so I just created a new user and that fixed the issue. Seems the desktop cube effect kills Unity....

---

### Post by pritam_par on 2011-08-06
Check this post to enable cube with unity.
[http://ubuntuforums.org/showthread.php?p=11124888#post11124888](http://ubuntuforums.org/showthread.php?p=11124888#post11124888)

and to get the title bar back
In the compiz manager select the option
move window and window decoration.

---

