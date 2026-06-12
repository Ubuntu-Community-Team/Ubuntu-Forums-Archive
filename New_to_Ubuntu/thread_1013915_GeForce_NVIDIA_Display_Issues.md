---
title: "GeForce NVIDIA Display Issues"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2008-12-17
Hello all, i have another slight issue, this time with my video card. every time i move a window, or minimize one, i'm giving a lagging effect like how old windows had the option of 'trails' on their mouse. I'll attach a screen shot.

I wouldn't think too much of it, but I'm running Ubuntu on a brand new PC, Triple Core AMD with 4gb of RAM, GeForce 8200 video card. My laptop (3 years old) seems to run Ubuntu better.

Also, the reason i'm blaming this on the video card is that when i first installed Ubuntu, yesterday, i was greeted with a warning about how my video driver wasn't compatible and blah blah, but that ended after i downloaded an update.

any ideas guys?  Thanks in advance.

---

### Post by Therion on 2008-12-17
Which version of 'buntu are you on?

Have you checked that you are, in fact, running the restricted driver for your video card?  Once it's downloaded it still may need to be enabled.

---

### Post by x0prah_Winfr3yx on 2008-12-17
I just downloaded the latest 64-bit version. Yes, i was running a restricted driver at first, after that update i spoke of i had to click on that little driver icon and verify that i wanted to activate it.

i don't think it's restricted anymore, that icon has gone away. here's that screenshot i spoke of earlier

---

### Post by Hospadar on 2008-12-17
Try running a good system monitor program (from the command line) like top or htop (htop is very nice, you'll need to install it from the repos though) and watch it while these problems are happening.  It might help you to identify which process is slowing you down.

Also, you might try monkeying with your compiz settings (if you havn't done so already, install compizconfig-settings-manager from synaptic, you can get to it from System->Preferences->Compizconfig) and see if maybe disabling some plugins or changing what the do helps at all.

I suppose you could try removing and re-installing your video driver, and see if that helps.

---

### Post by Therion on 2008-12-17
> **x0prah_Winfr3yx said:**
> I just downloaded the latest 64-bit version. Yes, i was running a restricted driver at first, after that update i spoke of i had to click on that little driver icon and verify that i wanted to activate it.

i don't think it's restricted anymore, that icon has gone away. here's that screenshot i spoke of earlier
Looks like the restricted driver is installed and running properly alright (the "restricted" driver is the driver that is written by nVidia; it's called that because the source code is not open-source like Ubuntu.  Hence we Linux users can use their drivers but with "restrictions").  

Also, what I was asking is what version of Ubuntu are you running *as in Hardy Heron or Intrepid Ibex*?  The reason I ask is because Intrepid handles Xserver quite differently than Hardy does.

My last suggestion would be to try using the latest restricted driver.  Version 180 is out and a lot of people are reporting big performance improvements once it's installed.



Ahhh... Here's the thread on the new nVidia 180 series drivers:  [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180)

---

### Post by x0prah_Winfr3yx on 2008-12-17
Thanks for your input guys.

i installed the latest version of my video card driver (180.16) but that didn't help.

i also installed the htop that was mentioned, but my computer isn't running much. my cpu is working around 20%.

i am cursed here?:confused:

---

### Post by x0prah_Winfr3yx on 2008-12-17
> **Hospadar said:**
> you might try monkeying with your compiz settings (if you havn't done so already, install compizconfig-settings-manager from synaptic, you can get to it from System->Preferences->Compizconfig) and see if maybe disabling some plugins or changing what the do helps at all.

i also disabled all of the effects plugins without any luck.

---

### Post by GrantsV on 2008-12-17
This is a common problem with 8000 series NVIDIA cards.  Please visit nvnews.net and go to the Linux forum.  The latest drivers 180.11.02 seem a big step in the right direction addressing this problem.
Good luck!

---

