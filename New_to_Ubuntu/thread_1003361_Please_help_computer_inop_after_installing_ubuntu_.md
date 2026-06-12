---
title: "Please help computer inop after installing ubuntu :("
date: 2008-12-06
forum: New to Ubuntu
---

### Post by dannistim on 2008-12-06
just installed Ubuntu on my desktop following prompts just like I did for my laptop which went fine. This time there are two problems: 1, I can no longer boot windows, it just hangs. 2 the first time I restarted it after downloading updates it said there was a display conflict then rebooted in plain text mode. There is no obvious way to fix it from the command line if you're new. Also help is less than useful because unlike man it scrolls off the page. The installation disk is less than useful for recovery only offering to further partition the existing ubuntu partition our use the whole disk. an option to just reload ubuntu would've been nice. I tried booting in safe mode and clicking on all the fix it options but it still boots in text mode. Grump.

---

### Post by nhasian on 2008-12-06
see if this will fix your ubuntu.  type this in a terminal prompt:

```
sudo dpkg-reconfigure xserver-xorg
```

as for windows, do you get the windows splash screen and then it hangs or what?

---

### Post by dannistim on 2008-12-06
no screen just goes black and stays that way with no hard drive action

---

### Post by dannistim on 2008-12-06
input that command and it still boots up in text mode after showing the graphical splash screen and shuts down with same screen so graphics are possible but aren't happening for some reason. CD boots fine and that's how I'm writing this.

---

### Post by dannistim on 2008-12-06
I tried both the yes answer and no answer on the xserver question in the menu that pops up. neither made any difference.

---

### Post by 3rdalbum on 2008-12-06
> **dannistim said:**
> I tried both the yes answer and no answer on the xserver question in the menu that pops up. neither made any difference.

It should ask you multiple questions. When you are asked about video card autodetection, go to NO and specify the "vesa" driver. When asked about monitor autodetection, go to NO and then "simple" method of specifying monitor. If the "simple" method doesn't work, then go through the process again and try the next method.

Remember to restart after changing the configuration each time:

```
sudo reboot
```

---

### Post by Elfy on 2008-12-06
That command doesn't work for video anymore, boot with the recovery mode option.

When you reach the small menu - choose the xfix option, then resume.

---

### Post by dannistim on 2008-12-06
I never got an option for the vesa it was all about the keyboard after the first question. ok i did the xfix then resume from protected boot mode and is still boots in text mode. what now????? I'm very discouraged. I found out what caused this though. I used brute force and did a clean install over everything blowing away windows and the previous ubuntu and everything works GREAT until I activated the "recommended" 97 nvidia driver and rebooted. Before I'd done so many things I had no idea what caused it. this time it was the only thing different. It hung on reboot for ~ 20 min then finally shut down just like last time and now is the same as before. doing the xfix then resume gave me a nicer looking text terminal. typing 
sudo gnome-session -failsafe 

gets me the error message

** (gnome-session:5750): WARNING **: Cannot open display:

the fancy splash screen appears at both boot and shut down.

---

### Post by dannistim on 2008-12-17
This is sort of solved in that I was able to do a fresh install and get my system up again and know not to use the 96 nvidea driver, but serious questions remain. I checked for the exact number of the damaging one once I got Ubuntu re-re-reloaded which is 96 NOT 97 as I guessed earlier. Sorry. The other one, 173, only sort of works but at least it doesn't break the windowing system (permanently?). I still must run xfix in recovery mode after doing anything in the Nvidea X server settings window or I get error messages and 5 -10 minute freezes when trying to log out. It is not solved in that nobody could figure out how to fix the windowing system once it was broken with the 96 driver. It is not solved in that there is a damaging driver still being downloaded. It is not solved in that this damaging driver is marked as the recommended one!

---

