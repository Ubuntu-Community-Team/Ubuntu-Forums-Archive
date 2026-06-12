---
title: "need help with USB - SOMEONE PLEASE HELP!"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by evil_queen_lisa on 2009-07-28
Hi everyone,
I'm sure that someone will tell me that there is an answer to my questions here somewhere, but I just can't find it!
1st of all - The reason I installed Ubuntu is to be able to use MythTV. I am having an issue with my TV tuners and USB.
Problem A: I installed my PCI tv tuner, but I can't / don't know how to get it to mount in Ubuntu. I can't get it to work in MythTV - I scan for channels but it finds nothing.
Problem B: I have a USB tuner for my laptop that I know works, so I wanted to try it with Ubuntu. I also can't/don't know how to get it to mount. It will show up when I use lsusb - but I can't seem to get MythTV to detect it/use it. Also, the light on it does not light up (usually the light goes on when it has power).
I tried to install the autofs thing that I saw people talking about; but i'm afraid that I may have failed (not even sure how to tell sadly!)

I'm feeling rather incompetent! Give me Windows and I don't need a manual for CMD; and I can hold my own in MacOSX - yet I seem to be failing miserably in Linux! I have read the free guide and everything, googled, but I am getting frustrated and considering just removing Linux and going back to the dreaded Windows!!

Someone PLEASE HELP ME!
thanks,
*EQL*

---

### Post by llamabr on 2009-07-28
Maybe this is a question you ought to take to the mythtv forum.

---

### Post by corevalue on 2009-09-10
Lisa

I'm opening a new topic on USB. One of my problems was that I installed a Pinnacle 72e USB stick, which worked fine, until I rebooted. After a reboot, although it was correctly detected (from messages in dmesg), it would not work, until I completely removed the player (kaffeine) and all it's components, and re-installed. Then it would work again.

Try this: you have already installed your application (MythTV). In dmesg you should see something like 

"(your USB TV stick name) found in a warm state...."

Remove the tuner stick. Reboot with it out. Plug it in after booting and see if your TV works. This works for me on my Pinnacle stick.

---

