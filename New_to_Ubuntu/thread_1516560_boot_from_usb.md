---
title: "boot from usb"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by 007casper on 2010-06-23
downloaded server edition 64bit to a stick.  Follow the instructions, start up disk etc... reboot, it doesnt load the installation.

any ideas?

---

### Post by VH-BIL on 2010-06-23
The boot options for your computer should be in your bios.

---

### Post by C.S.Cameron on 2010-06-24
Are you trying to install to USB? Are you using the start up disk creator that comes with Ubuntu?

---

### Post by VH-BIL on 2010-06-24
I think he is trying to install from USB.

---

### Post by JP121 on 2010-06-24
Your computer may not allow booting by USB.  I spent two hours yesterday trying to get it to work, only to try the CD install and get it all working in minutes.  

If you can, try a CD.

---

### Post by VH-BIL on 2010-06-24
If it is not allowed you can have a look to see if there is a firmware upgrade for you motherboard that may allow it.

---

### Post by 007casper on 2010-06-26
it was a bumpy ride but finally I got it to work with usb.  It kept not working properly.  It is loaded. 

However, the search box on synaptic doesnt work.  

And the shutdown button, and any of the icons on the top right says "No Indicators"

any suggestions?

---

### Post by sukigenseki on 2010-06-26
Does the search box on synaptic say Rebuilding search index? If it does then it will stay grayed out until it finishes, and will only do that once, and even if you add new repositories and it needs to rebuild the index it won't totally gray out since there is stuff already in the index. It might take a while for it to finish depending on your system, so my advice if that is the case would just be to let it stay open for a little while and let it do it's thing.

---

### Post by sukigenseki on 2010-06-26
If the panel is messed up does removing ~/.gconf/apps/panel and then restarting X (or gnome, or the whole darn thing) help?

---

### Post by 007casper on 2010-06-28
no synaptic search box is totally dead, and right top icons are not there.

when I installed desktop I wrote on the terminal
> sudo apt-get install ubuntu-desktop --no-install-recommends

I wonder if something didnt load correctly.  

How can I fix the situation?  

Thank you.

---

### Post by lkjoel on 2010-06-28
Did you try UNetBootIn?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install unetbootin
unetbootin
```

---

### Post by 007casper on 2010-06-28
I did do apt-get update, and upgrade.

Why do I need unetbootin?  I am confused.  I am not booting from usb.  I am booting from the internal hard drive.

I still have the same problem.  Synaptic search box is grey.  I cant access it.  Also, the top right corner icons says "USA No Indicators Mon Jun 28, 1:38PM No Indicators"

Please, advise.  Thank you.

---

### Post by 007casper on 2010-06-28
** bump **

---

### Post by lkjoel on 2010-06-29
Did you update the bios?
Usually that is the problem.
You might also need to stay in the shell, and update your system.

And I know that this is slightly off topic, but I see **bump** all the time.
What does it mean?

---

### Post by 007casper on 2010-06-30
bump is when you try to bump your thread to the top of the list, so someone in the community would provide a solution for the problem posted.  

I dont think the bios is the issue though.

I think something didnt load properly.  How do I check if the system loaded properly?


It seems like only the top right icons, and the synaptic is the issue. 

If I reload > sudo apt-get install ubuntu-desktop --no-install-recommends Would that fix the issue?

Please, advise.  Thank you.

---

### Post by lkjoel on 2010-06-30
Maybe, but my computer does not have that installed, and it still works.

---

