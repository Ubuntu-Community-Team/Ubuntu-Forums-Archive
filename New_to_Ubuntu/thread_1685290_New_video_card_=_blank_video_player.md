---
title: "New video card = blank video player"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Cooker on 2011-02-10
I have Ubuntu 10.04 installed on my dell optiplex. Everything worked  great until I installed a video card (Asus EN210), now I have no video  in Movie Player or VLC however there is still sound in both. Online  flash videos work fine in windowed and full screen. Could this be a  video configuration issue with the Nvidea driver that is now installed?

---

### Post by no2498 on 2011-02-10
? have you installed the ubuntu extra's
that gets a lot of video codes installed

---

### Post by quadproc on 2011-02-10
> **Cooker said:**
>  Could this be a  video configuration issue with the Nvidea driver that is now installed?
Yes, you need to uninstall the old driver.  After that, you may need to install a new driver for your new graphics hardware, depending on what you plan to do with the graphics system.  Uninstalling the old driver should return you to the default Ubuntu driver and that driver may be adequate for your needs.  If not, then you need to install a driver appropriate for your new hardware.

I am somewhat surprised that your system runs at all with mismatched driver/hardware.

quadproc

---

### Post by Cooker on 2011-02-10
Whoops, forgot to mention that I did select the "Extra" button in the "Visual Effects" under "Appearance Preferences" after installing the new card. When I did that it searched and found a driver for the card and subsequently installed it. The card is indeed an Asus video card but its chipset is Nvidia GeForce.  The new driver seems to have it's own video configuration manager, "NVidia X Server Settings" which is "recommended" by my computer. Previous to all this there was only onboard video.

---

### Post by quadproc on 2011-02-10
> **Cooker said:**
>  When I did that it searched and found a driver for the card and subsequently installed it. The card is indeed an Asus video card but its chipset is Nvidia GeForce.  The new driver seems to have it's own video configuration manager, "NVidia X Server Settings" which is "recommended" by my computer.

Two things:

First, something should have disabled the original graphics hardware.  I do not know if the software that you used did so.  You might need to do this yourself in the BIOS.

Second, I would recommend _not_ using the "additional drivers" utility.  Reason: the last time that I used it, the utility did not give me a choice of which driver to install. Instead, I would go directly to the manufacturer's web site and download the appropriate driver for your graphics hardware, your CPU size (32/64), and your version of Ubuntu.  Once I had a good download then I would install that driver.  And I would keep a copy of the download, just in case I needed to reinstall the driver.

You *really* need to be sure that any new driver and any little bits of it have been removed from your system before you start to install a new driver.  Some driver uninstall packages leave behind little bits of stuff and these bits can prevent your installation from succeeding.  I would recommend that you Google your graphics hardware ID along with something like "driver remove" to find directions on how to do that.

quadproc

---

### Post by Cooker on 2011-02-10
OK, I might have some new info.

 The BIOS only gives me an option for external video settings of OFF or Auto (yay Dell....lol) onboard was a measly 8 MB MAX, hence the addition of a video card.

  I tried installing MPlayer and using it, got an error for initializing video out. I tried several different output settings and found the gl2 output to work.  Hmmmmm, interesting.

  Opened VLC player and set video output to GL and now it works too. Am I on to something?

  Unfortunately Movie Player doesn't seem to have a video output setting in the preferences so it still doesn't work.

  As it sits right now, I can handle not having Movie Player work as the other two players seem to be fine. Would it still be advisable to try to get a different driver? Everything else seems to work OK.

Thanks for all the help, I truly appreciate it, cheers!

---

### Post by quadproc on 2011-02-11
> **Cooker said:**
> 
  As it sits right now, I can handle not having Movie Player work as the other two players seem to be fine. Would it still be advisable to try to get a different driver? Everything else seems to work OK.

I recall having seen a number of Ubuntu Forums posts regarding some of the video players not working; it is possible that the problem which you have is a problem in the player, rather than the driver.  If so, it might get fixed in some future update so it may be worth installing updates for that player as they become available.  I do suggest some caution because sometimes an update will break something that used to work.

If I were in your situation I would probably try to live with the working players and not worry about the driver, at least until and if I found some other application that didn't work.

It is good that you have something that works. :)

quadproc

---

### Post by Cooker on 2011-02-12
OK, thats kinda what I figured too.

Thanks again for helping me out.

---

### Post by gradinaruvasile on 2011-02-13
> **Cooker said:**
> OK, I might have some new info.

 The BIOS only gives me an option for external video settings of OFF or Auto (yay Dell....lol) onboard was a measly 8 MB MAX, hence the addition of a video card.

  I tried installing MPlayer and using it, got an error for initializing video out. I tried several different output settings and found the gl2 output to work.  Hmmmmm, interesting.

  Opened VLC player and set video output to GL and now it works too. Am I on to something?

  Unfortunately Movie Player doesn't seem to have a video output setting in the preferences so it still doesn't work.

  As it sits right now, I can handle not having Movie Player work as the other two players seem to be fine. Would it still be advisable to try to get a different driver? Everything else seems to work OK.

Thanks for all the help, I truly appreciate it, cheers!

Something is not right there. The best video output is xv (that is the default form all programs) and vdpau in your case.
If xv output is not working you have some serious issues. I  did have an Asus nvidia 210 and i had absolutely no problems with it, it worked perfectly.
But again i used the proprietary driver downloaded from nvidias site and Debian...

---

