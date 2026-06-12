---
title: "How to install alsa hda-intel sound driver?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-06
OK, I have tried two sound post and now I just need to install the driver. It's an hda-intel alsa driver (if that will help) and I have tried two post because my sound just stopped working in intrepid. this is what I get when I type aplay -l in a terminal: aplay: device_list:215: no soundcards found...

Any help?

---

### Post by Titan8990 on 2009-01-06
Try running:

sudo alsaconf

to see if it detects your card. The hda intel sound drives are modules that come with the default kernel. Do you have a custom kernel?

You can also report the results of:


lsmod | grep intel

---

### Post by taylor102387 on 2009-01-06
taylor@Taylor-laptop:~$ sudo alsaconf
[sudo] password for taylor: 
sudo: alsaconf: command not found
taylor@Taylor-laptop:~$ lsmod | grep intel
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp



HELP!!!!!!!

---

### Post by tornado89 on 2009-04-23
Better late than never

you can try to use the module-assistant:

sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant

and then choose alsa and build then install...

YOU MUST RESTART after the preceeding steps

i had exactly the same problem as yours and this fixed it

hope it helps....

---

