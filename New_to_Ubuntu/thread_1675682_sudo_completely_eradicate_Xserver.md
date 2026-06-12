---
title: "sudo completely eradicate Xserver"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2011-01-25
I just switched from an Nvidia to an ATI card and of course Ubuntu booted up into low graphics mode. I tried to get my computer back up and running with new ATI drivers but no luck. The backup plan was to SSH into the computer and try to fix it.

Long story short, I blew up my Xserver I'm guessing. The thing that made it worse was some nice code such as 
```
rm -r ~/.Xauthority
touch ~/.Xauthority
```

Now I have a black screen on my computer and I can't launch anything via ssh -X from another computer. My plan was to download the drivers from the AMD website and hope that it fixed things.

Are there some strictly shell commands I can give to the computer to get even very low res video?

I'm assuming /etc/X11/xorg.conf is completely eradicated along with whatever Xauthority I thought the thread I came across had me rm...

---

### Post by Lazy-buntu on 2011-01-26
I'm going to try ```
sudo apt-get purge xserver-xorg
```, rebooting, and reinstalling. I'll let you know the results.

Edit: I've got ssh -X working again. Going to reboot and see if I get any sort of GUI.

---

### Post by Lazy-buntu on 2011-01-26
Sorry for posting, but fixed it on my own. Here's what I did (YMMV) via ssh -X:

```

sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg
sudo reboot
sudo cd ~/Downloads
sudo sh ./ati-driver-installer-9-12-x86.x86_64.run
sudo reboot

```

That assumes you've downloaded the driver package from AMD to a directory in your home folder called "Downloads". After you run that sudo sh line of code, a GUI will walk you through the installation. I just did express and clicked right through. Right now I'm up and running, multiple monitors, 1920x1080, visual effects are working, catalyst is up and working, etc.

Hope this can help someone in the future who goes from an Nvidia card to ATI (at least someone going to 5870 lol).

---

