---
title: "C++ programming with Codeblocks IDE"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Nervouswreck on 2009-06-23
I have been writing in C++ on my Windows installation for a while. After installing Ubuntu Jaunty (my third experience with linux, 2nd with Ubuntu, this time to stay) I checked out the Linux version of the Codeblocks IDE. Obviously things like 
```

system ( "pause" );

```
didn't work because of the operating system. Is there a library I can include -- or a package I can install -- that will give me access to those commands? I have dosemu but I like the IDE.

---

### Post by MuH4hA on 2009-06-23
"Those Commands" are system-specific. Therefore something like system("pause") will not work - but it seems you aleready know.

I'm not sure, but I think there is no library or package for Codeblocks, that'll make it possible for you to use those calls.

I think you will have to continue using dosemu, if you want to write DOS Software in Linux. But I would suggest, you stop using those, 'cause 
the programs will only work with DOS/Windows or behave different, when using another system.

Here's a little site, about why you shold not use system("pause"):

[http://www.gidnetwork.com/b-61.html](http://www.gidnetwork.com/b-61.html)

---

### Post by mister_pink on 2009-06-23
If you want to write crossplatform software (which for big projects can be a bit of a nightmare...) you're best off using a toolkit. It can provide a lot of functionality that would be system specific, but the toolkit deals with that so you don't have to.

---

### Post by Nervouswreck on 2009-06-23
Thanks, I knew they were system-specific but was hoping there would be some type of workaround. Currently I need to write DOS console applications for school so I'm kinda stuck.

Mr.Pink, I'm not writing much besides school stuff at the moment, but for future reference (read "i've got a project in the one-of-these-centuries file") which toolkit do you recommend for a Windows/debian-based Linux/Mac OSX project?

---

### Post by MuH4hA on 2009-06-23
Which Toolkit fits your needs depends on the application and your personal preferences. As I do not know, what type of Application you are about to write, I can't recommend a specific Toolkit, but you should be able to find one with google or by posting in this Forum again ;-)


If you - for example - need a GUI in your application, I would recommend using Qt ([http://www.qtsoftware.com/](http://www.qtsoftware.com/)) or GTK+ ([http://www.gtk.org/](http://www.gtk.org/)).

---

### Post by mister_pink on 2009-06-23
I've only really used gtk before, but it does provide a lot of useful tools other than the obvious GUI end to things. I imagine there must be some command line toolkits out there, but I guess most of the time it shouldn't be needed.

---

