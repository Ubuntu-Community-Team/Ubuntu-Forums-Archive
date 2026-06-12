---
title: "Edit sources.list file in Ubuntu Server. Using terminal?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Swerve1000 on 2010-02-22
Hi,

I have just installed Ubuntu 9.10 Server Edition and would like to add some repositories to the sources.list file.

But being the server edition, there is no GUI.

How can I edit the file?

I did use vi once, but it was not a fun experience.

In gnome I would normally enter "gedit sources.list" and gedit would fire up.

Is there a easier text editor I could use? 

Thanks for any advice!

---

### Post by dmaxel on 2010-02-22
I personally like to use nano instead. Just use ```
sudo nano /etc/apt/sources.list
```

---

### Post by wojox on 2010-02-22
> **dmaxel said:**
> I personally like to use nano instead. Just use ```
nano /etc/apt/sources.list
```

+1 and Ctrl+O to save and Ctrl+X to exit.

---

### Post by Swerve1000 on 2010-02-22
Oh thanks. 

nano fired straight up!

and thanks for the shortcut tips, hopefully it's a little more intuitive than vi 

:)

---

### Post by dmaxel on 2010-02-22
Although save and exit as the main shortcuts you'll be concerned with, there are a list of usable shortcuts at the bottom of the screen when nano is fired up. These shortcuts not only help save, exit, etc., but navigate around the file too.

---

