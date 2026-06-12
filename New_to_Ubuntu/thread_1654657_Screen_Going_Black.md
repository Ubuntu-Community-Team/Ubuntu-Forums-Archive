---
title: "Screen Going Black?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Bunnies on 2010-12-28
My screen will sometimes turn black and disallow any alterations or usage of the laptop. Sound will cut off and I'm forced to turn it off by the button.

I guess it's freezing? What is causing it and what can I do to solve it?

---

### Post by cariboo on 2010-12-28
Does it go completely black, or can you still see the desktop, you may be able to get to a console by pressing Ctrl-Alt-F1, you can then type:

```
top
```

to see what application is using all the resources, it should be at the top of the list. You can try killing the application using the PID, it will be on the far left:

```
sudo kill 1449 
```

---

### Post by Bunnies on 2010-12-28
> **cariboo907 said:**
> Does it go completely black, or can you still see the desktop, you may be able to get to a console by pressing Ctrl-Alt-F1, you can then type:

```
top
```to see what application is using all the resources, it should be at the top of the list. You can try killing the application using the PID, it will be on the far left:

```
sudo kill 1449 
```


I can't see the desktop when it does this, no. Would these fixes still work?

---

