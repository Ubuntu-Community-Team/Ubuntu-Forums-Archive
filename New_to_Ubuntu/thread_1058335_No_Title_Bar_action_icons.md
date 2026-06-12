---
title: "No Title Bar action icons ??"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Drakkor on 2009-02-02
Why is there no minimize,restore,and close buttons on the title bar ??
Thanks

---

### Post by Crafty Kisses on 2009-02-02
> **Drakkor said:**
> Why is there no minimize,restore,and close buttons on the title bar ??
Thanks

On Firefox, or every program?

---

### Post by Drakkor on 2009-02-02
Seems to be isolated to FF, the title bar is just blank,with not even a title !

---

### Post by Crafty Kisses on 2009-02-02
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```

Once you've done that close out CCSM, then open CCSM back up again, then change that to:
```
any
```

Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

### Post by ModelM on 2009-02-02
If you are running compiz, try turning it off.

---

### Post by Drakkor on 2009-02-02
Thanks, Codename , I did the window decoration thing , and now at least it works, but seems  to go in and out depending on where the cursor is. 
Oh well :)

---

### Post by Crafty Kisses on 2009-02-02
If you press F11 twice and resize your Firefox window, that fixes it, it only really happens when Firefox crashes, not sure if you have tried that yet.

---

### Post by Drakkor on 2009-02-03
It's  fixed good enough  for me, thanks ! :p

---

### Post by Crafty Kisses on 2009-02-03
I'm glad I could help Drakkor!

---

### Post by Drakkor on 2009-02-03
Too bad I can't give you a  thanks, but the thread tools seem  to be  locked

---

### Post by Crafty Kisses on 2009-02-03
Haha, it hasn't worked, they removed that feature I think due to server issues.

---

### Post by Drakkor on 2009-02-03
I guess  if it works for you, but   come on 6.06,Dapper Dan? ,lol :p

---

### Post by Crafty Kisses on 2009-02-03
Haha Dapper Dan! Nice! I still like Dapper, the most solid release I think! :)

---

### Post by Drakkor on 2009-02-03
Ubuntu, I'm lovin' it,lol :D

---

