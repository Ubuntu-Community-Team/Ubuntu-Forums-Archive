---
title: "karmic wont install, and unable to run after upgrade"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by techno-mole on 2009-12-30
hello.

I'm not sure what could be causing this problem, but I'll try and explain it.

I have tried to install karmic on one of my kids pc, I used the cd I burned when I installed it on my system, but it was very slow, and it got to a point and then just stopped, the last bit of the message I caught was something like " purging files for gdm session " ? or something like that, and then the monitor lost its signal, like the lead had come out.

I tried numerous times, and even tried using the safe graphics mode, and still the same issue, not idea what it is though, its almost like the system doesn't have the power to carry on, it was running intrepid by the way.

So I decided to install jaunty and then upgrade, the jaunty install went fine, and the upgrade to karmic went fine, no apparent errors, until I rebooted that is, and then I had the same problem as before, like the power had been cut and I also got the vague message regarding purging the gdm session files.

any ideas ? as I would like to upgrade the system in question to karmic, but a fresh install so as I can upgrade the file system to ext 4.

cheers in advance for any help.

---

### Post by jbrown96 on 2009-12-30
Could you describe what's happening when the GDM error messages show up? Is it after the loading screen, before/after login, etc? What does the screen look like (has X started)?

It would also be helpful to know your hardware. If you can get into Jaunty (via Live CD), then run ```
lspci
``` in a terminal and post the output here. 

If you have access to an ethernet connection then you can try to upgrade from the terminal.
1) Install Jaunty and run all the updates that are available, but don't upgrade to a newer version. 
2) Reboot and don't log in (or logout if you have auto-login enabled).
3) Ctrl+Alt+F2 to switch to a virtual console and log in.
4) Upgrade to Karmic ```
sudo apt-get update && sudo apt-get dist-upgrade
```
5) Once the upgrade finishes, then ```
sudo reboot
```

---

### Post by jbrown96 on 2009-12-30
Didn't want to edit my last post. I saw that you want a clean Karmic install for ext4. 

When you tried a clean install were those "purging" messages during install or after a reboot?

You may also have a bad CD. When you first choose the Live CD, try checking it for defects. I'm leaning towards that since you seem to be having problems on multiple computers.

---

### Post by techno-mole on 2009-12-31
I did try installing jaunty and then running the upgrade manager, but ran into the same problem.

basically when trying to run an install i get as far as the ubuntu logo that flashes white when booting up.

so it goes like this - 

boot from cd (karmic cd, which worked on my system, and my wifes)

select english,
then select install ubuntu 
then the screen goes to the little white ubuntu logo and thats as far as it gets, I then get the purging message ?

the monitor then goes off, and I get the message on the monitor that there is no signal.

the same thing happened after installing jaunty and trying the upgrade, the upgrade went fine, no errors, but when it came to rebooting I got the same problem.

I did try to run the live cd, with out installing, but again got the same problem.

I don't know what help running lspci from a jaunty live cd would do to be honest, I can tell you whats plugged in.

a via sound card, and an nvidia agp graphics card, and thats it, surely if there was an error with the hardware then jaunty wouldnt run either ?

I did also try running the disc checking feature, it came up with no errors, I also tried burning new discs ( I did 2) and I also ran the disc check on those and got no errors.

I am a little puzzled to say the least.

I should say that last night I installed jaunty on the system and it works like a charm, no errors, no strange gdm purging messages, it installed pretty quickly and runs a fair bit faster than intrepid did.

the system specs of the system in question are as follows - 

2gb ram
amd athalon cpu (I forget the model, but it runs at 2.2ghz)
256mb agp graphics card (nvidia)
2 sata hard drives, one for ubuntu and the other runs xp (dual booting, as we do with all the other systems in the house)
via sound card

---

### Post by jbrown96 on 2009-12-31
Try booting without the splash screen. I had a problem with this on my AMD HTPC with 9.10. You can do this with the installed version or the live cd.

Installed:
Since it's dual-boot, then you should get a grub menu. Highlight the newest kernel and press "e". This will take you to a screen that you can edit. There's one line that's really long and has "splash" in it. Change that to "nosplash" and then follow the instructions at the bottom to boot. 

Live CD:
Once you choose the language, do not boot. There should be an option like F4 for "more options"; choose that then go to the end of line and find the "splash" part and change to "nosplash."

What errors do you get?

---

### Post by techno-mole on 2010-01-27
it seems that in the end there were 2 bits of hardware causing issues, firstly the dvd drive was playing up, and secondly the graphics card was playing up as well, although the card itself is fine it wasnt getting enough power for the psu, which to be honest isnt a good one.

so for now i am using an old fx5200 agp card in the system and karmic is now installed, will be ordering a new psu for the system as the other card is much better.

cheers for the help.

---

