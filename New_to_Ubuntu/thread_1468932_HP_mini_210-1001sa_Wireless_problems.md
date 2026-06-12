---
title: "HP mini 210-1001sa Wireless problems"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by tonycobb on 2010-05-01
Good evening,
I have just brought a HP mini 210-1001sa which I wanted to put 10.04 desktop.
It installed OK but I can't get the wireless to work.  Everything else appears to work OK.

After a lot of searching I was told to install 9.04 desktop instead which I did and the wireless card works fine but no sound. I upgraded at 9.10 and once again the wireless card did not work.

What I would like to know is can I get the wireless card to work on 10.04 desktop? if not how to get sound in 9.04

Many thanks for any advice given

Tony

---

### Post by anewguy on 2010-05-01
Please open a terminal window (applications/accessories/terminal), then do the following:

type:

lspci <press enter>

lsusb <press enter>

lshw -C network <press enter>

copy and paste the output from each of those back here.

Dave ;)

---

### Post by AlanR8 on 2010-05-01
I have the Compaq version of your machine. Everything just worked ou of the box!

Go into System/Administration. Hardware Drivers and make sure you have the right network driver installed and set up. That might mean changing the selected driver. I seem to remember that's what I had to do.

---

### Post by tonycobb on 2010-05-04
Many thanks for your help.
 
I have managed to get the wireless working on 10.04
 
I went into System/Administration. Hardware Drivers and disabled the Broadcom driver and then enabled it and did a reboot. 
 
Many thanks
 
Tony

---

### Post by lotharmat on 2010-05-04
Don't forget to mark the thread as solved using the thread tools above!

---

