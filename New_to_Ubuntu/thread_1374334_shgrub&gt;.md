---
title: "sh:grub&gt;"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by battleshipterry on 2010-01-06
**Problem is back** no grub on boot up reference to earlier post.
[http://ubuntuforums.org/showthread.php?t=1372286](http://ubuntuforums.org/showthread.php?t=1372286)

My Itouch was hooked up to usb this time not sure if this is related,what is going on? I did updates in Ubuntu and windows but not sure what is dumping the grub2 so far only way to fix is reinstall Ubuntu and loss all previous install.I cant believe I am only one having this problem.It should not be related to hard ware.I looked in the file Grub while in windows it is empty just like someone deleted it.I had just installed Ubuntu within windows and did all updates.



This is error on boot up screen.


GMU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub>
battleshipterry is offline Report Post   	Edit/Delete Message

---

### Post by tom.swartz07 on 2010-01-06
> **battleshipterry said:**
> **Problem is back** no grub on boot up reference to earlier post.
[http://ubuntuforums.org/showthread.php?t=1372286](http://ubuntuforums.org/showthread.php?t=1372286)

My Itouch was hooked up to usb this time not sure if this is related,what is going on? I did updates in Ubuntu and windows but not sure what is dumping the grub2 so far only way to fix is reinstall Ubuntu and loss all previous install.I cant believe I am only one having this problem.It should not be related to hard ware.I looked in the file Grub while in windows it is empty just like someone deleted it.I had just installed Ubuntu within windows and did all updates.



This is error on boot up screen.


GMU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub>
battleshipterry is offline Report Post   	Edit/Delete Message

Again, I believe that this problem is related to WUBI. I would hazard a guess that your drive is really really full because it seems to get so fragmented so quickly.

My advice would be thus:

See if you could clear any large files from your Windows Drive. Run defrag, I would suggest Defraggler, available for free. Google will turn up some good links- I believe its available on CNet also.

Now that your drive is cleared up and cleaned up, see if that fixes the errors with grub for your WUBI install.

ADDITIONALLY, with all due respect, if you are interested in using Ubuntu for more than just once or twice a week, I would recommend you install under Dual Boot. WUBI isnt really designed for situations of high use like this, and you might end up severely damaging your data on both Ubuntu and Windows if you keep using it like this.

---

### Post by alzie on 2010-01-06
It is a WUBI issue and it is known.  I ran into it to.

After the first update after the WUBI install you need to open terminal and run ```
sudo update-grub
``` I'm not sure if this needs to be done after later updates or only if there are GRUB updates like you have after the initial install.

I don't think this affects true dual boot installs of Ubuntu (where you actually install Ubuntu onto a partition of your harddrive) but it does affect WUBI installs because of the way WUBI sets up GRUB.

I hope this helps.

---

### Post by centaure on 2010-01-06
[B]a
[/B]

---

### Post by battleshipterry on 2010-01-07
My hard drive has 42 gig free using 32 gig so it has a lot of free space,had ran defrag not to long ago. I am going to try Alzi's suggestion of sudo update-grub, but I think I tried it and it was not one of the limited commands that it will allow me to use at the boot up screen where the error has been displayed.not sure how to boot to terminal to use the command unless I could use a live cd for that.I am still not that good at this yet to be comfortable and not toast winders while in the live cd boot.

---

### Post by alzie on 2010-01-07
The option I offered has to be done from inside ubuntu.  Basically reinstall Ubuntu using WUBI and then run the grub update after the round of updates you get from Ubuntu.

If you want to try and access your current installation from the sh:grub> you can try the methods here:  [http://ubuntuforums.org/showthread.php?t=1312249](http://ubuntuforums.org/showthread.php?t=1312249)

I tried to follow the directions but got too frustrated and ended up just reinstalling then using the update to prevent the problem from recurring.

Sorry if I caused confusion

---

### Post by battleshipterry on 2010-01-08
Nice thanks Alzie.I will do the reinstall and updates then sudo update-grub at terminal in Ubuntu.and thanks Tom every ones help is great, keep up the good work.I will marked this solved.

---

