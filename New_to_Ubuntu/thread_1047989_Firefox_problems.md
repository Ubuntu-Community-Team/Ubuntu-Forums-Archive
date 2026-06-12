---
title: "Firefox problems"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by scheibo on 2009-01-23
Hey, this question is going to sound very dumb, but for some reason it's causing me a lot of grief.

As of about 20 minutes ago, whenever I run Firefox, it immediately hides my panels (top and bottom, ie. system clock, menu bar..etc). It also does not have one of the window manager bars with the maximize, minimize and close buttons. It is **not** running in full screen mode, and I've tried restarting my system, but no luck.

Any idea how I've somehow magically screwed up firefox?

---

### Post by Crafty Kisses on 2009-01-23
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows"

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

### Post by scheibo on 2009-01-23
Thank you very much. Pressing F11 twice, minimizing and then resizing worked! If it seems to only be a temporary fix I'll check out the compiz fusion methond. Thanks a lot.

---

### Post by Crafty Kisses on 2009-01-23
The one that actually worked for me the best, is pressing F11 twice, and resizing the window and closing Firefox, then reopening it, that works perfectly.

---

