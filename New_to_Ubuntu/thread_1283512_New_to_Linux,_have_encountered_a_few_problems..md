---
title: "New to Linux, have encountered a few problems."
date: 2009-10-05
forum: New to Ubuntu
---

### Post by bob1105 on 2009-10-05
I have just installed ubuntu linux 9.04 on my Lenovo Ideapad y650. The specs of my computer are intel core2duo p8700 @ 2.53 GHz, 4gb ddr3 ram, and an Nvidia GeForce G 105M. Wireless, bluetooth, cd-rom, and all other components seem to be working fine except for my laptop monitor. My screen resolution is a maximum of 1366 by 768, but in the display settings I am only seeing the maximum option for 1280 by 720. I am very adept at general windows usage and decently adept with macbooks, but I have no prior experience with Linux. I did several google searches to try to remedy my problem but none were helpful and all seemed very convoluted/ to advanced for my current Linux knowledge. I tried to go to the terminal and use xrandr to change the settings but I couldn't get it to work. Is there anyway someone can help me out with a step by step simple tutorial of how my problem can be fixed? If anyone could I would be much obliged. Oh and on a side note if you could also include a tutorial on how to install compiz so I can have windows aero type graphics I would be the happiest guy in the world. Thanks in advance.

---

### Post by Temposs on 2009-10-05
I'm not sure about your resolution problem, but I can help you with the compiz part perhaps.

Compiz is in fact installed by default on Ubuntu. There is a simplified interface to enable a limited number of features. To activate the Compiz features, you should go to System->Preferences->Appearance, then click the Visual Effects tab. Choosing "None" here deactivates Compiz. The other two options activate different levels of Compiz features.

If you would like to play with all the features of Compiz, go to Applications->Add/Remove, and search for "ccsm". You should get one result, Advanced Desktop Effects Settings. Check it, click Apply a couple times, and it will install. Once installed, go to System->Preferences->Advanced Desktop Effects Settings. You can then play around with all the great effects that are possible in Compiz.

---

### Post by HarrisonNapper on 2009-10-05
Also, make sure your restricted driver for your nvidia card is installed and selected in System>Administration>Hardware Drivers

P.S. Once you've enabled the new driver, you may have to restart X or even the computer. You can restart X with Ctrl-Alt-Backspace or you can just do a full restart. Happy *nixing!

---

### Post by Temposs on 2009-10-05
> **HarrisonNapper said:**
> P.S. Once you've enabled the new driver, you may have to restart X or even the computer. You can restart X with Ctrl-Alt-Backspace or you can just do a full restart. Happy *nixing!

Ctrl-Alt-Backspace is not enabled in Ubuntu 9.04 by default. It won't work unless you set the keybinding.

---

### Post by HarrisonNapper on 2009-10-06
Oh, well in that case, full restart for the win!

---

### Post by AGeorge on 2009-10-19
I just got my Y650 and was thinking of installing Ubuntu and then installing Vista via VirtualBox.  I would like to use all the default features such as the touch sensitive strip from w/in Vista but wasn't sure if Ubuntu would have drivers for them.  Let me know if anyone has gotten it to work?

---

### Post by punkybouy on 2009-10-19
ctrl+alt+backspace works fine on my 9.04 64 bit to log out and I did not have to enable anything.

---

### Post by p0cky84 on 2009-10-19
> **HarrisonNapper said:**
> Oh, well in that case, full restart for the win!

Actually, you only need to restart your X session ;P

---

