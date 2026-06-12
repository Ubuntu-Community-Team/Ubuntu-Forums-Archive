---
title: "Is there a way to start Tasque hidden?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-09-12
Is there a way to start Tasque hidden?

---

### Post by freak42 on 2009-09-12
what do you mean by hidden?

if you want to start a task on the commandline in the background, you can append an ampersand ( & ) after the command.


e.g.:

firefox &

your command line will return immediately.. if you close your console by typing 'exit' firefox will keep running (if you close by clicking the windows close button it will close as well I think)

---

### Post by slughappy1 on 2009-09-12
I mean I want the program to start, but not show up. So the tray icon will be there but the program will start sort of minimized. Other programs can do it. For example, gnome-do can start hidden or start up and show on the screen.

Edit:
Start it in the background.

---

### Post by sharm on 2009-09-13
You can start tasque with the --quiet argument if you are using 0.1.8 or later.

---

### Post by Shpongle on 2009-09-13
you could try all tray , i havnt used it but apparently you can minimize any application to the system tray , so maybe you can start it up in the tray like rhythmbox , see [http://kmassada.wordpress.com/2009/05/18/all-tray/](http://kmassada.wordpress.com/2009/05/18/all-tray/)

---

### Post by sharm on 2009-09-13
> **DillByrne said:**
> you could try all tray , i havnt used it but apparently you can minimize any application to the system tray , so maybe you can start it up in the tray like rhythmbox , see [http://kmassada.wordpress.com/2009/05/18/all-tray/](http://kmassada.wordpress.com/2009/05/18/all-tray/)

This is not necessary, Tasque already appears in the notification area (aka tray), and if you start with --quiet it solves the original poster's problem.

---

### Post by slughappy1 on 2009-09-13
Thank you. That was exactly what I was looking for. I couldn't find out about --quiet anywhere, including the man page. Although, I might just be blind

---

### Post by sharm on 2009-09-14
> **slughappy1 said:**
> Thank you. That was exactly what I was looking for. I couldn't find out about --quiet anywhere, including the man page. Although, I might just be blind

No, this is entirely our fault.  We have an update for the man page to include this, but we haven't made a new release with it yet.

Glad it's working for you!

---

