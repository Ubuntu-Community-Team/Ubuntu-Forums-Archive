---
title: "Help with Firefox please"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by jluda on 2009-02-05
My open firefox window takes the whole screen, there are no close minimize or maximize buttons just the flower looking icon where its supposed to be. I can not see any of my regular desktop menus or minimized programs. I also am sure its not in full screen mode because ive taken it on and off to see if that would fix it and it didnt. please help

---

### Post by RomeReactor on 2009-02-05
Hi. can you please post a screenshot of the problem? It does sound like the fullscreen problem that's been going around for a while.

---

### Post by Doug11 on 2009-02-05
> **jluda said:**
> My open firefox window takes the whole screen, there are no close minimize or maximize buttons just the flower looking icon where its supposed to be. I can not see any of my regular desktop menus or minimized programs. I also am sure its not in full screen mode because ive taken it on and off to see if that would fix it and it didnt. please helpTry press your F11 once or twice.

---

### Post by jluda on 2009-02-05
alrite so i got the menus back but now all my programs are still missing like the close minimize and maximize icons ill get a screenshot one minute

---

### Post by jluda on 2009-02-05
here is where the icons are supposed to be on firefox

---

### Post by RomeReactor on 2009-02-05
Did you try [these steps]("http://ubuntuforums.org/showpost.php?p=6488032&postcount=6")? make sure you unmaximize the window and resize it before closing Firefox.

---

### Post by jluda on 2009-02-05
yea i just tried that except i dont have the maximize minimize i can see the minimized programs at the bottom now so i right clicked and maximized minimized that way but i am still missing those buttons to close maximize and minimize on all my programs

---

### Post by RomeReactor on 2009-02-05
> **jluda said:**
> yea i just tried that except i dont have the maximize minimize i can see the minimized programs at the bottom now so i right clicked and maximized minimized that way but i am still missing those buttons to close maximize and minimize on all my programs

So the problem affects all your other applications? Do you have Desktop Effects enabled? If so, turn them off and see if the problem persists.

---

### Post by jluda on 2009-02-05
its still not working

---

### Post by Guille Damke on 2009-02-05
Can you move/resize it? Try pressing "left_alt + space". Use your scroll arrows plus enter when using move or resize. Try moving it down, the bar may be just hidden behind the panel, then resize it.

---

### Post by RomeReactor on 2009-02-05
Have you changed the default Human theme recently? Have you tried other themes? What happens when you run this?
```
metacity --replace
```

---

### Post by jluda on 2009-02-05
i got it some how when i went to system>preferences>Appearance and for the "Visual Effect" none were selected i fixed it thanks for all the help

---

### Post by Crafty Kisses on 2009-02-05
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any

```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```

---

