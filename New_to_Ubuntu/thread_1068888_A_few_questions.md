---
title: "A few questions"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Shozzking on 2009-02-13
1. when I start up my laptop then i get an option to choose between Ubuntu, Ubuntu recovery mode, another Ubuntu option and Vista, it gives me 10 seconds to choose and if i dont then it boots Ubuntu. Is there any way to change this so that it gives me 30 seconds and boots Vista if I dont choose otherwise?

2. Is there anywhere that I can go to download more themes?

Thanks

---

### Post by drs305 on 2009-02-13
You can change the boot delay by directly editing /boot/grub/menu.lst or via a gui app called startupmanager. I recommend startupmanager since you can tweak a lot of grub's settings without manually editing anything.

To install:
```
sudo apt-get install startupmanager
```

To run:
startupmanager
or 
System, Administration, Startup-Manager. Boot options, change value in "Timeout".

To edit manually (use *gksudo* rather than *sudo* when using graphical apps such as *gedit*):
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst

```
Find the line and change the value, and save the file:
```
timeout    10

```

For themes, look here:
[http://www.gnome-look.org/]("http://www.gnome-look.org/")

---

### Post by vikramaditya on 2009-02-13
Go here...
[http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/)

---

### Post by vikramaditya on 2009-02-13
> **drs305 said:**
> I recommend startupmanager since you can tweak a lot of grub's settings without manually editing anything.
Thanks, I didn't know about that util!

---

### Post by drs305 on 2009-02-13
> **vikramaditya said:**
> Thanks, I didn't know about that util!

I forgot to mention there is a *startupmanager* tutorial link in my signature...

---

### Post by vikramaditya on 2009-02-13
> **drs305 said:**
> I forgot to mention there is a *startupmanager* tutorial link in my signature...
So I see, thanks . . . aww, I don't need no stinkin' tutorial - I'll just blunder on in there and see if I can get a kernel panic going! :)

---

### Post by Shozzking on 2009-02-13
nvm, i found it. how do i delete posts?

---

### Post by howefield on 2009-02-13
Open up a terminal from the Application > Accessories menu.

Enter your password when it asks after you have typed the command.

---

### Post by egalvan on 2009-02-13
> **Shozzking said:**
> nvm, i found it. how do i delete posts?

One does not delete posts. (moderators excepted)
They are left here for others to read, 
and learn from.

That is one of the strengths of forums such as this one.

And welcome to the club! 

ErnestG

:popcorn:

---

