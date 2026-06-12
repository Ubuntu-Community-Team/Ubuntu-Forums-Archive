---
title: "installing a game with wine (.mdf)"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by ktulu19 on 2009-07-07
i have a .mdf and a .mds file (prefer not to burn to a disc, but i'll do whatever i need to). I've never installed a game using wine so any help would be appreciated. 

thanks!

---

### Post by llamabr on 2009-07-07
Wine is so rarely the correct solution.  What's the game.  Have you looked for a native application?

Look at the game on winehq, which usually pretty honestly gives you a report of how well it will run.  Don't be surprised if the answer is 'not very well'.

---

### Post by ktulu19 on 2009-07-07
the game is Fallout 1. It says on the DB that it works perfectly, but I wasn't too sure how to go about installing it, and on top of that installing it with a .mdf.

PS i'm positive it works on windows with MagicDisc.

---

### Post by llamabr on 2009-07-07
Hi.  Sorry, I don't use wine, but if it says on your discussion board that it works perfectly, perhaps a better place to post this question is on that discussion board?

report back if you succeed.

---

### Post by ktulu19 on 2009-07-07
sorry by DB i meant Database(the one on Wine's website). I don't think it says anything about installing from a .mdf. I'll post here if i succeed. I'm sure I won't be the last one to attempt this procedure.

---

### Post by synapsys on 2009-07-07
You can use the gmountiso to mount iso's. If this doesn't work for your .mdf then try converting it to an iso with mdf2iso package.

---

### Post by abhiroopb on 2009-07-07
Hi there, don't bother with posting on wine. The main issue here is the MDF and MDS. Basically, whether the game installs and works with wine is one step further than where you are right now.

To install in wine you generally need the **setup.exe** file that virtually every game comes with. To get to this file you will have to mount your .mdf file and browse the mounted file (as though it is a CD) and then look for the .exe file.

First, download [Acetone ISO]("http://www.getdeb.net/app/AcetoneISO").

After installation start up the program and it is fairly self-explanatory. You will just need to browse to the .mdf file from the Acetone ISO browser and it will mount it. Then you can use your file browser in ubuntu to open up the mounted drive. Then just double-click on the file that is called "setup.exe".

As you can tell my instructions are general, the file may not be called "setup.exe" so use your judgment.

Let me know if it works!

---

### Post by ktulu19 on 2009-07-08
did it. it runs fine (somewhat of a low framerate, but i'm on an old laptop so i don't expect much.)

I downloaded Acetone, renamed the .mdf to .iso (it told me to do that when i tried to convert it.)

Then i used Acetone to extract the data from the iso, ran the setup.exe with wine, installed, and enjoyed.

thanks abhi.

---

