---
title: "grub problem with updates on wubi install of 10.04"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by gertrude58 on 2010-05-09
Twice I installed 10.04 with wubi on  windows 7.Everything went well both times until I tried to update,there were loads to download and this was fine.then they started to install and thats where it all went wrong.The first ones were all right I think,then a box came up asking if I wanted to configure Grub 2 so I said yes as there was a stern warning of things to go wrong if I didnt.Then it started and the progress bar got 2/3 of the way across and just stopped. I left it for ages and nothing more happened.It seemed to be frozen.I had no alternative but to shut down,go into windows and delete Ubuntu.So I tried again and installed,downloaded updates etc.and the exact same thing happened.Would it have been better to ignore the warnings about grub and leave the configuring thing alone?Or am I doing something else wrong?

---

### Post by Paqman on 2010-05-10
Which option did you pick when it asked you how you wanted to configure Grub?

---

### Post by deadite66 on 2010-05-10
just selected yes to carry on **without** installing grub-pc, let you know what happens when its finished updating :)

Update: boots fine.

---

### Post by gertrude58 on 2010-05-10
I selected the option to install grub 2 so Id better try again and select the other option?

---

### Post by wil08son on 2010-05-10
> **gertrude58 said:**
> I selected the option to install grub 2 so Id better try again and select the other option?

Yes. Grub would only be necessary if you actually installed Ubuntu on your hard drive. Since it's a Wubi install, you don't need to install grub 2.

---

### Post by gertrude58 on 2010-05-10
Great!Here I am on ubuntu ,all updated successfully.Thanks a lot, people.

---

### Post by beyar on 2010-05-10
Hello,
I have exactly the same problem but I was upgrading, not new install.  I told it to install grub on all partitions.  Now when I boot up, I have choice of windows or ubuntu but when I choose ubuntu, my pc reboots.

Is there a way to fix this as I prefer not to have to reinstall packages?

Also, being that wubi is so unstable, I am thinking of repartitioning my disk but have heard that as I have no install disk for win7(it came preinstalled), win7 may decide I have a pirate version and lock up.  is that true?

---

### Post by jobaehr on 2010-06-09
i made the same mistake as gertrude - trying to installl grub 2 with the updates after the initial wubi install.

now there is an extra screen when i boot - after selecting ubuntu over windows, there is another screen with options for four different ubuntu bootups (two of which are labeled "restoration") as well as the windows option.

is there any way to undo or uninstall whatever traces of the grub install have apparently caused this problem?

---

### Post by wilee-nilee on 2010-06-09
> **jobaehr said:**
> i made the same mistake as gertrude - trying to installl grub 2 with the updates after the initial wubi install.

now there is an extra screen when i boot - after selecting ubuntu over windows, there is another screen with options for four different ubuntu bootups (two of which are labeled "restoration") as well as the windows option.

is there any way to undo or uninstall whatever traces of the grub install have apparently caused this problem?

The best thing to do is to start a thread and post the bootscript in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Your own thread will make it easier to diagnose the problem, and just be sure to use the code tags so that it is easier to read. ;)

---

