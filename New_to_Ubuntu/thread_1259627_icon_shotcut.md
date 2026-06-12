---
title: "icon shotcut"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-06
I was wondering if it's possible to activate the window switcher (not sure if this is the wright word,used to Dutch,it's the application like 3D flip in vista) by clicking an icon instead of clicking a button.If so,how do I put it in the panel?

---

### Post by defacto on 2009-09-06
What's the difference between "button" and "icon" ( in panel ) ?
On the desktop, create a new shortcut, set it's icon, add command & finally, drag-n-drop to your panel.

---

### Post by dzon65 on 2009-09-07
Sure.But how to add a compiz application?How to add for example the cube application to the panel? For now I start this "3D flip"-effect by clicking the F1.How can I add this key binding to the panel? AND,keep it there.All url shortcuts disappear after rebooting,hope this one stays.That is,if it's possible to add that kind of shortcut to the panel.

---

### Post by kerry_s on 2009-09-07
in terminal:
[B]sudo apt-get install xautomation
mkdir ~/bin
gedit ~/bin/3d-flip[/B]

put:
```
#!/bin/sh
xte 'key F1'

```

make it executable:
**chmod +x ~/bin/3d-flip**

now log out & back in

create your launcher & put "**3d-flip**" for the command.

---

### Post by dzon65 on 2009-09-07
I tried but it didn't work.Tried 3D-flip and (in dutch "schuifwisselaar").None worked,file doesn't exist.

---

### Post by Penguin Guy on 2009-09-07
Run [COLOR="Green"]PATH=/home/<username>/bin:$PATH[/COLOR], then try again.

---

### Post by kerry_s on 2009-09-07
then you didn't do it right.

did you install the "xautomation" program?
did you create the "bin" folder?
etc...

it's simple really, just copy & paste.

---

### Post by kerry_s on 2009-09-07
> **Penguin Guy said:**
> Run [COLOR="Green"]PATH=/home/<username>/bin:$PATH[/COLOR], then try again.

~/bin is added to the path if it exists automatically, that's why the log out & back in.

---

### Post by dzon65 on 2009-09-07
Kerry.I think the problem is "3d-flip".The code is probably wright,but not 3-D flip.It's called like that in vista.I couldn't find the word in English.On my pc it's called Schuif wisselaar.In compiz config some applications have english names,others dutch ones.

---

### Post by dzon65 on 2009-09-07
No use,tried several times.xautomation's installed,bin is made and executable but gives same error,"file doesn't exist".

---

### Post by kerry_s on 2009-09-07
the name don't matter the script just runs the F1 key.

i use a similar thing for alt+f4, which is to close programs, cause i'm using maximus & don't want to use window-picker-applet, cause i want a normal taskbar, not the icon type.

---

### Post by dzon65 on 2009-09-08
Don't get it,did exactly the same thing with the same outcome:"file doesn't exist".I had similar problems with some other stuff though.Not far from where I live there's a firm specialized in installing linux.I consider to pay them a visit cause this wubi installed version keeps popping up problems (poor jerky and banding graphics,no standby,no headphone sound[no surround option],freezing a lot,crashing while rhythbox+visualizations,etc.....).Too bad cause this is quite a good machine.I hope these guys can fix these problems cause the way ubuntu is running now,well,my vista is stabler and yes..faster.I really like ubuntu so..fingers crossed.As for this shortcut issue,I'll give it another try but I'm pretty sure the outcome will be the same.But nevertheless,many thanks,J.

---

### Post by dzon65 on 2009-09-08
Say kerry,some good news.Got it to work!Thanks again.

---

