---
title: "Is there any documentation for the 'Search Files &amp; Folders' function in the launcher?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by skitter on 2011-07-19
I'm trying to understand what is being searched when I use this function.  I don't want to get too far off topic, but an example of what I'm doing might clarify my question. I want to take another shot at getting 3D acceleration to work on my machine that has a Sandy Bridge chipset, and thought I'd do some testing first. I understand that there are some utillites from Mesa for testing 3D. I've gone to both 'Applications' and 'Files and Folders' and tried searching for mesa as well as glxgears. Both of these return 'Your search did not return any files' or 'Your search did not match any applications.'  I know that glxgears is on the system because it will launch from the a terminal, so I'd like to understand why I can't find it in the launcher.

Thanks in advance.

---

### Post by raja.genupula on 2011-07-19
i am giving the solution upto i understand  

if you wanna check your application folder where it is then do this 
```

which application_name
```
in terminal

---

### Post by jfbooth on 2011-07-19
> **skitter said:**
> I know that glxgears is on the system because it will launch from the a terminal, so I'd like to understand why I can't find it in the launcher.

Thanks in advance.

Not sure what you mean by 'launcher' .. are you speaking of CATFISH?

In any case, in terminal, do:

```
sudo updatedb
locate glxgears
```

and it should tell you where glxgears is.

---

### Post by skitter on 2011-07-19
Thanks for the locate and which commands, they help.  That said, I would still like to understand how the GUI searches for files. 

> Not sure what you mean by 'launcher'

I'm referring to the thing along the left hand side of the screen that appears when the mouse is at the far left of the screen (in Natty).  The home folder is at the top, and trash is at the bottom.  I thought that was called the launcher, but now suspect I may not be using the correct terminology.

---

### Post by raja.genupula on 2011-07-20
i am glad that you have find your solution and dont forget to mark the thread as solved by clicking at thread tools.  please

---

