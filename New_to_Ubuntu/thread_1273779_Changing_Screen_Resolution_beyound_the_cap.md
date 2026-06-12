---
title: "Changing Screen Resolution beyound the cap"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by GenDeath on 2009-09-23
Hello
I finally made the leap to ubuntu(YAY!)
and im having an issue with the screen res I want it to be like 1024x800 but it saying only 800x600
I am used to a larger resolution than that idc how small things will look its what I want because I love the multi tasking and I just cant on such a small resolution

Yes I am the administrator

Thank you so much
~The General

---

### Post by paultag on 2009-09-23
Hey man.

Are you using the correct driver for your card?

please output `lspci`, and then we can work from there :)

---

### Post by GenDeath on 2009-09-23
Alright im going to attach it because its really long

---

### Post by paultag on 2009-09-23
OK. You have a GeForce 7000M. You need the nvidia-glx package. I think `sudo apt-get install nvidia-glx-180` should work for that card.

---

### Post by GenDeath on 2009-09-23
kk installing atm thx
ill reply with results asap

---

### Post by GenDeath on 2009-09-23
Ok i don't think its working
See attached

---

### Post by paultag on 2009-09-23
can you paste the log of the install?

Did you restart, as well?

---

### Post by GenDeath on 2009-09-23
How do i do that?
and yes I did first thing

---

### Post by paultag on 2009-09-23
Ah. Can you try re-running that install line, and then paste the output from that command?

There is a chance you need the kennel headers as well

---

### Post by GenDeath on 2009-09-23
After rerunning it heres what i got

[INDENT]Censor@Censor-laptop:~$ sudo apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-180 is already the newest version.
The following packages were automatically installed and are no longer required:
  sharutils debootstrap bochsbios vde2 vgabios libvdemgmt0 libvdeplug2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 117 not upgraded.
Censor@Censor-laptop:~$ [/INDENT]

---

### Post by paultag on 2009-09-23
howabout `sudo depmod`

---

### Post by GenDeath on 2009-09-23
doesn't do anything
just starts a new line

and srry hadn't noticed we went to second page

---

### Post by paultag on 2009-09-23
can you send the output of `lsmod | grep nvidia` ?

---

### Post by GenDeath on 2009-09-23
nvidia               7233756  0 
agpgart                42696  1 nvidia

---

### Post by paultag on 2009-09-23
try `sudo nvidia-xconfig` and restart :)

---

### Post by GenDeath on 2009-09-23
Error
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by paultag on 2009-09-23
Looks OK. Give a restart and retry setting the screen resolution

---

### Post by GenDeath on 2009-09-23
WOW it works you Rock!
TYVM!

---

### Post by paultag on 2009-09-23
You got it.

Have fun with Ubuntu :)

---

