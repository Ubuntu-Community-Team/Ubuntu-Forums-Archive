---
title: "Graphgics problem"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by The-IRS on 2009-03-09
Hi all.
I installed an updete through the update manager and restarted my computer.
After I restarted the highest resolution I could get was 800x600. Any ideas on how to fix it?
Card is an MX 4400

---

### Post by The-IRS on 2009-03-09
please help

---

### Post by PurposeOfReason on 2009-03-09
What got updated? And post your /etc/X11/xorg.conf.

---

### Post by The-IRS on 2009-03-09
I'm not exactly sure what got updated and it says permission denied to /etc/X11/xorg.conf

---

### Post by PurposeOfReason on 2009-03-09
> **The-IRS said:**
> I'm not exactly sure what got updated and it says permission denied to /etc/X11/xorg.conf
You need root permission for that file. In a terminal, type

sudo cat /etc/X11/xorg.conf

This will give you root permision and post the contents of the file in the terminal for you to copy paste. You could also use sudo gedit which will use the gedit program with root permissions, just make sure that you do not edit the file.

---

### Post by Miljet on 2009-03-09
There is no need to use sudo with the cat command since it only displays the contents of files and makes no change to them.

---

### Post by Razmear on 2009-03-09
I had the same problem with the Nvidia GeForce MX 440, which I'm guessing is the same card your using. 
After a week I finally surrendered and spent the $40 at NewEgg for a GE6200 and life was good. 
If you are using the Nvidia Settings app in the system menu, then expect it to hose your monitor section of your xorg.conf file. Every time I would change it it would set the sync freqs to 497982345.0 instead of 50hz. The 96.x version of the Nvidia tool is crap, but if you are using a MX 440 it's the only version you can use. 
If you search the forums for MX 440 you'll find a lot of hard luck stories. Sorry I don't have any better advice for you other than to consider saving some stress and gray hair and upgrade the video card to a supported version. I'd recommend 6000 series or higher if you are sticking with Nvidia. 

eb

---

### Post by The-IRS on 2009-03-13
I got a GTX 260 now

---

