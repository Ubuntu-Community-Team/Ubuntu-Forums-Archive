---
title: "running .exe with wine"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-06-18
I just don't get it, I installed wine, then I go to browse c drive, then click on the downloaded .exe file and it just wants to extract it, then if there is an exe file extracted, I click and i get an error message.  I am totally new to ubuntu, so there is probably some incredibly long and complicated terminal operation that I have to do in order to get it to work like there was in installing java, if so, im a little dumb so if someone could kinda walk me through it, I would really appreciate it

---

### Post by bodhi.zazen on 2010-06-18
What are you trying to do ? What application are you trying to run in wine?

Linux is not a drop in replacement for windows, and honestly wine is not easy to use. To run complex applications with wine one needs to understand a fair amount of how BOTH Linux and Windows work.

You are best off looking up your application on winhq, if the application works you will find detailed instructions:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by gandaran on 2010-06-18
> **beelzebufo said:**
> I just don't get it, I installed wine, then I go to browse c drive, then click on the downloaded .exe file and it just wants to extract it, then if there is an exe file extracted, I click and i get an error message.  I am totally new to ubuntu, so there is probably some incredibly long and complicated terminal operation that I have to do in order to get it to work like there was in installing java, if so, im a little dumb so if someone could kinda walk me through it, I would really appreciate it
no it ain't any complicated terminal operation (only if you choose to go that way like you did for java),just right click the .exe file on you desktop and choose from the drop-down menu load with windows wine, simple! it will install just like in windows.
but find out first if the application can run in wine without problems, very few windows applications can run in wine.

---

### Post by bodhi.zazen on 2010-06-18
> **gandaran said:**
> no it ain't any complicated terminal operation (only if you choose to go that way like you did for java),just right click the .exe file on you desktop and choose from the drop-down menu load with windows wine, simple! it will install just like in windows.
but find out first if the application can run in wine without problems, very few windows applications can run in wine.

Depends on the complexity of the .exe

With simple apps, such as utorrent or almost anything from portableapps.com what you say is true.

But with more complex applications you will need to a far amount of command-line-foo

---

### Post by Locke_99GS on 2010-06-18
You could also try looking for a linux alternative to the software you're attempting to run via Wine.

---

### Post by J V on 2010-06-18
+1 for open source alternative.

Now as for wine, it's not easy to use... At all...

I have to say you should use playonlinux, it just makes tasks that not only take forever to find a guide for, but forever to execute, last 10 seconds...

The Lucid version crashes every time you try to install a custom application, but just xkill that and the next window pops up.

---

