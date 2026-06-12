---
title: "UI won't  load"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by superninja on 2010-07-05
I'm running ubuntu 10.04 on my laptop and when I turn it on I get a command prompt and I login, then I run startx and the screen goes blank. It has worked many times before but now it won't. Any help is greatly appreciated

---

### Post by superninja on 2010-07-05
I'm running ubuntu 10.04 on my laptop and when I turn it on I get a command prompt and I login, then I run startx and the screen goes blank. It has worked many times before but now it won't. Any help is greatly appreciated

---

### Post by overdrank on 2010-07-05
Hi and welcome, please do not create multiple threads on the same issue. It may help if you could give us some system specs.

Moved to Absolute Beginner Talk

---

### Post by superninja on 2010-07-05
Ok, I'm sorry. I installed ubuntu 10.04 last week and it has worked great, until now. I turn my laptop on and commands come up then I log in with my user name and password then i type in "startx" and my screen goes blank. I'm on a Sony Vaio, ubuntu is the only operating system on it, it is about 10 years old, 40 gig hard drive, probably about 1 gig RAM, Im not sure of any other specs sorry.

---

### Post by philinux on 2010-07-05
> **superninja said:**
> Ok, I'm sorry. I installed ubuntu 10.04 last week and it has worked great, until now. I turn my laptop on and commands come up then I log in with my user name and password then i type in "startx" and my screen goes blank. I'm on a Sony Vaio, ubuntu is the only operating system on it, it is about 10 years old, 40 gig hard drive, probably about 1 gig RAM, Im not sure of any other specs sorry.

Reboot and let it get to the command prompt then login. Dont use startx.

Try this first

```
sudo apt-get update && sudo apt-get upgrade
```

Any idea what graphics card it has or the model name/number of the vaio, look at the base of it.

---

### Post by superninja on 2010-07-05
I turned on my computer and the UI suddenly worked, I did not type in the commands you gave me because it did not come up to a command line. Is there anything I can do to prevent this from happening again? And where can I learn more about the ubuntu commands, is there a website or book available? Thank you very much for your help :)

---

### Post by superninja on 2010-07-05
Should I still run these commands in terminal?

---

### Post by superninja on 2010-07-06
This morning I turned on my laptop and it came to command line again, I have run the commands that you posted and my screen went blank. My model # is PCG-V505BX, my graphics card is ATI MOBILITY™ RADEON™ 16 MB video DDR SDRAM. Thank you

---

### Post by superninja on 2010-07-06
Now I turned it on and the UI came up. I have done absolutely nothing different.

---

### Post by xlr8.at on 2010-07-06
Hmm, I had same issues, but with a nvidia card. My Issues where gone after I manually added my monitor specs inside the xorg.conf. It seemed like when xdm startet, it didn´t always get the Hsync and Vsync right,  and my Monitor suspended because it ran out of sync and turned black. 

There must be a manual for your vaio somewhere in the internet. Maybe you give it a try.

BTW you can always look inside your log-files. Maybe you´ll see a message there, which tells you what was happening when only a console came up. 

When your in UI , then you can take a look at the logfiles at system -> systemmenagement (Systemverwaltung, sorry I only have a german version) -> Logfile viewer.

Regards Andre

---

### Post by philinux on 2010-07-06
> **superninja said:**
> Now I turned it on and the UI came up. I have done absolutely nothing different.

Could be a hardware problem as it's so intermittent.

---

### Post by superninja on 2010-07-06
Thank you all very much for all the help. If I find a solution or figure out the problem I will post it

---

### Post by xlr8.at on 2010-09-04
Hy, 

I am unsure if my PM did reach You superninja, but I&#314;l write it down here too:

if its not too late, here are my 5 cent to the problem. I had 2 Problems  with X,proprietary drivers, booting etc.

First problem I encountered was the resolution and effects with my geforce,  other one was, that it booted nearly always into command line mode, and  only sometimes in GDM, sometime GDM with safemode 640x480. It did it  totally random, but more often into command-line. I could manually start gdm in 640x480 safe mode. But not always.

My problems with that booting in the command-line mode was gone, when I  removed "plymouth" pkg´s and re-installed them. Somehow, I saw inside  the logfiles a hint, that plymouth had caused problems, and somehow  X-Server (GDM) was involved or couldn´t start when plymouth had a problem. When I had  reinstalled the plymouth core pkgs with standard parameters, the problem  with plymouth was gone, and my system now boots with UI (Gnome).

Second Problem was that my gnome when it startet now only could go with  640x480... I went back to commandline, and downloaded the newest  nvidia.pkg, I apt-get remove *nivdia, X-server etc. and installed only  x-server nvidia, and the newest nvidia driver. I removed all proprietary drivers too.

That repaired my effects problem.

Then starting gdm did work but only in 4:3 sizes, I own a 16:9 HD-Resolution. When adding that resolution manually to my xorg.conf, my monitor suspended (turned black) - now I now why - it ran out of sync.so i had to get the Vsync and Hsync from my Monitors manual  into the xorg.conf, I manually added the lines and commented out unused  parameters, then a reboot, and since then everything works flawless.     

Somehow, with minimum knowledge of Linux I managed to get my problems solved. I made some manuals for myself, so I would remember every step I  did. Because it was quite a experience working only in commandline... 

I sorry I can´t explain it better, I a Newbie to Linux.
Feel free to ask me again, if You have a question to my solution, I´ll be glad to help.

CU

---

