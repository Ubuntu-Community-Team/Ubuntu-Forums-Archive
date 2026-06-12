---
title: "Choosing which OS to use"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by TerryV on 2011-03-19
I have partitioned my drive and have XP on one partition and wish to install Ubuntu on the other.
Before I do so, I need to be sure I can select which OS I wish to run.

How is this achieved?

Do I need to install something else before I proceed with the Ubuntu installation?

In future when I start my notebook, at what point will I be asked to make the selection?

Thanks

---

### Post by thunderbirdje on 2011-03-19
When you boot from a Live Cd, you have to option to "test" or "to install", when you choose to install you will be able to install it as a second OS where after a bootmenu will appear.

Good luck and have fun!

You might be interested in 

[http://doc.ubuntu.com/screencasts/Installing_Ubuntu_with_Windows_Dual-Boot](http://doc.ubuntu.com/screencasts/Installing_Ubuntu_with_Windows_Dual-Boot)

or if you can't view video you can read up on the process here

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by kroq-gar78 on 2011-03-19
or you can not partition it and use wubi ([http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)). Basically, if anything goes wrong in ubuntu, you can uninstall it really easily (through programs & features in windoz). If you do it this (wubi) way, then it asks for which to boot as soon as the windows boot manager comes (it'll be defaulted to windoz, and wil load that after ~10 seconds). If you do it the way YOU want to, you HAVE to make sure that it DOESNT erase windoz - otherwise you won't be able to go back very easily. Sorry for the possibly confusing post. Post if you have any questions.

BTW: I only use the REGULAR (non-wubi) install on my desktop and one of my laptops. My other 2 comps are running wubi 10.04. I MIGHT do the regular way for my awesome new toshiba laptop which i got yesterday :D

NOTE: the maximum space available on wubi is 30GB, but you can just save all of your stuff on the windoz partition (which is in the directory called '/host/' through WUBI)

---

