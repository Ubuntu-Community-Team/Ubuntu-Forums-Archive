---
title: "Can't run Synaptic or Update manager"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by brentavius on 2010-06-18
This problem may be more widespread, but the two instances I've noticed are Synaptic Package Manager and the Update Manager.  For either, when I try to open it, it gives prompts me for my password to do administrative tasks.  I enter said password, the window disappears, and that's it.  The program does not open.

This just sort of started.  I can't pinpoint it to any particular event.  Frustrating.  Any ideas?

Also, I don't know if this is part of the same problem or a different problem, but UFRaw won't open my .CR2 files.  Again, this is a piece of software I've been using for awhile, but suddenly it doesn't recognize the format.  This is why I want to go into Synaptic - to check the installation of UFRaw.  But I can't get in there. . . .

---

### Post by drs305 on 2010-06-18
Try opening synaptic via the terminal to see if any error messages are produced. If so, copy them here. You can also try running the APT update command to see what happens when the repositories are updated:

Open a terminal (Applications, Accessories, Terminal).

Run the first command to open Synaptic. If that doesn't provide any clues, close it and try the second:
```
gksu synaptic &
sudo apt-get update
```

---

### Post by wilee-nilee on 2010-06-18
> **brentavius said:**
> This problem may be more widespread, but the two instances I've noticed are Synaptic Package Manager and the Update Manager.  For either, when I try to open it, it gives prompts me for my password to do administrative tasks.  I enter said password, the window disappears, and that's it.  The program does not open.

This just sort of started.  I can't pinpoint it to any particular event.  Frustrating.  Any ideas?

Also, I don't know if this is part of the same problem or a different problem, but UFRaw won't open my .CR2 files.  Again, this is a piece of software I've been using for awhile, but suddenly it doesn't recognize the format.  This is why I want to go into Synaptic - to check the installation of UFRaw.  But I can't get in there. . . .

I have noticed that if you type the password really fast it is easy to make a mistake and since Lucid I don't get a try again prompt. Here are two general commands from the terminal that can clear stuff up.
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by jmszr on 2010-06-18
brentavius,

If the above solutions do not fix your problem, try running (copy and paste) this in your terminal:

```
sudo rm /var/cache/apt/*.bin
```

---

### Post by brentavius on 2010-06-18
Thanks for your help, everyone.  It turns out that (as usual) it was the simplest of things:  Dummy (that's me) was entering the wrong password.  Your posts were helpful, though.  I learned from them, and they also helped me discover what I was doing after the Terminal told me I was entering the wrong password.

Sorry for crying, "Wolf!"  and thanks for your help.  Now if I can just get UFRaw to work. . . .

---

### Post by wilee-nilee on 2010-06-18
> **brentavius said:**
> Thanks for your help, everyone.  It turns out that (as usual) it was the simplest of things:  Dummy (that's me) was entering the wrong password.  Your posts were helpful, though.  I learned from them, and they also helped me discover what I was doing after the Terminal told me I was entering the wrong password.

Sorry for crying, "Wolf!"  and thanks for your help.  Now if I can just get UFRaw to work. . . .

Welcome to the Doh club we are quite full, but there is always room for more.;)

---

