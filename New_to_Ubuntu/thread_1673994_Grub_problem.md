---
title: "Grub problem"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by adeee on 2011-01-23
guys i just copy 
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.copy 



then i cant found error is cp: cannot strat `/boot/grub/menu.lst': No such file or directory


and when i check my grub folder no menu.lst is there.


i am installing boot splash screen.




in previous ubuntu versions there are System--->Administration--->Login Window
but in 10.04 i cant see this. 

another
System--->Appearance-->Sessions then startup.
i also cant see this.

am asking because on net these lines wrote some articles. 
Why ubuntu dont make any standard? every version is different from previous one.
its bothered.

---

### Post by fabricator4 on 2011-01-23
> **adeee said:**
> 

am asking because on net these lines wrote some articles. 
Why ubuntu dont make any standard? every version is different from previous one.
its bothered.

It's not that bad, it's just that grub 2 is different from the old grub.  You need to make any changes you want in /etc/default/grub, then run update-grub to get them written into grub-cfg

update-grub also seems to fix problems of a valid kernal not being found when device assignments change and that sort of thing.

Chris.

---

### Post by kansasnoob on 2011-01-23
Beginning with Ubuntu 9.10 fresh installs now use grub2 instead of the old legacy-grub and grub2 does not have a menu.lst.

Also, beginning with 10.04 Ubuntu uses plymouth rather than using usplash. I can't remember when we changed gdm versions? It's been a while.

But I think this should help you:

[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

Just be careful! **If you break it, you own it** ;)

---

