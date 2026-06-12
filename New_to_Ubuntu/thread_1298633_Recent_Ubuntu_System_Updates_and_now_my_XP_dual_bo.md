---
title: "Recent Ubuntu System Updates and now my XP dual boot is gone"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by andrewcd on 2009-10-23
So I love ubuntu, but I am not a programmer.  I just use computers and I like them to work quickly and unpretentiously.  I have very much liked ubuntu for the four months that I have been using it, but I don't understand it like most on this forum do.  

So I need your help.  

Just now I let ubuntu install updates.  I don't know what any of the files were -- kernels and things, whatever they are.  Now, after installing these updates in the ubuntu GUI, GRUB no longer shows the option to boot in windows XP.  It just shows several different ubuntu options, each with an associated safe mode.  

I do not know why there are so many ubuntu options, and I do not know why XP is gone.  Previously, there were 3 or 4 ubuntu options, each with an associated safe mode.  Now there is one more, where the XP option used to be.  

I can still access the files that I had on XP from ubuntu however -- the "preload" drive is accessible in the file browser.  

I need XP for video games and occasional microsoft excel -- largely because I cannot get WINE to work.  So this is not terribly urgent, but it is a problem.  

Any advice would be much appreciated.  

Thanks.

---

### Post by undecim on 2009-10-23
press Alt+F2 and type "gksu gedit /boot/grub/menu.lst"

A text editor will pop up with a file loaded. At the end of that file (on a new line after "### END DEBIAN AUTOMAGIC KERNELS LIST"), paste this: ```

title        Windows XP
rootnoverify        (hd0,0)
makeactive
chainloader    +1
```this is assuming that XP is the first partition on your hard drive. if it is the second, replace the (hd0,0) with (hd0,1)

---

### Post by lockettpots on 2009-10-23
Are you sure it has disappeared from your Grub list.
It may just be that with the addition of another entry it has just moved below the visible potion of the display.

Move the highlighting down to the bottom of the visible list and keep going. You may find the entry down there.

---

