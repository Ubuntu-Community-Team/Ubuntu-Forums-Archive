---
title: "Need help: ubuntu 10.04 wont load with windows 7 dual boot"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by pankaj.gadade on 2010-09-03
Hi Team, i need help urgently, request you to kindly help me asap. I am pretty new Linux as i am a windows guy and very keen to work and learn linux coz i am in love with it. I installed a fresh copy of windows 7 and then installed Ubuntu 10.04 within it. It worked for a few days. When i boot up the pc i get two options windows 7 and Ubuntu. When i select windows it works fine. When i select Ubuntu it gives me a minimum edit utility and the prompt just says grub> i have tried serveral commands but it does not take any of them. Unknown command. Earlier i used to get four options within ubuntu for some kernels and i used to select the first option. But this is strange. I have tried to boot with windows 7 dvd and fix mbr and boot but does not work. I booted to ubuntu cd and in terminal i tried setup, root, find list 1 etc commands none of them work. i searched the entire forum but no go. the screen says i am using some grub lubuntu 0-98 or something like that at the top.  the only changes i have made to ubuntu since i have installed is some security fixes which automatically popped up. Audio video codecs, Kbuntu desktop as i liked the interface. Default boot manager was selected as Gnome. Please help. what do i need to do now?

---

### Post by Rubi1200 on 2010-09-05
Hi and welcome to the forums :)

Please boot the computer with the Ubuntu CD, choosing to try not install.

Post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by Mark Phelps on 2010-09-05
> **pankaj.gadade said:**
> ... I have tried to boot with windows 7 dvd and fix mbr and boot but does not work... 

Did you open a command line and run "bootrec.exe /FixMbr" ?

Or did you just run Startup Repair once?

If the latter, you need to run it THREE times -- it repairs the MBR on the third pass.  So, if you run it fewer than three times, you won't see any MBR changes.

---

### Post by sandyd on 2010-09-05
> **pankaj.gadade said:**
> Hi Team, i need help urgently, request you to kindly help me asap. I am pretty new Linux as i am a windows guy and very keen to work and learn linux coz i am in love with it. I installed a fresh copy of windows 7 and then installed Ubuntu 10.04 within it. It worked for a few days. When i boot up the pc i get two options windows 7 and Ubuntu. When i select windows it works fine. When i select Ubuntu it gives me a minimum edit utility and the prompt just says grub> i have tried serveral commands but it does not take any of them. Unknown command. Earlier i used to get four options within ubuntu for some kernels and i used to select the first option. But this is strange. I have tried to boot with windows 7 dvd and fix mbr and boot but does not work. I booted to ubuntu cd and in terminal i tried setup, root, find list 1 etc commands none of them work. i searched the entire forum but no go. the screen says i am using some grub lubuntu 0-98 or something like that at the top.  the only changes i have made to ubuntu since i have installed is some security fixes which automatically popped up. Audio video codecs, Kbuntu desktop as i liked the interface. Default boot manager was selected as Gnome. Please help. what do i need to do now?
thats because you installed it using WUBI, which is prone to NTFS corruption

---

