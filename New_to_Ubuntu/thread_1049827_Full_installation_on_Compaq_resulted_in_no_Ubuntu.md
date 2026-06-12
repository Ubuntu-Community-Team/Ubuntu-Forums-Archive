---
title: "Full installation on Compaq resulted in no Ubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by zaivala on 2009-01-25
I have tried 5 times now to install Ubuntu on my best friend's Compaq Presario (about 4 years old, 3.2 GHz Celeron).  This last time we took the plunge and did a full install of 8.10, complete with GRUB (previous installation attempts were using WUBI).

It reported that the installation was complete, and that we needed to reboot.  GRUB works fine... and it didn't mess up the Windoze partition (like it repeatedly did on my HP Pavilion a1020n until I used WUBI)... but when we boot to Ubuntu, we get all the right noises... the bar scrolling from side to side... the tan screen... and then a black screen, and nothing more. We have waited 20 minutes, an hour... still no Ubuntu Gnome Desktop.

What can we do from here?

We have tried installations with 8.04 and 8.10, with the same effect no matter whether we use GRUB or WUBI.

---

### Post by taurus on 2009-01-25
What kind of graphic card does it have?  Try booting into recovery mode from GRUB menu and pick the fix X server option.

---

### Post by zaivala on 2009-01-25
> **taurus said:**
> What kind of graphic card does it have?  Try booting into recovery mode from GRUB menu and pick the fix X server option.

We'll try that... all graphics are on the motherboard, which I believe is Intel.

Moss

---

### Post by taurus on 2009-01-25
I also have one of those Intel integrated graphic controllers on a dell optiflex 620 in the office and intrepid didn't have any problem installing and running it.

---

### Post by zaivala on 2009-01-25
I have an HP Pavilion a1020n, and it has software which detects any changes to the MBR (such as GRUB), and required me to restore the software (Windoze) from scratch...  Mike's Compaq didn't have that problem, but it is having the problem noted.  This is a Presario SR1103WM, if that helps any.

---

### Post by zaivala on 2009-01-25
The motherboard may NOT be Intel... the Compaq/HP website calls it MIS name: MS-6577 M-ATX Rev. 3.1 (Giovani), Rev. 4.0 (Giovani2).  But it has an Intel 845GV graphics chip.

---

### Post by anewguy on 2009-01-25
When the black screen comes up on boot (unable to get into x windows) hold ctrl/alt and press F1.  That will bring up a terminal window.  Log on with your username and password.  At the prompt after login, type:

lspci  <press enter>

Post the output of that back here and we can try to go from there.

Dave :)

---

### Post by pagmatic on 2009-01-25
> **anewguy said:**
> When the black screen comes up on boot (unable to get into x windows) hold ctrl/alt and press F1.  That will bring up a terminal window.  Log on with your username and password.  At the prompt after login, type:

lspci  <press enter>

Post the output of that back here and we can try to go from there.

Dave :)

I'm the one with the problem. 

here's what I got after all your instructions

pagmatic@pagmatic-desktop:$ 

I typed in lspci again; but got the same prompt.


(my login is "pagmatic")

---

### Post by anewguy on 2009-01-25
It should have output some data before returning to the prompt.  If not, try sudo lspci <press enter>.  Post the output from that back here.

Also, post back the exact model, etc., of your pc.  We might be able to find what type of video it is using from that (via the HP/Compaq support site).

Once we know the video chipset being used we can work on getting you a working driver.  It may mean running envyng from a terminal prompt to let it install the driver, but we need to see the chipset 1st.

Be aware we aren't looking for it to be windowed yet - we are just trying to find the video adapter type so we can find a driver for it and help you load it.

Dave :)

---

### Post by zaivala on 2009-01-26
Sorry for the tag-teaming... the model is a Compaq Presario SR1103WM.  The motherboard specs are to be found at
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00063244&lc=en&dlc=en&cc=us&lang=en&product=424182](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00063244&lc=en&dlc=en&cc=us&lang=en&product=424182)

Moss

---

### Post by zaivala on 2009-01-26
Mike:

Try typing sudo lspci

Moss

---

### Post by anewguy on 2009-01-26
From what I've been able to find on the net, it would appear that if you are using the integrated graphics, it is intel i845.  The driver shown on the compaq support site is the intel extreme graphics driver.  I believe I remember seeing the i845 handled in several posts here on the forums.

I personally haven't had to work with the i845, so I don't have the experience you need with that.  I would suggest doing a search function in this forum and put in i845 graphics driver and see what comes up.

There should be others that can help you with the specifics, if not, I'll check back.

Dave :)


EDIT:  What would probably work best is to (1) close those thread and (2) open a new thread with "integrated Intel 845G graphics driver needed" as the title - you'll get a lot more help that way!

---

### Post by anewguy on 2009-01-30
Sorry it took so long to get back to you.  I found another post with the same symptoms with the same IGP.  It was claimed there that somehow the i845 IGP and compiz don't cooperate with each other, and they did the following in a terminal window and then rebooted:


sudo apt-get purge compiz compiz-core


Try that and see if it works for you.

Dave :)

---

### Post by abn91c on 2009-01-30
> **anewguy said:**
> Sorry it took so long to get back to you.  I found another post with the same symptoms with the same IGP.  It was claimed there that somehow the i845 IGP and compiz don't cooperate with each other, and they did the following in a terminal window and then rebooted:


sudo apt-get purge compiz compiz-core


Try that and see if it works for you.

Dave :)
you are correct ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

