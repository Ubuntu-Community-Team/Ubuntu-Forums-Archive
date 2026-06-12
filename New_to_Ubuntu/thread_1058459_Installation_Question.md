---
title: "Installation Question"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by schmi284 on 2009-02-02
I have had hardy heron installed on my computer and that has been working fine for me.  I recently installed version 8.10 of ubuntu on my machine and after I enter my username and password it will go to a blank orange screen.  The mouse cursor is visible but I cannot do anything and it will load no further.  Does anyone know what I can do to fix this or what I did wrong?

---

### Post by yellowaeroplane on 2009-02-02
Keep it nice and easy to start.

Boot into Recovery Mode from the main (GRUB) boot list. First do the "fsck" option... probably won't fix your problem but it's good practice. After that completes go to "repair x server" and follow the dialogs. If that doesn't get you up and running then we'll have to do some dirty work.

---

### Post by diablo75 on 2009-02-02
Do you happen to know what kind of video card you have?

---

### Post by channerhewitt on 2009-02-03
After the installation, why is it the desktop has no icon? I don't know how to configure it..

---

### Post by schmi284 on 2009-02-03
I just have the video card that came with the machine.  It is a basic intel card, nothing special.  I did the "fsck" option and the "repair x server" option.  I am still having the same problem.

---

### Post by Crafty Kisses on 2009-02-03
What are your full system specs?

---

### Post by o0Rusty0o on 2009-02-03
You most likely have an Intel graphics card does is incompatible with Compiz Fusion. Exactly what happened with me (I have Intel 82845 Graphics Controller) and I cannot get Compiz to run. Try this fix from [Andrew's Blog: Blank screen on startup after installing Ubuntu 8.10? Try this fix]("http://andrewtheart.blogspot.com/2008/12/blank-screen-on-startup-after.html"). This worked for me and will most likely work for you also. [This will remove Compiz Fusion, allowing you to boot into Ubuntu]

---

### Post by schmi284 on 2009-02-03
I used o0Rusty0o's fix and that got me booted up.  Now I have another problem.  I have no sound.  I tried running the tests and there was nothing.  I have this sound card in my machine: [http://www.bestbuy.com/site/olspage.jsp?skuId=7698404&type=product&id=1138084673510](http://www.bestbuy.com/site/olspage.jsp?skuId=7698404&type=product&id=1138084673510)

---

### Post by mikechant on 2009-02-03
Afraid I can't help you with your sound problem but you might get more useful replies if you post it as a seperate question with the sound card brand/model in the title - e.g. someone who's had the same problem is more likely to notice it.

---

### Post by carml on 2009-02-03
Did you try to run a hardware test by System->Administration->Hardware test?

---

