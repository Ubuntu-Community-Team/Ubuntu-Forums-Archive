---
title: "Losing Windows boot on dual boot Windows/Ubuntu machine"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by windows22 on 2010-08-22
Hi 

Does anyone here have any comments on this thread:
[http://www.linuxquestions.org/questions/linux-newbie-8/losing-windows-boot-on-dual-boot-windows-ubuntu-machine-826934/](http://www.linuxquestions.org/questions/linux-newbie-8/losing-windows-boot-on-dual-boot-windows-ubuntu-machine-826934/)

I doubt the last suggestion there that I can't dual boot Win 98 and Ubuntu because it worked for several months then failed after an Ubuntu update as all my efforts to dual boot Win & Ubuntu eventually do... 

Any advice really welcome. 


Thanks

---

### Post by dagdeniz on 2010-08-22
I would advise you to: 
1. try update-grub2 instead of update-grub
2. if that doesn't solve anything, first boot to win98 manually (by pressing "e" on the grub screen and changing the parameters; you must know the sda number) then add a boot entry manually ([http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html](http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html) -the part with the title "custom menu tweaks).

---

