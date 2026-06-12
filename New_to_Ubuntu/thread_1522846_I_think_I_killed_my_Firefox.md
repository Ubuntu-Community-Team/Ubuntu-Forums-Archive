---
title: "I think I killed my Firefox"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by MoeThirteen on 2010-07-02
I was trying to d-load firefox 3.6.6 because i had this weired namoroka pre release thing before.

I tried everything i could to install and now my /usr/share/firefox folder only has a defaults folder in it. i'm assuming thats bad because i believe i saw more in there before.

i'm really stuck. i hope someone can help me.

---

### Post by col48 on 2010-07-02
I'm on Firefox 3.0.19 and only have 'defaults' in /usr/share/firefox. In 'defaults' there is only a folder 'pref' and in there is only a javascript file apturl.js

Doesn't solve your problem but maybe this is not the symptom to be worried about.

---

### Post by MoeThirteen on 2010-07-02
I also get a error that says 'Failed to execute child process "/usr/lib/firefox/firefox" (No such file or directory).' when i try to launch and firefox is not present in the network menu of the application menu on the toolbar at the top.

i had heard of a fix that to make a change that made it say "/usr/lib/firefox/firefox" needless to say it didn't work.

i should have included the error.

---

### Post by -humanaut- on 2010-07-02
Try this

sudo apt-get purge firefox && sudo apt-get install firefox

Make sure you disable the daily-builds PPA first if you have them installed thats why your getting Namoroko or whatever its called.

---

### Post by Kixtosh on 2010-07-02
Have you tried using the Synaptic Package Manager to select Firefox for reinstallation?
 
Also, as a different consideration, if you are using Xubuntu for a lightweight distribution (as I am), you might also want to consider switching to Chromium as well. It's significantly faster on my old machines.

---

### Post by -humanaut- on 2010-07-02
As recommend a different browser for Xubuntu is a good idea however I recommend giving Midori a try its super-fast passes acid3 100/100 webkit based and designed for Xfce I heard the version in Lucid Lynx is super stable as well.

---

### Post by MoeThirteen on 2010-07-02
-humanaut- and myself got the tag-team fix. With his code and myself undoing everything i 'fixed'.

In addition i'll explain that i don't have an old computer, but i used to. i not too long ago bought a new computer and am sticking with Xubuntu until i'm ready to fall into the loving arms of an LTS release, my first time using an LTS also.

Thank you to everyone that posted help!

---

### Post by Kixtosh on 2010-07-03
Good job, MoeThirteen! 
 
As far as using a LTS version of Xubuntu (or any other flavour of Ubuntu): for the simple computing/browsing needs that I use on my old machines, Lucid Lynx 10.04 (which is a LTS release, of course) has been much simpler to install and use than 9.10 so far, despite the more demanding "minimum system requirements", and I intend to stick with it! If anything, performance was faster, and even more so after I added the LXDE desktop package (and Chromium instead of Firefox helped somewhat as well). By the time the next LTS version of Xubuntu is released, it'll be time to retire these old dogs for good, any maybe by then I'll have switched over my newer laptop to some form of Linux O.S. as well.
 
Best of luck.
 
*P.S. Don't forget to mark the thread as "solved"!*

---

### Post by ddecator on 2010-07-03
Where did you get Firefox from? Did you use a PPA? Did you download the source and try to run it manually?

---

