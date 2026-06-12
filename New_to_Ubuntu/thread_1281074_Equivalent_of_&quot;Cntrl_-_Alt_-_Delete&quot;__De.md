---
title: "Equivalent of &quot;Cntrl - Alt - Delete&quot; ??? Dell Mini10V"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by franklin_m on 2009-10-02
Newbie here...

Have had Firefox hang up every once in a while. I'll close it, but when I attempt to open it again, it tells me that an instance is already running and that I need to close the process.

In Windows (ugh), I'd hit <cntrl><alt><delete> to bring up a list of processes, then kill it.

Two questions: How do identify hung processes in Ubuntu (notebook remix 9.04) and then how do I kill them?

Thanks,
Frank

---

### Post by BorgHunter on 2009-10-02
Yeah, I've had Firefox do that to me a couple times before too. I've no idea how to identify hung processes unless they're eating up a lot of CPU while being hung, but opening the terminal and entering "pkill firefox" should kill that lingering Firefox instance that didn't die properly.

---

### Post by kerry_s on 2009-10-02
in ubuntu just run "killall firefox" & you should be good.

---

### Post by aktiwers on 2009-10-02
[https://answers.launchpad.net/ubuntu/+question/19234](https://answers.launchpad.net/ubuntu/+question/19234)
look in 3. post.

Or add "force quit"  to your panel.

Or open terminal and type: 
```
xkill
```

and click the app you want to close.

---

### Post by boogey on 2009-10-02
save "Force Quit" to the panel

edit: too late... sorry for the double post

---

### Post by the.phantom on 2009-10-02
if it is just firefox, try waiting about 5 to 10 sec after you close it before you start it again, that is what i do on firefox
another thing to try if it is still displayed ( or any other hung program)

right click on the task-bar and select add to panel. select  "force quit"

then just click it when you get a hang  ;-D

---

### Post by franklin_m on 2009-10-03
Thanks for the help...but that leads me to another question...how does one add something to the control panel?

Frank

---

### Post by 3rdalbum on 2009-10-03
> **franklin_m said:**
> Thanks for the help...but that leads me to another question...how does one add something to the control panel?

The panel, not the control panel. Right-click on either your top panel or your bottom panel, choose "Add to Panel...", click the Force Quit item in the list and then click the Add button.

---

### Post by NoaHall on 2009-10-03
Right click -> Add to panel

---

### Post by Paqman on 2009-10-03
> **franklin_m said:**
> ...how does one add something to the control panel?


Right click > Add to panel. Right click on existing panel applet to remove or move them.

Lots of good stuff to be had.

---

