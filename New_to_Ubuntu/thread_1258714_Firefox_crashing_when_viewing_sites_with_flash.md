---
title: "Firefox crashing when viewing sites with flash"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Cashman3000 on 2009-09-05
I think this may be a reoccuring theme on the forum but i am having issues with my firefox today. Using firefox 3.0.13 on Ubuntu 9.04. Last night I fell asleep watching hulu.com and noticed this morning when i woke up that that firefox had closed down. Now it seems that firefox crashes immediately upon entering any site using flash. 

I ran firefox from the terminal and I get this message when I crash:

[SmartNamer] updateEntry()
Segmentation fault

Anyone know how to fix this problem without having to reinstall Ubuntu?

---

### Post by Liolikas on 2009-09-05
Get latest flash from adobe site and reinstall flash.

---

### Post by Cashman3000 on 2009-09-05
Okay went to Adobe site. Downloaded Adobe Flash Player version 10.0.32.18** for **Linux using Installation instructions for tar.gz. I downloaded the file to my desktop. Where do I extract the file? Its "libflashplayer.so" Right now it went to my desktop and not sure if that is correct. Most likely not.  

The instructions say that a directory called install_flash_player_10_linux will be created and that I need to navigate to this directory and type ./flashplayer-installer                       to run the installer. 

Could you possibly walk me through the rest of this Flash Installation? Any help would be greatly appreciated and thanks for the initial quick response to my thread....

---

### Post by PorkyPie on 2009-09-05
[Download this one instead]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29") . Simply download, double click and clck on Install Package. Then, Adobe Flash Player is on your computer.

---

### Post by Liolikas on 2009-09-05
```

mv ~/Desktop/libflashplayer.so ~/.mozilla/plugins/

```
Restart Firefox.
or even better upper advice it will install flash for all users.

---

### Post by Cashman3000 on 2009-09-05
Thanks for the help. I will let you know if I crash again....

---

### Post by PorkyPie on 2009-09-05
> **Cashman3000 said:**
> Thanks for the help. I will let you know if I crash again....

You're welcome. We hope you get it working! :D

And... usually, you should use a .deb version if it's provided, it's better for your system, plus, it only takes a minute to install.

---

### Post by Cashman3000 on 2009-09-05
so everything seemed to be working after the deb install and then it promptly crashed again. And to make matters worse the terminal wouldnt even stay open. It crashed right after opening then wouldnt even open at all. I am currently on my netbook and decided to do a fresh Ubuntu install on my desktop. Seems like an easier way to resolve problem.

This all stemmed from leaving Hulu.com open all night. Have you ever heard of anything like this happening?

---

### Post by PorkyPie on 2009-09-05
> **Cashman3000 said:**
> so everything seemed to be working after the deb install and then it promptly crashed again. And to make matters worse the terminal wouldnt even stay open. It crashed right after opening then wouldnt even open at all. I am currently on my netbook and decided to do a fresh Ubuntu install on my desktop. Seems like an easier way to resolve problem.

This all stemmed from leaving Hulu.com open all night. Have you ever heard of anything like this happening?

Could you please go to terminal and type ```
firefox
```?

Then, don't close the terminal, go and do whatever you were doing on hulu in the firefox window that appears, and post everything that appears in the terminal here.

---

### Post by Cashman3000 on 2009-09-05
after i installed that deb install of flash 10,  I couldn't even open up the terminal. Very weird. I am reinstalling Ubuntu as we speak. I think in the future i will just stay away from using hulu with Ubuntu because everything had been working great beforehand. Thanks for the help.

---

### Post by PorkyPie on 2009-09-05
> **Cashman3000 said:**
> after i installed that deb install of flash 10,  I couldn't even open up the terminal. Very weird. I am reinstalling Ubuntu as we speak. I think in the future i will just stay away from using hulu with Ubuntu because everything had been working great beforehand. Thanks for the help.

Go to add/remove and install konsole, then run firefox in that. Sorry that you're re-installing. :(

This seems a very weird sort of problem to me, and i strongly beleive that theres no need to re-install. I don't think flash/hulu caused the problem somehow.

---

### Post by lovinglinux on 2009-09-05
> **PorkyPie said:**
> This seems a very weird sort of problem to me, and i strongly beleive that theres no need to re-install. I don't think flash/hulu caused the problem somehow.

+1 for that

For the purpose of troubleshooting, create new Firefox profile from the profile manager:

```
firefox -P
```

Launch the new profile and visit the site crashing Firefox. Report back if it still crashes.

Also take a look at the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by MelDJ on 2009-09-05
hey, i think this might be the solution: [http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

hope it works:D

---

### Post by frank002 on 2009-09-05
You can try the latest Firefox, version 3.5 called Shiretoko, You can install it from Synaptic.  You can also try Opera. The latest is Opera 10. I am using it and so far, it has been great.

---

### Post by Cashman3000 on 2009-09-06
I will definitely check out the "libflashsupport" flash fix for jaunty the next time I run into problems with Firefox and the phantom crashing occurs. Thank for all the ideas everyone. I am obviously new to Ubuntu and every little bit of knowledge helps. This site is incredible!

---

### Post by mike555 on 2009-09-06
If you don't get flash working good for you , you might try " Epiphany -webkit " from the package manager it doesn't use mozilla as it's backend and plays flash much better .....



opp's it doesn't work on Jaunty ... sorry

---

### Post by PorkyPie on 2009-09-11
> **Cashman3000 said:**
> I will definitely check out the "libflashsupport" flash fix for jaunty the next time I run into problems with Firefox and the phantom crashing occurs. Thank for all the ideas everyone. I am obviously new to Ubuntu and every little bit of knowledge helps. This site is incredible!

On behalf of all of us, you're welcome :). There's about 909,204, probably more after this posting. If you ever have a problem, don't hesitate to post a thread :).

---

