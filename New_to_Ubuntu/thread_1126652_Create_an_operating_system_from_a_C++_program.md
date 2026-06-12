---
title: "Create an operating system from a C++ program"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by eeeandrew on 2009-04-15
hi guys,

Heres an interesting problem for you. I'm looking to find out more about this but I may not actually do it. If this is very difficult to do, I don't want anyone to go to a lot of trouble trying to write an answer/how-to for me.

Basically, at the moment I'm working on a project at university. We're coding a cipher program in C++. We've been told that we can add to the brief and use more complex ideas to get a lot of extra credit. I've been looking into the idea of compiling a custom kernel using the code. My idea is to hand in an operating system which runs the project and only the project if that makes sense. So I'd like to boot my laptop up choose "cipher project" or whatever as an operating system then boot straight into the GUI and start the encryption process.

Is this possible without too much legwork?

Thanks in advance,
Andrew

---

### Post by OutOfReach on 2009-04-15
I don't think you need to go down all the way to Kernel level just to do this. You can just make your program run when the GUI (GNOME I'm assuming) starts.

---

### Post by eeeandrew on 2009-04-15
of course but the idea was to get the extra credit for the extra work.

Thanks,
Andrew

---

### Post by damis648 on 2009-04-15
> **OutOfReach said:**
> I don't think you need to go down all the way to Kernel level just to do this. You can just make your program run when the GUI (GNOME I'm assuming) starts.

You could just add a separate session to GDM that starts the program instead of GNOME, and set it as default and make it auto-login.

---

### Post by eeeandrew on 2009-04-15
I like that suggestion...how would I do that?

Thanks,
Andrew

---

### Post by LowSky on 2009-04-15
Here is what I would do. Use a Linux version that has no GUI, say Arch Linux. Build your program to work from the console. Have the program automatically start up when you enter the user name and password and when you exit the application it also logs out as that user. Also create your own user name to actually use the system in full GUI mode if you like as well.

---

