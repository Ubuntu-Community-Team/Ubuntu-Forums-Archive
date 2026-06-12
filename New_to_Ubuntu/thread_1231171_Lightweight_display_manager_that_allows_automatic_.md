---
title: "Lightweight display manager that allows automatic login?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by user 123 on 2009-08-04
What is the most lightweight display manager that will allow automatic-login?

---

### Post by keplerspeed on 2009-08-04
Im sure sonething like fluxbox would do the job. Or XFCE.

---

### Post by user 123 on 2009-08-04
> **keplerspeed said:**
> Im sure sonething like fluxbox would do the job. Or XFCE.

Sorry if i was unclear in the first post but i'm looking for a display manager such as GDM, KDM, XDM etc. not a window manager.

---

### Post by wizard10000 on 2009-08-04
> **user 123 said:**
> What is the most lightweight login manager that will allow automatic-login?

Probably entrance but I'm guessing.  Don't know whether entrance or XDM is lighter.

[http://xcomputerman.com/pages/entrance.html](http://xcomputerman.com/pages/entrance.html)

---

### Post by user 123 on 2009-08-04
> **wizard10000 said:**
> Probably entrance but I'm guessing.  Don't know whether entrance or XDM is lighter.

[http://xcomputerman.com/pages/entrance.html](http://xcomputerman.com/pages/entrance.html)

I'm not sure but i think i heard XDM doesn't support automatic login?

---

### Post by wizard10000 on 2009-08-04
> **user 123 said:**
> I'm not sure but i think i heard XDM doesn't support automatic login?

Don't know.  Never used it  :)

---

### Post by kpkeerthi on 2009-08-04
If you want to autologin, why use a display manager? [http://ubuntuforums.org/showthread.php?t=903042]("http://ubuntuforums.org/showthread.php?t=903042") (google should get you more)

---

### Post by user 123 on 2009-08-04
will try this, thanks!

---

### Post by user 123 on 2009-08-04
In the above link I'm not sure what this means:

> and on .bashrc in my home dir i have:

pgrep X &>/dev/null; [ $? = 1 ] && startx

to start the x server.

What does this mean/how would I do it?

---

### Post by kpkeerthi on 2009-08-04
That will autostart 'X' immediately after login. But before you do that, have you checked if autologin worked?

---

### Post by user 123 on 2009-08-04
The autologin works. I know what it does per se I just don't what it means by 'having that on .bashrc in my home directory' or how to do it.

---

### Post by lykwydchykyn on 2009-08-04
Install slim and see this:

[http://www.linuxmint.com/wiki/index.php/Fluxbox_Auto_login_with_Slim](http://www.linuxmint.com/wiki/index.php/Fluxbox_Auto_login_with_Slim)

---

### Post by lykwydchykyn on 2009-08-04
> **user 123 said:**
> The autologin works. I know what it does per se I just don't what it means by 'having that on .bashrc in my home directory' or how to do it.

In your home directory there is a file called ".bashrc".  The prepended dot makes it hidden, but if you open it in some kind of text editor it should have lots of stuff in it.

Paste those commands at the end of it.

---

### Post by kpkeerthi on 2009-08-04
> **user 123 said:**
> The autologin works. I know what it does per se I just don't what it means by 'having that on .bashrc in my home directory' or how to do it.

Great. You just have add that line to ~/.bashrc (I would add it to ~/.bash_login, though)

But before that verify if the **startx** command brings up your desktop environment. Then, 
```

gedit ~/.bash_login
```
* Do this from your desktop environment

Add the line:
```
pgrep X &>/dev/null; [ $? = 1 ] && startx

```
Save and Exit gedit. Reboot.

---

### Post by user 123 on 2009-08-04
I've done this however when I shutdown i now get the error:

Unable to perform Shutdown

org.freedesktop.hal.power-management.shutdown no<-- (action, result)

---

### Post by user 123 on 2009-08-04
> **user 123 said:**
> I've done this however when I shutdown i now get the error:

Unable to perform Shutdown

org.freedesktop.hal.power-management.shutdown no<-- (action, result)

No worries, i managed to solve with the solution here:

[http://www.nowhere.dk/articles/xfce-unable-to-perform-shutdown](http://www.nowhere.dk/articles/xfce-unable-to-perform-shutdown)

---

### Post by lampar on 2009-12-04
There is a program called NODM (No display manager). In ubuntu you can find the package nodm.

---

### Post by tweaksource on 2010-01-22
Definitely slim is the way to go.

---

### Post by arsya on 2011-02-03
If what you need is autologin, then I suggest to use nodm. Install it via ubuntu repository and you're good to go.

I wrote about it in my blog:
[http://murzal-arsya.blogspot.com/2010/03/automatic-display-manager-login-using.html](http://murzal-arsya.blogspot.com/2010/03/automatic-display-manager-login-using.html)

---

