---
title: "Ubuntu fails to start"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by babloo75 on 2009-12-24
I switched off my Ubuntu yesterday, and all was fine. But now it has failed to start. When I try to do so the black screen with options of starting the versions come, but there is no mention of Ubuntu starting in seconds at the bottom portion of screen.
When I press "Enter" the black screen with Ubuntu logo comes for few seconds, then it disappears. The screen turns dark and it stays forever...
What should I do now.
(My computer has dual boot- windows 7 with Ubuntu) and right now I am typing this thru Windows.
Please help.........

---

### Post by LowSky on 2009-12-24
choose one of the options for safe mode. try to boot to that

---

### Post by babloo75 on 2009-12-24
I tried that but could not understand anything there...

---

### Post by fslezak on 2009-12-24
At the GRUB boot, select "Recovery Mode". Try the dpkg recovery. It might also be X (I dunno) so try xfix. If any of those work, you're done.

---

### Post by babloo75 on 2009-12-24
> **fslezak said:**
> At the GRUB boot, select "Recovery Mode". Try the dpkg recovery. It might also be X (I dunno) so try xfix. If any of those work, you're done.

Ubuntu 9.10 is not like the older versions. The recovery mode is different.
Will shifting over to some other linux- fedora or suse help me save my data?

---

### Post by Guilden_NL on 2009-12-29
For all problems where the system seems to hang, I recommend going into the start up and editing out "splash quiet" in the start up line.

This allows you to see what's loading, what's failing and where it hangs.

Go to the grub boot menu (you described it as "black screen with options...") and press the letter e  and it will present you with that start up line - at the end of it will be "splash quiet", just use your backspace key to delete only those two options.  You then press the letter b key to boot.  This will allow you to see what's going on when your system boots up.

---

### Post by dtapia63 on 2010-03-23
I have the same Dell2400, after installing 9.10 2.6.31-14  everything worked fine. First kernel upgrade to 2.6.31-19 also fine but the last upgrade to 2.6.31-20 gives me a black screen and I am unable to log in, after the splash the screen goes to black. Now both of the two previous kernels give me the black screen. 

I tried following some of the suggestions in this thread but I wasn't able to get anywhere, however, I did log in using the recovery kernel. It took me to the text based login and after logging in and startx I was able to have my GUI but I am unable to switch between users, everything else seems to be working fine.

Any more suggestions..?!?!

Dell 2400
P4 2.66Ghz
1Gb Ram
No video card but I don't know which video chip set I have, how can I find that out?

---

### Post by boofastic on 2010-08-31
I had this same problem with a similar pc until I found this.. 
[http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html](http://linux.dipin.info/2009/06/blank-screen-after-boot-process-in.html)

---

