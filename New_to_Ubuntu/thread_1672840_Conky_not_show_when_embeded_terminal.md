---
title: "Conky not show when embeded terminal"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by adeee on 2011-01-21
Guys i just install conky. here it is working fine.
[ATTACH]181651[/ATTACH]
And also just embaded terminal by getting help of this [Thread.]("http://ubuntuforums.org/showthread.php?t=202249")
[ATTACH]181652[/ATTACH]

But as you can see both are shown in different work spaces. terminal in first and conky in second.
so my question is can i give width and hight to embeded terminal 700*725?
So that i can see conky in first workspace as well as terminal too.

---

### Post by Random_Dude on 2011-01-21
I had a terminal and conky arranged in a similar way and it didn't cause any problems.
Maybe your terminal window is just too big, have you tried reducing the terminal window size?

Cheers :cool:

---

### Post by adeee on 2011-01-21
> **Random_Dude said:**
> 
Maybe your terminal window is just too big, have you tried reducing the terminal window size?


Nope this is my default terminal window size. when i click on terminal it appears in this size.
[ATTACH]181658[/ATTACH]

---

### Post by Random_Dude on 2011-01-21
After I checking the link you provided, I saw this:

> 
3) Paste the following configuration (press Ctrl^X to save and exit):
     Code:
     (if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
) 
Have you tried using a smaller geometry in the configuration? Like this:

```
(geometry "200x100")
```

---

### Post by adeee on 2011-01-21
Thank you random dude. its help me. i was changed it to my screen resolution 1024*786. now i change it to require width and hight.. again thanxs

---

### Post by Random_Dude on 2011-01-22
No problem.
Don't forget to mark the thread as [solved]. ;)

Cheers :cool:

---

