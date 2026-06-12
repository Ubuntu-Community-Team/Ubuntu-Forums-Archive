---
title: "A beginner with NVidia GeForce FX5200 resolution problem."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by WarrenL on 2010-01-15
Hi folks,

I'm an Ubuntu newbie, keen to make the switch from Windows XP. I thought I'd try the "inside windows" installation first, and it worked really well but for one problem: I cannot increase my display resolution beyond 640x480. I've downloaded and installed the latest NVidia hardware driver (version 176, IIRC) and poked about for a while, but I'm at a loss. I've had to give up and reboot to Windows so I can post on this forum.

From googling about I've seen that this has been a problem for others, but there was a certain amount of command line jargon in the answers; therefore I'd like to know if anybody can give me some help in plain English.

I've fallen at an early hurdle, which is quite a disappointment considering the buzz around 9.10.

Best regards,
Warren

---

### Post by marshmallow1304 on 2010-01-15
How did you go about getting the driver?  I'm fairly sure 176 is not the latest version, unless nVidia assigns different version numbers to different drivers.

Edit: I should have checked first.  They do use different version numbers.  The question still stands, however.

---

### Post by WarrenL on 2010-01-15
It was the one that Ubuntu found itself through the hardware update facility (and was tagged "recommended"). The previous version available was 90-something.

It did say that it had been tested by Ubuntu developers.

I'm operating from within Windows XP and gathering more details will require a boot up to Ubuntu, but let me know if there's anything I can provide here that might help answer my problem.

---

### Post by warfacegod on 2010-01-16
I have the nVidia Geforce FX Go5200 64 MB. It uses the 173 driver. I've never had any problems with it. Then again, I've never tried to use it with Linux inside Windows and I suspect that to be the problem.

---

### Post by WarrenL on 2010-01-16
It's been in the back of my mind that that might be the problem, warfacegod, so if it proves correct I will have to make a leap of faith and convert. Thank goodness for disk imaging!

---

### Post by warfacegod on 2010-01-16
I took a look at your video card. It's basically the 128 MB desktop version of what's in my laptop. It uses the same driver as well, the 173. So I'm even more inclined to think it was running inside Windows that did it.

---

### Post by WarrenL on 2010-01-16
Well, that didn't work! I've just completely overwritten my primary hard drive with a fresh install of 9.10 and I'm in the same position I was when running from within XP. Stuck at 640 x 480.

Next step?

---

### Post by ronniestamps on 2010-01-16
I have the exact same video card and the only driver that worked was 173. I had to edit my xorg.conf file to get it to work properly. Are you encountering any error messages? Does it tell you that it has to run in low graphics mode? Give me as much info as possible, I think I can help.

---

### Post by WarrenL on 2010-01-16
Hi there ronniestamps, thanks for replying! I've just reloaded my XP partition to get the wife and son off my back; now I have to go back to loading a copy of 9.10 inside Windows so I can carry on my Ubuntu experimentation on the side.

There were no messages that I recall, but I will need to step through the process again to provide you with some definite info. That'll be tomorrow ronnie, it's late at night here in NZ and I'm starting to droop over the keyboard.

Now I do recall googling up a forum thread which had somebody dealing with another NVidia card in which they had to edit the xorg.conf file, but when I hunted it down I discovered that I had to be the root user to edit it, and the root user is not activated in Ubuntu. By this time my Linux knowledge was exhausted!

I'll look in tomorrow, thanks very much for all the replies so far, chaps.

---

### Post by warfacegod on 2010-01-16
You are correct, root user is not enabled in ubuntu. Y ou can use sudo in the terminal or gksudo nautilus and it amounts to being in the user account.

---

### Post by ST3ALTHPSYCH0 on 2010-01-16
If you want to try something that's a little less command line intensive, and have a spare cd laying around, you could try the link in my sig.

---

### Post by albert s on 2010-01-16
I had major problems with my Nvidia card too last week, after loads of messing about and getting it to work , then it resetting every time I rebooted I got so fed up I re-installed 9.10 and shazaam, it just instantly worked, I tend to think I had changed some other setting first, so that time the first thing I done was download the Nvidia driver, 173 IIRC.

---

### Post by WarrenL on 2010-01-16
Well, gents! I managed to fumble about until I found a resolution (pun intended).

I reinstalled 9.10 inside Windows (after last night's near-disaster) then followed my nose according to your posts and Google, which took me to the following links:

[HOWTO: change resolution/refresh rate in Xorg - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=83973")
[The XFree86 Modeline Generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

After a bit of fiddling around in xorg.conf (thankyou for the advice on how to get into it as the root user) with the specs in the manual for my monitor (a Dell 1907FPV) I've got it all working.

The upshot of it is that downloading the drivers alone will not work - the xorg.conf file MUST be edited appropriately.

This is the kind of thing that will put off newbies - I have been so keen to switch from MS to Ubuntu yet this almost killed my desire. However having woken up yesterday morning without ever touching a Linux system in my life, I now know all sorts of things! Probably not enough to get me out of the next problem by myself though, so I'll see you all back here in about.... 5 minutes!

Thanks again for the advice and help.

Warren

---

### Post by marshmallow1304 on 2010-01-16
You might have also tried running
```
sudo nvidia-xconfig
```
but if its working now, there's no reason to mess with it.

---

### Post by MarkC502 on 2010-01-16
Warren I would recomend trying envyng to install a newer driver and try that.

Command to install envy

sudo apt-get install envyng-core

Then this to run it

sudo envyng -t

then choose uninstall current Nvidia driver followed by install Nvidia driver and pick the latest one it says is compatible followed by a reboot.

That may solve your issue, I have never had good luck with Nvidia drivers Ubuntu installs itself and I always use Envy or download a driver run package from Nvidia.

---

### Post by WarrenL on 2010-01-16
Thanks Mark. While it's working I'll leave well enough alone (I have so many other things to learn about Ubuntu!) but sooner or later I'm going to be keen to ditch Windows altogether and reformat for a full Ubuntu installation. When that time comes I'll refer back to your instructions above.

I'm simply pleased to get the display working properly so that I can now press on with other things. It does take a bit of getting used to Ubuntu after a lifetime spent in Windows.

---

