---
title: "new and need help"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by jallem on 2010-10-25
I'm brand new to this so pardon my ignorance.

I installed Ubuntu 10.4 in dual boot config on a Pentium 4 386 box.  I notice a few problems right out of the gate and I'm not sure if they are just platform limitations.

When I try to install Adobe Flash 10 for Linux (.deb) I get an error referencing i386. I installed the 32 bit version of Ubuntu, so I'm not sure where the problem is. I think I've gotten similar messages trying to install other items.

I also cannot send mail to the SMTP server I use even though all the settings are correct. The POP3 works great on the incoming side.

Thanks!

---

### Post by ivarn on 2010-10-25
It would probably help if you posted a link to the site where you found the flash plugin.
Also, you should run this command 
```
sudo apt-get install ubuntu-restricted-extras
```
Ok this will give you the flash, java and video codecs you'll need for your system.
Since you installed adobe flash from a .deb file I assume you didn't install it from synaptic package manager.
What other programs have you tried to install?

---

### Post by spiky001 on 2010-10-25
1386 is for the 32 bit system as is x86

---

### Post by TBABill on 2010-10-25
Best option is to always install from the repositories unless your system requires something outside of them. Using Synaptic you just mark an item for installation and then click apply when ready. Or use the Ubuntu Software Center to do the same thing in a bit different way (click the item, then click install).
 
The Ubuntu restricted extras pulls it all in for you. If you get finished and something with java doesn't work, just install the sun java plugin, also in the repos. You may have to remove the open source java if it conflicts but I can't recall. I always remove them first then install sun java.

---

