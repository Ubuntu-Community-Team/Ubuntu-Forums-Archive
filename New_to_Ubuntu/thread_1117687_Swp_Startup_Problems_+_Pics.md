---
title: "Swp Startup Problems + Pics"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Sugz on 2009-04-06
Ok folks, this has been a problem for a while. 
Whenever i try to startup Ubuntu (7.10)
it always falters and i get these error messages. 

(Press Ctrl+Alt+F1)
[[IMG]http://img11.imageshack.us/img11/8083/dsc00587uxc.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=dsc00587uxc.jpg)

[[IMG]http://img11.imageshack.us/img11/8083/dsc00587uxc.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=dsc00587uxc.jpg)

[[IMG]http://img21.imageshack.us/img21/1165/dsc00586d.th.jpg[/IMG]](http://img21.imageshack.us/my.php?image=dsc00586d.jpg)


The image that started it all

[[IMG]http://img11.imageshack.us/img11/4710/dsc00588i.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=dsc00588i.jpg)

**UPDATE** Now if i logout of the main session (Ctrl+Alt+F7) it keeps on starting up an odd version of Ubuntu, but i cannot shutdown or restart :mad:

if i try to shutdown it says 
shutdown: time expired

reboot does nothing

And now my keyboard is acting strangely

This is weird any help at all?

---

### Post by Bölvaður on 2009-04-06
this sounds very alien.
I cannot read any error messages from the photos you took. But the errors might be visible if you turn splashscreen off and just has the output of what the computer is doing on startup (in grub ress E on the boot option you want to edit, delete "quiet" and splash and press enter).

But using 7.10 is a little bit retro, the support has ended quite a while ago havent it?
For me gusty (7.10) was a very good release, but I would recommend you to install 9.04 when it comes out. There are still too much errors in the beta to jump right ahead, but it is very promising.

---

### Post by Sugz on 2009-04-06
My use of ubuntu is now very limited as this problems seems to have crippled my system.

I can read the error messages fine, just click the Thumbnails to see a larger version. 

I would have upgraded by now, but i can't because of this error plus i just don't trust linux at updating yet. ;)

---

### Post by LowSky on 2009-04-06
I'm going to say that you should really update to 8.04 as 7.10 ends its shelf life in about 3 weeks. 8.04 has a much longer shelf life (another 2 years).

A reinstall will fix all current issues.

But remember that these issues all start when you install or mess with installtions that you know little about. befor eyou enter any command try to look it up and see if it has any effects to your system, sure many command or programs installations go just fine, but knowing how a program might effect your system is a good idea befor running them.

Also have you tried using an older kernel to start your system from GRUB?

---

### Post by Sugz on 2009-04-06
The reasons why i am reluctant to upgrade is another story
I have just tried to use the recovery mode kernel Here is a pic of what happens

[[IMG]http://img11.imageshack.us/img11/6895/dsc00589vlv.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=dsc00589vlv.jpg)

---

### Post by Hospadar on 2009-04-06
What happens when you Ctrl-D at the recovery mode prompt?

If you just boot up normal, then log in textually, the do "sudo /etc/init.d/gdm start" to start up a gnome session (which is what normally happens when you log in) what happens?

---

### Post by Bölvaður on 2009-04-07
> **LowSky said:**
> Also have you tried using an older kernel to start your system from GRUB?

What happened is probably that there was an kernel update (the kernel has driver modules for your hardware) and there is a need to either reinstall the driver, which is probably the graphical card, or what is easier, just boot up the old kernel.

How to :
When you turn on the computer you either see grub (boot menu) or it is "hidden", if it is hidden you need to press esc when it asks if you want to see it.
When you are in grub try an older kernel, normally the older kernels are further down the menu. You can tell how old they are by the version number.

I hope this will solve the problem.

---

### Post by anewguy on 2009-04-07
Just FYI, for me at least, when I follow the links to your images, they are very small and not clickable - I've tried clicking and nothing happens.  Hence, they are unreadable.

Dave

---

