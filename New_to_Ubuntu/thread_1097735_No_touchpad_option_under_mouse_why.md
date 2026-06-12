---
title: "No touchpad option under mouse why?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-16
why isn't my touchpad there? i've installed gsynaptics etc. as the guide on the page says. Why isn't my touchpad there i need to disable it and also in my xorg file it's not even there. What's going on with this OS?

---

### Post by stoogiebuncho on 2009-03-16
What happens when you try to open gsynaptics?

---

### Post by stoogiebuncho on 2009-03-16
I've been looking at a few of your other threads, and thought I would update this with a little more information.

I'm guessing you're using Ubuntu 8.10, is that correct?  8.10 does not use xorg.conf nearly as much as 8.04 did.  That's why your touchpad is not listed there.

If you have installed gsynaptics (and it sounds like you have), open it by pressing Alt+F2 and entering
```
gsynaptics
```
If you get an error message, post it back here.

If you don't get an error message, you should be able to change whatever you need to.

---

### Post by 133794m3r on 2009-03-16
```
The command "gsynaptics" failed to run:

Failed to execute child process "gsynaptics" (No such file or directory)
```

i installed the .deb b/c for some reason it's not in the universe and now i get this

also i'm on xubuntu 8.1 :/ which is supposedly just like ubuntu but i'm finding it to be almost nothing like it :/ at all

---

### Post by stoogiebuncho on 2009-03-16
Yeah, I just did all of this on my mom's laptop which is Xubuntu 8.10.  I also use Xubuntu on my laptop and Ubuntu on my desktop and there are certainly differences.  Xubuntu has a lot less options built in to the GUI so you end up doing more command line work, I find.  But I find it's worth it for the speed.

Anyway, it sounds like there's something wrong with your install of gsynaptics.  I would recommend a reinstall.

I know you said you weren't able to find it in synaptic package manager, but I just installed it from there last week, so maybe you could double check to be sure you typed it correctly and everything.

I'd start with this:
```
sudo apt-get remove gsynaptics
```

Then:
```
sudo apt-get install gsynaptics
```

I believe you can also reinstall from the .deb file you downloaded if you wish to do it that way instead.

(or try clicking this [link]("apt:gsynaptics"))

---

### Post by 133794m3r on 2009-03-16
ok that worked but i for some reason don't have that erm what's it called translucent selection rectangle? as in i can't select and highlight multiple files from the desktop.

---

### Post by stoogiebuncho on 2009-03-16
I can't remember if I have the selection rectangle on my Xubuntu machine or not...

You can always select multiple files by holding Ctrl.

---

### Post by 133794m3r on 2009-03-16
well i don't really need the rectangle but it was nice to have one :/ so i could select files easily. Also if you could check out my other thread to explain that for me :/

---

