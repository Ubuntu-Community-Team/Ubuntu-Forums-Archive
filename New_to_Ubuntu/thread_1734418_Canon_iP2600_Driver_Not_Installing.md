---
title: "Canon iP2600 Driver Not Installing"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Inhopeless on 2011-04-20
I've seen other threads and they suggest downloading:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

and

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

I've tried installing both, but the first one depends on the second one.

After trying to install the second one (in Software Centre), it does about 90%, then fails with "package did not install". 

It asks me to repair packages, which I accepted, however, after this, it still won't install the package.

Is there any other way I can install the printer? 

Thanks,

I'm running 11.04 on an Advent Firefly FP9004

---

### Post by mynameisnotbob on 2011-04-20
> **Inhopeless said:**
> I've seen other threads and they suggest downloading:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

and

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

I've tried installing both, but the first one depends on the second one.

After trying to install the second one (in Software Centre), it does about 90%, then fails with "package did not install". 

It asks me to repair packages, which I accepted, however, after this, it still won't install the package.

Is there any other way I can install the printer? 

Thanks,

I'm running 11.04 on an Advent Firefly FP9004

The problem could very well be that you are running 11.04. The package may not have been updated for it yet. Wait until the official version comes out, then see if that fixes your problem.

---

### Post by Bob_Dole on 2011-05-30
The problem exists in 10.04 as well, it's a change in one of the libraries (or a change of the name of the library, can't remember)from 9.10 to 10.04. There's user patched .deb's floating around somewhere. Ah, here they are: [http://ubuntuforums.org/showthread.php?t=1492636](http://ubuntuforums.org/showthread.php?t=1492636)
However, if you so choose to use the prepacked debs there, the file permissions are wrong and it will complain in natty, and you also have to chown a file to root before it'll actually work after you install it.
Ah, this library that got changed was libcupsys2. that's what it was when this driver actually just worked.

---

### Post by lol768 on 2011-06-13
Sorry to dig up an old thread, but you can also use a "dummy" transitional package rather than editing the deb file.

See [http://packages.debian.org/lenny/all/libcupsys2/download](http://packages.debian.org/lenny/all/libcupsys2/download) to download this -- then you should be able to install the driver.

For a step by step guide you may want to take a look at this post: [http://technostripe.com/getting-the-canon-pixma-ip2600-to-work-on-ubuntu/](http://technostripe.com/getting-the-canon-pixma-ip2600-to-work-on-ubuntu/) 

It should work with your printer.

---

### Post by Elfy on 2011-10-16
Works in 11.10

---

### Post by desertpig on 2012-02-03
i have Xubuntu 11.10 and have followed the previous steps for installing the canon ip2600 driver and it still doesnt work.  the printer says "Rendering Completed" under status but doesnt print.  i entered these commands successfully in the terminal: sudo add-apt-repository ppa:michael-gruz/canon sudo apt-get update sudo apt-get install cnijfilter-ip2600series  any other ideas?

---

