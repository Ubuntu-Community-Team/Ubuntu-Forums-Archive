---
title: "Kubuntu Hangs On Boot"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Maleificus on 2010-05-08
Hello,

I just activated the proprietary driver for my graphics card. Upon boot it shows a bunch a errors that I can't read because it scrolls to fast (i don't know if they are ALL errors because it scrolled too fast) and then it goes to a screen like the attached picture (but not as streamlined. I am guessing that the resolution is off.) and just hangs there. Every once in a while I can see some hard-drive activity. I let it sit for about five minutes before pressing the restart button and booting into Windows 7. Does anyone have any idea what is going on here?

---

### Post by dracayr on 2010-05-08
can you boot in recovery mode/safe graphics mode? if yes, you can probably check the errors in /var/log/boot.log
what happens when you boot with nosplash? (in the boot menu, press e while the kernel is selected, select the kernel line, press e again, and change the 'splash' at the end of the line to 'nosplash'. press enter and then b.)
Can you read the errors then?

dracayr

---

### Post by Maleificus on 2010-05-08
No I can't boot in safe graphics mode, however I will try the nosplash boot after I go to sleep. Thank you, I will let you know if it works.

---

### Post by Maleificus on 2010-05-08
No, that did not help. First off there is no second time that I can select the kernel, second after I put nosplash at the end of the line and press enter, and then b, it just makes another line and puts the letter b there. If it helps any I am using Kubuntu 10.04.

---

### Post by Zorael on 2010-05-08
With Grub2 (that lucid users), you don't hit B but rather Ctrl+X to execute the entry.

---

### Post by Maleificus on 2010-05-08
Okay I have re-installed Kubuntu. However, when I tried to install my proprietary driver for my graphics card and reboot, it hung on boot again. So I did ANOTHER re-install. Now I am waiting to install that driver to see if anyone on here has any input on what I should do prior to installing that driver so that my graphics can stop being so laggy...but I can still boot.

---

### Post by Maleificus on 2010-05-09
If it helps any I am trying to activate ATI/AMD proprietary FGLRX graphics driver.

---

