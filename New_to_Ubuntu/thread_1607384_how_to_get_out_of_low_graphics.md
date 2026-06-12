---
title: "how to get out of low graphics"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by dbowlin17 on 2010-10-27
I am in the low graphics mode. not sure why. doesn't detect my display. it did detect it before, but after the machine froze one day and i powered down by holding the power button, it won't start with regular full graphics anymore. im running 8.04 cause thats the newest that works on my laptop.

---

### Post by ivarn on 2010-10-27
Ok so what did you do (installed / removed) before this happened?
Also, what graphic card do you use? NVIDIA?
If you don't know the answer of the first question go to recovery mode, root prompt and type the command:
sudo --fix-missing, followed by sudo apt-get update.
Now if you use NVIDIA graphic card, type this command:
*sudo nvidia*-*xconfig to right a new xconf file for your card.*

---

### Post by sikander3786 on 2010-10-27
> sudo --fix-missing

It doesn't do any thing. This one is new to me.

To the OP: You need to provide more details as mentioned by **ivarn**. Graphics card and driver version in use at least.

---

### Post by ivarn on 2010-10-27
it's the command you run to fix broken packages.
SOmething is obviously wrong with his gui somehow.

---

### Post by dbowlin17 on 2010-10-27
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller 

Thats my graphics card. I didn't make any changes. Someone had flipped the screen orientation on me and i was trying to fix it. then the computer locked up so i did a hard power down and restarted to this issue. does this fix missing command work with 8.04 or work at all, as someone had never heard of it? im not sure what to do...

---

### Post by ivarn on 2010-10-27
see if the repair function in recovery mode can help you out.
But now when this guy says fix missing is new to him, I'm not sure if it's fix broken or whatever. anyway. if the repair function in recovery doesn't work try to install ubuntu-desktop again.

---

### Post by sikander3786 on 2010-10-27
> sudo --fix-missing 

It is not doing anything on my system. I believe what you were talking about is

```
sudo apt-get install -f
```

However the OP doesn't really need to do that.

To the OP: Backup your xorg.conf by

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Delete the original one,

```
sudo rm /etc/X11/xorg.conf
```

And then try to reconfigure your graphics,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot to see if it worked. If it didn't, boot into Grub recovery mode by holding down the Shift key at startup and select 'Reconfigure Graphics' or something like that.

---

### Post by dbowlin17 on 2010-10-27
I tried before seeing anything, and i got to the recovery mode and selected repair broken packages. now i can select the resolution i had before, which works for me. while it still doesn't detect the screen like it did before, its better than it was... thanks

---

