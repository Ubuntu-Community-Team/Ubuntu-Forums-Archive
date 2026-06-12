---
title: "installing graphics driver in ubuntu 10.10"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by shashank bisht on 2010-10-20
i am using ubuntu for the first time and i am facing some problems.
i have installed ubuntu 10.10 and the screen resolution have stuck to 800x600 and graphics are too bad. i have intel 845g chipset, please tell me where to get drivers for ubuntu and how to install them.

---

### Post by ubudog on 2010-10-20
Have you checked in System>Admin>Hardware Drivers?

---

### Post by Mark Phelps on 2010-10-20
I don't believe that Hardware Drivers is going to offer you Intel drivers.  As far as I know, it only offers AMD or Nvidia drivers.

As to the Intel drivers, they are installed by default during system setup but, unfortunately, Intel driver support (as you have found out) is not very good.

---

### Post by SuaSwe on 2010-10-20
If you can't find an easy solution I might suggest trying an older version of the OS from a live environment (USB or CD/DVD) to see if they run OK there? I had major graphics issues upgrading from Jaunty to Karmic back in the day on my Packard Bell; just downgraded right back and it continued to work beautifully. :)

Otherwise, this article is very old but might still hold some value? 
[http://daveshields.wordpress.com/2007/08/21/configuring-intel-845g-video-chipset-on-ubuntu-704-feisty-fawn-desktop/](http://daveshields.wordpress.com/2007/08/21/configuring-intel-845g-video-chipset-on-ubuntu-704-feisty-fawn-desktop/)

---

### Post by ubudog on 2010-10-20
Hmm, didn't know that about Res. Drivers.  Intel is very bad to use with Linux, but like SuaSwe said, downgrading may help.  Sucks, but it may be what you need to do.

---

### Post by shashankbisht on 2010-10-23
hello guys 
when i run ubuntu live from cd it runs fine and the graphics are  awesome and even i can customize screen resolution, so please help me out. Please suggest me where to download the drivers for intel 845g chipset for ubuntu 10.10, send me the link.

---

### Post by Riiznn on 2010-10-24
System>Administration>Drivers

You might be able to find some with that. But, if your like me, you will have to search around for them and download them that way. 

Good luck.

---

### Post by cariboo on 2010-10-24
I don't know where the idea that Intel drivers weren't very good came from,  but I use them on my netbook and media center pc, I have no problem running at 1024X600 on the netbook, and native 1360X768 on a 32" Samsung LCD TV, connected via vga.

I watch DVDs and recorded televisions show at full screen on both with no problems. 

To the op, what type of monitor are you using?

---

### Post by joe2005 on 2010-10-25
I had this problem some time in january when using 10.04 and solved by following the guidance given in this topic.[http://ubuntuforums.org/showthread.php?t=1364460&highlight=UNKNOWN+MONITOR](http://ubuntuforums.org/showthread.php?t=1364460&highlight=UNKNOWN+MONITOR)

---

### Post by ubudog on 2010-10-25
> **cariboo907 said:**
> I don't know where the idea that Intel drivers weren't very good came from,  but I use them on my netbook and media center pc, I have no problem running at 1024X600 on the netbook, and native 1360X768 on a 32" Samsung LCD TV, connected via vga.

I watch DVDs and recorded televisions show at full screen on both with no problems. 

To the op, what type of monitor are you using?

With games though, it is a big hassle to get them working with Intel graphics. 

(eg. [http://dangerdeep.sourceforge.net](http://dangerdeep.sourceforge.net))

---

### Post by ElroyJ on 2011-02-20
Follow instructions on this page [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

---

