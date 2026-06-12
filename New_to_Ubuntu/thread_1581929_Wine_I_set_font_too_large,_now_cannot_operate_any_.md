---
title: "Wine: I set font too large, now cannot operate any of my wine-related programs"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by swarup on 2010-09-25
My colleague has poor vision and the font was very small in the two programs he has running in wine. So he went into Wine -> Configuration and found a way to globally increase the font in all programs that run on wine. He set it to the largest setting. Now when you open any wine program, the font is so large that you can't see anything. And at the same time, for some reason the program window only opens in one small corner of the screen. So, combine a massive font size with a small program window, and we can't see anything in the wine-run programs. And if we go into Wine -> configuration, there too the font is so massive and program window so small, that we can't get to the page where the font controls are to make them smaller again. If we could get the program window to fill the whole monitor screen, then at least we could get into Wine -> configuration, and again decrease the font size. How can we solve the problem?

---

### Post by mrhhug on 2010-09-25
i think this is a very similar problem to yours

[http://ubuntuforums.org/showthread.php?t=771316](http://ubuntuforums.org/showthread.php?t=771316)

---

### Post by swarup on 2010-09-25
I am thinking perhaps in the absence of any way to reset the font size, I can remove Wine itself, and then reinstall it. But before doing that, surely I need to uninstall the two programs that run on wine. Otherwise once I uninstall wine, those two programs will still be hanging around. And when I reinstall wine, then the new wine may not be able to run the two wine-mediated programs that were installed using the previous wine, and I fear their presence may prevent me from installing new versions of them. Is my fear justified, or should I just let the two wine-mediated programs remain, and uninstall and then reinstall wine?

---

### Post by swarup on 2010-09-25
> **mrhhug said:**
> i think this is a very similar problem to yours

[http://ubuntuforums.org/showthread.php?t=771316](http://ubuntuforums.org/showthread.php?t=771316)

Yes, it does look similar. Let me have a look at that and see if it can help me solve the matter. Thank you.

---

### Post by swarup on 2010-09-25
Well, following the instructions on that post did seem to help somewhat in that the font is smaller now. But the program window is still stuck in the upper left corner of the monitor screen, and cannot be expanded or moved. It is only about 1/10 the size of the monitor screen. So most of the program features are still outside of the viewable window and therefore unusable. I would like to uninstall the two wine-mediated programs I have, and then install and reinstall wine. But when I go to Applications -> wine -> uninstall wine software, the "remove" button at the buttom of that screen is not viewable. So although I can click on i.e. select the software to be removed, I cannot click on "remove" to remove it. So should I just go to applications -> add/remove programs, and remove wine and reinstall it (without having first removed the two programs that run using it)?

---

### Post by swarup on 2010-09-25
Well, I went ahead and ininstalled and reinstalled Wine. But it didn't make any difference. So it seems clear now that the problem is in the .wine folder i.e. with the personal settings, and not with the program itself. But how to get the graphic settings back to the default?

@mrhhug-- thank you for the reference. That post seems to be addressing the problem I face. i.e. it makes sense that the problem is in the system.reg file in the .wine folder. But the change the writer suggested, did not fix the problem for me. 

If someone could suggest a further step, I would be so grateful. My entire office work is stalled until this problem with the wine settings gets fixed.

---

### Post by mrhhug on 2010-09-25
you don't need to worry about the programs installed on wine everything is contained in your /home/YOURNAME/.wine folder (. means hidden)

is this window looking at you from another desktop ? do you have multiple desktops enabled - can you post a screenshot the printscr button is usually 2 buttons above delete ( in line vertically with your left arrow)

i would disagree with you just simply uninstalling and reinstalling wine but i'll tell you how to do it, when you go into synaptic make sure you right click and completely uninstall and be sure to remove that .wine file (thats where your settings stay)

---

### Post by swarup on 2010-09-25
What would you like a screen shot of? I deleted Wine by going into Applications -> add/remove. And when that was done, then I went into my home folder and deleted .wine as well. Now neither of the two wine-mediated programs will run. And nor am I getting success in re-installing them.

No, I am not using multiple desktops. The desktop I am typing on now is the same desktop on which the wine problem is occurring.

---

### Post by mrhhug on 2010-09-25
since you have completely removed wine. you need to install it again , are you installing from repository? like using apt or aptitude? 

after wine is installed you should be able to install the programs again, your windows programs are dependant on wine to run in linux.

deleting that .wine removed the windows programs you had installed

1. resintall wine
2. install windows programs again using wine
3. if error persists take screenshot
4. if error is gone celebrate!

---

### Post by swarup on 2010-09-25
I tried again to reinstall one of the two wine-dependent programs, and it installed! Now it is working fine, and the font is also plenty big enough for my colleague to read it. It is not exactly clear to me why it is working, but it is working. So thank you! :) I will try reinstalling the other wine-dependent program in a little while, and see how that goes. But for now, all seems fine.

---

