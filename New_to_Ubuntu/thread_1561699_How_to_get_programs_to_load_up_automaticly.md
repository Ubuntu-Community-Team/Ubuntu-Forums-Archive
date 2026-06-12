---
title: "How to get programs to load up automaticly?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by 74mtondreau on 2010-08-26
Hi, I'm running Ubuntu 10.04 on my desktop computer and i'm trying to find a way to get programs such as empathy to load up automaticly as i turn the computer on?

Thanks!

---

### Post by akoskm on 2010-08-26
> **74mtondreau said:**
> Hi, I'm running Ubuntu 10.04 on my desktop computer and i'm trying to find a way to get programs such as empathy to load up automaticly as i turn the computer on?

Thanks!

Hi!
You can configure it under:
System > Preferences > Startup Applications.
Hope this help.

---

### Post by 74mtondreau on 2010-08-26
> **akoskm said:**
> Hi!
You can configure it under:
System > Preferences > Startup Applications.
Hope this help.

Thanks for the help but when i go to "add" what do I type into the command line?

---

### Post by akoskm on 2010-08-26
> **74mtondreau said:**
> Thanks for the help but when i go to "add" what do I type into the command line?

The correct patch to the applications executable, in case of empathy:
```

/usr/bin/empathy

```.
To easily find the patch for other applications type the following command in Terminal:
```

locate <application> | grep bin

```, replace the <application> with the applications name. Example:
```

akoskm@akoskm-laptop:~$ locate skype | grep bin
/usr/bin/skype
/usr/bin/skype-wrapper

```.

edit: the output of locate is to large so I added the **grep bin** to shrink the results (now it lists the patches including "bin" - probably executable files).

---

### Post by oldsoundguy on 2010-08-26
Just remember that the more you have programs "loading automatically", the more "windows like" (read that as SLOW) loading will become.
(In Windows you have to use msconfig to tell programs NOT to load vs Linux where you make the choice!)

IF I use a program a LOT. I just put the launch icon in the panel on Gnome.  Makes for a blazingly fast boot up!!

---

