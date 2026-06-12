---
title: "no more ubuntu after ATI Catalyst Center?"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by marcellux on 2009-08-13
Hello everybody!

I need some help. I was using Ubuntu 9.04 for 2 weeks without any problems. Yesterday, I activated the ATI Catalyst Center from the repository. I tried to open it and nothing happened, or so I thought.

When I restarted Ubuntu 9.04, the Grub loader was there (I am using dual boot with Vista) I chose Ubuntu, the loading screen was there, and after a while waiting, the screen beginns to flash and show funny colours. It all ends up in a self reboot. 

Vista starts without problems. But any time I try to start Ubuntu, it happens the same.

Does anyone have the same problem and could help me out with this issue please?

Thanks a lot

---

### Post by Duskao on 2009-08-13
Well, it sounds like you are having a driver issue. But to be sure we are going to have to know what video card you are using? Unless it's a HD2000 series or newer then it isn't supported within Ubuntu 9.04. I know... It sucks. However, there is some good news. The guys working on the open source drivers (the one that comes with ubuntu) for the Ati stuff are coming a long way and rather quickly as well. So eventually there should be decently suitable drivers for Ati that come with Ubuntu without even having to install anything extra. But, once again, that the future. For now... stick with the open source drivers (if you don't game on ubuntu you should be fine) or you might have to give 8.10 or older ubuntu's a try so that the kernel supports Ati's drivers...

---

### Post by automaton26 on 2009-08-13
If you installed your ATI drivers by using the ATI install instructions (that's what I do), then you can uninstall them the same way [http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

If that applies to you, you can get to a command prompt by pressing the ESC key during boot. That gets you to the GRUB menu (OS selection) and then select the "Recovery Mode" option. Once you get to the next menu screen, choose the option that gets you to an administrator login prompt, and just log in. Then you can enter the commands to uninstall the drivers.

Reboot, and the default ubuntu drivers will work, and then finally you can try installing the latest ATI drivers again.

---

### Post by alphacrucis2 on 2009-08-13
> **marcellux said:**
> Hello everybody!

I need some help. I was using Ubuntu 9.04 for 2 weeks without any problems. Yesterday, I activated the ATI Catalyst Center from the repository. I tried to open it and nothing happened, or so I thought.

When I restarted Ubuntu 9.04, the Grub loader was there (I am using dual boot with Vista) I chose Ubuntu, the loading screen was there, and after a while waiting, the screen beginns to flash and show funny colours. It all ends up in a self reboot. 

Vista starts without problems. But any time I try to start Ubuntu, it happens the same.

Does anyone have the same problem and could help me out with this issue please?

Thanks a lot

Which ATI card do you have?

---

### Post by marcellux on 2010-02-06
thanks for the help! the card is ATI radeon express 1100. I already re-installed ubuntu!

cheers

---

### Post by Mark Phelps on 2010-02-07
Just to let you know ... if you had bothered to answer the question about your video card back in August, we could have given you a link to some instructions that would have prevented you from reinstalling your OS.

Next time you come here for help, how about answering the questions we ask you.

---

### Post by marcellux on 2010-04-05
@ Mark Phelps : you are right. I am sorry I misused the forum, my problem and its resolution would have helped other users. I will be more patient next time.

cheers

---

