---
title: "Splash Screen"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-05-27
Is there any way to make the splash screen stay up for like 10 seconds instead of just 2 seconds?

---

### Post by doas777 on 2009-05-27
ok, use Alt + F2 to bring up the run bar, and paste in:
```
gksu gedit /boot/grub/menu.lst
```

then look down a few lines, for the word "Timeout" and change the value after it to 10

also i think you can control it with a gui in StartUp Manager. you should find it in synaptic or use : ```
sudo apt-get install startupmanager
``` and then you will find it in the system->administration menu.

have fun

---

### Post by hifly1231 on 2009-05-27
> **doas777 said:**
> ok, use Alt + F2 to bring up the run bar, and paste in:
```
gksu gedit /boot/grub/menu.lst
```

then look down a few lines, for the word "Timeout" and change the value after it to 10

also i think you can control it with a gui in StartUp Manager. you should find it in synaptic or use : ```
sudo apt-get install startupmanager
``` and then you will find it in the system->administration menu.

have fun

Actually, I was talking about the Splash Screen that comes up after the Boot Screen.  I've installed "Splash Screen", but the Splash Screen only stays up for like 2 seconds while the login sound is playing.

---

### Post by zeroseven0183 on 2009-05-27
Now that's too fast. Try other bootsplash to see if there are any differences. But I think it depends on how fast your computer is.

---

### Post by doas777 on 2009-05-28
> **hifly1231 said:**
> Actually, I was talking about the Splash Screen that comes up after the Boot Screen.  I've installed "Splash Screen", but the Splash Screen only stays up for like 2 seconds while the login sound is playing.

when you say "boot screen" do you mean the bios splash screen, or the Grub menu?

---

### Post by listerdl on 2009-05-28
i have a sort of similiar issue that I am unable to remove the text starting -

---

### Post by hifly1231 on 2009-05-28
Not the Grub Menu, not the Boot Screen (with Ubuntu and the loading bar), but the Splash Screen that comes up afterwards and the login song plays.  I can only get a .png Splash Screen to stay up for like 2 seconds.  It comes on, then disappears, and again all I have is the black screen with the taskbars on top & bottom.

---

### Post by doas777 on 2009-05-28
> **hifly1231 said:**
> [quote=doas777;7362314]when you say "boot screen" do you mean the bios splash screen, or the Grub menu?

Not the Grub Menu, not the Boot Screen (with Ubuntu and the loading bar), but the Splash Screen that comes up afterwards and the login song plays.  I can only get a .png Splash Screen to stay up for like 2 seconds.  It comes on, then disappears, and again all I have is the black screen with the taskbars on top & bottom.[/quote]

ahh. i know what you mean. I've never been able to do anything about it except change the color. do you have any autostart items that use gksu? I've found that that makes it worse. 

one thing to try; wait 20 seconds before launching some of your auto-start apps (just add `sleep 20;` to the begining of the command, or create a script) so that the desktop loads before the user apps load. just a thought. you may also be able to speed it up if you statically configure your network, and dump network-manager. 

good luck

---

### Post by hifly1231 on 2009-05-29
> **doas777 said:**
> ahh. i know what you mean. I've never been able to do anything about it except change the color. do you have any autostart items that use gksu? I've found that that makes it worse. 

one thing to try; wait 20 seconds before launching some of your auto-start apps (just add `sleep 20;` to the begining of the command, or create a script) so that the desktop loads before the user apps load. just a thought. you may also be able to speed it up if you statically configure your network, and dump network-manager. 

good luck

OK, are you telling me that I can change the color of the Splash Screen?  I can forget about having a .png come up, but I really don't like the black screen with the taskbars in Jaunty Jackalope.  I would prefer the beige screen in Intrepid Ibex.

---

### Post by doas777 on 2009-05-29
> **hifly1231 said:**
> OK, are you telling me that I can change the color of the Splash Screen?  I can forget about having a .png come up, but I really don't like the black screen with the taskbars in Jaunty Jackalope.  I would prefer the beige screen in Intrepid Ibex.

the black is the system default color (in previous versions it was brown, far more annoying IMO) and is displayed "under" the splash, so that when the splash closes, it is displayed for a few seconds.

check out this article on how to change it. the article is based on feisty or hardy so the color used is going to be different (#000000 for black). 
[http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html](http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html)

good luck

---

