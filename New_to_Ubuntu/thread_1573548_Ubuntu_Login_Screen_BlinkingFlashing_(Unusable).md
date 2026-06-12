---
title: "Ubuntu Login Screen Blinking/Flashing (Unusable)"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by snarkozard on 2010-09-12
Specs
System Manufacturer: Dell Inc.
       System Model: Studio 1749
               BIOS: Ver 1.00 A04
          Processor: Intel(R) Core(TM) i5 CPUM 520 @2.40GHz
             Memory: 4096MB RAM
Available OS Memory: 3956MB RAM
Card name: ATI Mobility Radeon HD 5650 

Preview
I was attempting to install a game called Leges Motus from freshmeat.net. [http://freshmeat.net/projects/leges-motus](http://freshmeat.net/projects/leges-motus) or [http://legesmotus.endrift.com/index.php/Main_Page](http://legesmotus.endrift.com/index.php/Main_Page)

It had me install several libraries, a few SDL ones, which I don't think are the problem, and then I needed openGL installed. I did so, and still something was going wrong with the installation. I had to redirect of the config files to /etc/X11/ instead of /usr/X11 (I don't know if that means anything, but there it is). I decided to restart and then give the game a try again. As I was starting to restart, the computer started freezing up, and I had to manually shut it down.

Now whenever I try and start Ubuntu, the background to the login screen appears, but there is only a flashing white area where the login should be, and a flashing white line on the bottom. 

I tried a few things I found online, like reconfiguring xserver-xorg, and some other things, with no luck, so here I am!

Thanks

---

### Post by snarkozard on 2010-09-13
Bump?

---

### Post by v1ad on 2010-09-13
on the grub menu boot into fail-safe mode, and drop to root shell.

remove the stuff you installed, and see if that will do it. if you don't know which onces and need to see what is installed type in " aptitude " and it will give u a display where you can pick what you want to remove.

---

### Post by snarkozard on 2010-09-14
I deleted every single package that I installed that day, except for mountall and xulrunner-1.9.2, and it still doesn't work. Those two had important dependencies, so I figured deleting them would be bad. 

No change to the blinking login screen. Any other help or do i have to clean install?

---

### Post by snarkozard on 2010-09-14
Shameless bump.

---

### Post by Greywhind on 2010-09-17
From your description of the problem, it sounds like you might have installed a buggy version of your graphics drivers somehow. Are you using ATI? It seems like those drivers often have problems.

Try switching your X session to use a non-proprietary graphics driver if you're using the proprietary version, or vice versa, and see if that changes anything.

---

