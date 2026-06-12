---
title: "uninstall wine, and PS: I hate itunes"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by chemgrl08 on 2010-10-07
Greetings. I'll try to keep this short:
I was trying to convert an m4p (protected itunes music file) into an mp3 or ogg or pretty much anything else that'll actually work. Determined that the best thing would be to install itunes via wine, burn a cd of my music, then rip it off as mp3. Well I didn't tell itunes to "autodetect" the CDs when I installed it and I think that made it not be able to burn a CD. So I thought I'd uninstall it and try again. Couldn't really get itunes to completely remove, so thought I'd just completely uninstall wine. Well that really fu-barred everything because now I can't get rid of wine completely but I can't reinstall it either! (Sigh: it started as such a simple problem! lol)
I am running Lucid Lynx. I have tried to uninstall via synaptic/software center: it still isn't completely uninstalled. I try to click "install" for wine (since the button appears), but nothing happens. I have read on some posts about manually going in and deleting some files, but can't figure out where they are (forgive me, but you'll have to be very basic in telling me where they are. i.e. "your user name folder>blah blah>...)
So now that I have screwed up Wine, kindly help me to reinstall it and I will quit messing with it once it works. Damn you, itunes! #-o

---

### Post by beew on 2010-10-08
You don't need itunes. ffmpeg converts anything. You can get it in the repo, for a gui front end you should install Winff as well. (**Edited** ok , I thought you mean mp4, my bad, I don't know the answer then :))

As for removing itunes you can simply uninstall it from WINE. The icons will still show,-even though the program is deleted already,-- to get rid of them go to /home/username/.local/share/applications and you should see the wine folder, open it and delete the itunes desktop files and that should do it.

**EDITED:** To be able to see the .local folder you have to choose "show hidden files" or something like under view on your file browser.

---

### Post by Dustin2128 on 2010-10-08
you don't have to uninstall wine to remove itunes as the above poster noted, but you'd remove wine by typing this into the terminal ```
sudo apt-get remove wine
```

---

### Post by rburkartjo on 2010-10-08
chem use these commands in the order given to completely remove wine
[http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

---

### Post by chemgrl08 on 2010-10-08
beew, I bow to you! =D> Thank you, that was the trick. Dustin2128 and rburkartjo, thank you for your help as well, but actually that was both the same as uninstalling Wine with the software manager, which is aparantly not all you have to do to get rid of wine.
Also, thanks beew for the ffmpeg suggestion, but one thing at a time! Reset-up my wine and then figure out this other problem, hopefully without screwing up something completely unrelated. haha! :lolflag:

---

