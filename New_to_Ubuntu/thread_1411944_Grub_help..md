---
title: "Grub help."
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Patar on 2010-02-20
Ok I just installed ubuntu using wubi. I rebooted my computer and ubuntu started installing. After it was done installing it rebooted again. Then I pressed ubuntu from the start up menu and it led me to this screen that says: GNU GRUB version 1.97 beta 4. Then under it it says: 

[ minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/ file completions. ]

Then it tells me to enter a command and I don't know what to do. Can someone help?

---

### Post by J V on 2010-02-20
First of all, learn how to install, you can't have installed ubuntu in wubi by restarting: find out what exactly you did to your computer and post back.

---

### Post by thefoolisme on 2010-02-20
> **J V said:**
> First of all, learn how to install, you can't have installed ubuntu in wubi by restarting: find out what exactly you did to your computer and post back.

JV - your tone is just a little offputting.  "First of all, learn how to install" doesn't sound very friendly.  It is the Absolute Beginner area after all.  

Have some patience.

---

### Post by Patar on 2010-02-20
Well I used wubi. Then after that was all set up it asked if I want to reboot now or later, and I clicked reboot now. Then after it rebooted I actualy started downloading ubuntu. Then after that was done it rebooted again. Then that grub screen poped up. Sorry if I'm not being clear I'm new to this.

---

### Post by J V on 2010-02-20
> Well I used wubi. Then after that was all set up it asked if I want to reboot now or later, and I clicked reboot now. *Then after it rebooted I actualy started downloading ubuntu.* Then after that was done it rebooted again. Then that grub screen poped up. Sorry if I'm not being clear I'm new to this.Wait, what? Did wubi ask you to reboot after installation or something?

Also, you should just be able to press enter at grub to select the highlighted menu item, ignore that text...

---

### Post by Patar on 2010-02-20
Yes it looked like this 
[IMG]http://i50.tinypic.com/22nxhj.png[/IMG]

But the thing is there isn't anything highlighted it like makes me enter a command. Do you think i should just try uninstalling it and re-installing it?

---

### Post by redfrog1978 on 2010-02-20
I believe im having a similar issue. After doing some recent updates in Linux, i was prompted to restart the computer. After reinstalling the computer, i selected Linux from the boot menu at startup and and the loading process stopped at the boot loader. I typed exit and booted into xp to figure out what is wrong. Any help would be appreciated.

Thanks

---

### Post by J V on 2010-02-20
They are probably unrelated, boot a live cd and google re-installing grub, that should fix whatever problems you come across...

---

### Post by redfrog1978 on 2010-02-20
OK. Ill give that a shot...

---

### Post by stoogiebuncho on 2010-02-20
> **Patar said:**
> 
But the thing is there isn't anything highlighted it like makes me enter a command. Do you think i should just try uninstalling it and re-installing it?

Yes, I would try reinstalling.  If it was a full install we could try to figure out what's going wrong with your grub menu by booting up a live cd, but because it's a wubi install I don't think there's any way to do that.

---

### Post by Patar on 2010-02-20
I reinstalled it and it didn't work. The same screen pops up. I tried the full install before wubi but the re partioning was to hard for me. I saw someone else had this problem though.

---

### Post by Patar on 2010-02-20
I got it to work. I used the CD instead of Wubi. There must be something wrong with wubi.

---

### Post by stoogiebuncho on 2010-02-20
Glad it's working for you.  I think you'll be glad you went for a full install instead of Wubi.  Wubi is great for trying out Ubuntu, but a full install is generally faster and more reliable.

---

### Post by meierfra. on 2010-02-20
> 
[ minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/ file completions. ]


This is caused by a bug in Grub2. See this link  for the solution:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

