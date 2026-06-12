---
title: "urgent help needed with eee easy peasy"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by djzoid on 2009-08-07
hi, my eee 900 with easy peasy has almost given up! im not sure what actually happened but it has probably got something to do with running compiz fuzion, synaptic, amarok and browsing the net at the same time.
i was thinking that i should get rid of compiz because it was making my poor little eee run really hot so i tried to open the terminal and it didnt open, next i tried to use synaptic and that wouldnt open either although the net and amarok were still running fine. so i went for a restart.....it got past the easy peasy loading screen (with the lemon) and went black. im not sure it has anything to do with the gpu because the pointer still showed up and worked and i could fn F5 to open the task manager.
 
so im thinking perhaps i could use my uncles vista box to create a live usb cd (eee doesnt have cd drive), how would i go about doing this? i couldnt find any posts to do this as this is a ubuntu forum heh. if i just missed a thread plz link it!
 
TIA!
 
:D
 
edit:well, okay i can find a way of making a live usb in vista but is there a fix for my problem which doesnt require me going out and buying a new usb stick?
edit2: ive just been looking into the vista live usb cd dual boot and it seems i have to edit partitions in vista computer....i dont want to do this, i just want to be able to make the live cd in a usb stick, still need help!!! (i know three exclamation marks are a sure sign of madness)

---

### Post by thezood on 2009-08-07
> **djzoid said:**
> hi, my eee 900 with easy peasy has almost given up! im not sure what actually happened but it has probably got something to do with running compiz fuzion, synaptic, amarok and browsing the net at the same time.
i was thinking that i should get rid of compiz because it was making my poor little eee run really hot so i tried to open the terminal and it didnt open, next i tried to use synaptic and that wouldnt open either although the net and amarok were still running fine. so i went for a restart.....it got past the easy peasy loading screen (with the lemon) and went black. im not sure it has anything to do with the gpu because the pointer still showed up and worked and i could fn F5 to open the task manager.
 
so im thinking perhaps i could use my uncles vista box to create a live usb cd (eee doesnt have cd drive), how would i go about doing this? i couldnt find any posts to do this as this is a ubuntu forum heh. if i just missed a thread plz link it!
 
TIA!
 
:D
 
edit:well, okay i can find a way of making a live usb in vista but is there a fix for my problem which doesnt require me going out and buying a new usb stick?
edit2: ive just been looking into the vista live usb cd dual boot and it seems i have to edit partitions in vista computer....i dont want to do this, i just want to be able to make the live cd in a usb stick, still need help!!! (i know three exclamation marks are a sure sign of madness)

Maybe you can avoid messing with a Live USB stick. Try pressing CTRL-ALT-F1. If it takes you to a terminal, you can disable Compiz by logging in and typing the following:
```

killall compiz.real
killall compiz
metacity --replace

```
Press CTRL-F7 to return to X-windows. If it still doesn't work, try restarting X:
```
sudo /etc/init.d/gdm restart
```
Also open the Appearance settings and change to the lowest effect setting.

---

### Post by djzoid on 2009-08-07
thank you very much! im at work at the moment, so i'll just have to try it tonight when i get back.

---

### Post by tarps87 on 2009-08-07
If you do need to make an install USB have a look here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just install it on vista point it to the live cd an to a USB stick

---

### Post by djzoid on 2009-08-07
just tried your advice, thezood, when i run the command "metacity --replace" it comes up with "window manager error: unable to open x display" :confused: 
 
i suspect im now playing a dangerous game but i "apt-get remove" ed compiz. didnt really think that one through so ive probably caused more problems for myself. my situation doesnt seem to have changed though im still stuck at some sort of loading screen (still black) when i press the power button it shuts down which is something.
 
any more ideas would be greatly appreciated!
 
also thank you tarps for the link i didnt realise unetbootin could be used in vista cos im a douche.

---

### Post by djzoid on 2009-08-11
well i installed jaunty so the problem is gone, first thing i did was remove compiz to avoid problems and unnecesary cpu usage. if anyone else had this problem i would be curious to see a fix and so i can understand my system a bit better. or admin can remove this thread as it's basically useless otherwise!

---

