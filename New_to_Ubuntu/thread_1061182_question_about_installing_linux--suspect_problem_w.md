---
title: "question about installing linux--suspect problem with video drivers"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by jebslg on 2009-02-05
I would like to install linux on my Dell Optiplex GX260.  I created an Ubuntu installation CD, but when I try to run linux without modifying my system, I get a white screen and then a black screen and then it seems to get stuck.  I've tried pressing various keys, (including enter and esc) but nothing happens.  I am able to run linux from the CD in safe graphics mode, so I suspect that the problem is with my video card.  I was thinking that perhaps I can install linux and then find the correct drivers for my video card, but then I get an i/o error of some sort when I try to install.  According to Windows XP, my computer has an Intel 82845G/GL/GE/PE/GV Graphics controller.  Does anyone have any suggestions about how I can get the display working properly?  Should I install linux from the boot menu (I am planning to have a dual boot system) and then fix the display?  Thanks for any help!

---

### Post by jpoRS on 2009-02-05
First thing first- when you are at the very first menu the disc gives you before you install anything, there SHOULD be a option to check disc for errors.  Do that.

And as a heads up, I don't know what video card you have, but most don't require drivers (I think it is just some nVidia and ATi cards, but I could be wrong about that).  Before you go searching for a driver, let us know what kind of video card you have so we can help you find out if you really do need a driver.

Good luck and welcome to the community.  
Peace,
jim

---

### Post by lykwydchykyn on 2009-02-05
I have installed Linux on many GX260's, and I can tell you that on early BIOS versions there is a bug that can cause problems with Xorg.  Download the latest BIOS from dell and install it (you'll need a DOS disk).

I know updating the BIOS is scary, but trust me you need to do this.

---

### Post by donkyhotay on 2009-02-05
I'd recommend using the alternate install disc. It's not as pretty but much less likely to have problems. I honestly almost never download the regular installer anymore because of it.

---

### Post by jebslg on 2009-02-07
Thanks for the suggestions. I installed Linux using the alternate CD, and I found out that my BIOS is already updated, but I still can't use the graphical interface; I just get a white screen.  I am able to log in to the command line.  My system has two 40GB hard drives--one for Windows XP and one for Linux, and I let the installation CD assign the partitions for me.

I had tried the two test options on the install CD--test the CD and test my computer memory and everything was good.

I am able to load Linux using the regular installation CD on a different computer (Dell Optiplex GX 400 with a different video card), which is why I suspect that Linux has a problem with my video card.  According to the control panel in Windows XP, my computer has an Intel 82845G/GL/GE/PE/GV Graphics Controller.  I would be happy to have any suggestions about how to get Linux running on my computer.

---

### Post by carml on 2009-02-07
Once you made login,try to code: sudo apt-get install ubuntu-desktop.This should install the missing packages,at least I hope it will solve.

---

### Post by avtolle on 2009-02-07
Does the sign-in page appear? If so, select, from Sessions, Safe mode Gnome (I think that's what it is called); when in, disable visual effects (System-preference-appearance) then restart and see if that helps.

---

### Post by glennric on 2009-02-07
The problem is your video card.  There is a bug in the intel driver that affects chips with the 82845G/GL chipsets.  The bug makes it impossible to run compiz.  If you do run compiz you will get the behavior that you are seeing.  It turns out that your computer is not locked up, but all video response is.  You could actually ssh into your computer remotely (if you have ssh server set up) to verify this.  If you upgrade to the latest version of compiz in the repositories this problem will be fixed in the sense that your chipset is now blacklisted by compiz, and so compiz will not run.

---

### Post by jebslg on 2009-02-09
Thanks for the suggestions.  I downloaded and extracted the installation files for both the current version and development version of compiz, but then I couldn't figure out how to install it from the command line prompt.  So, when I was searching online for instructions, I found something about uninstalling compiz
(sudo apt-get --purge remove compiz).  I uninstalled compiz (which hopefully wasn't a bad decision), but I still get a blank white screen when I tried to boot linux.  I get the same result when I chose 'failsafe Gnome' from options on the login screen and then tried to get into Linux, so I couldn't try to disable visual effects.  Finally, I also tried 'sudo apt-get install ubuntu-desktop', but it said that nothing needed updating.

Please help--I am really hoping to get Linux running.  I mostly want to use it to communicate with another Linux computer and use matplotlib, so I probably don't need fancy graphics.  I don't care if I use Gnome, KDE or whatever else is available.

---

### Post by lykwydchykyn on 2009-02-09
If you can log in to it at the command line, run this command to scan for errors in the Xorg log and let us know if there's anything notable:
```

cat /var/log/Xorg.* |grep "(EE)"

```

---

### Post by jebslg on 2009-02-09
The command:
cat /var/log/Xorg.* |grep "(EE)"

didn't show any errors.  As mentioned in the comment about compiz, my computer is probably not locked up--I still have a cursor that moves when I move my mouse.  Is there some way that I can easily make sure I disable any fancy graphics stuff from the command line or is it possible that my attempt to uninstall compiz didn't work?

Thanks!

---

### Post by alohatim on 2009-02-09
I have just installed ubuntu on a dell computer with that same chip.  

I first updated the bios to A02.  Then I intalled with the live cd in Safe Graphics mode.  It was a little hard because at 640x480, the forward button was not visible.  I had to guess where to click at the bottom of the screen or press the enter key and hope it was on "forward".  It installed very quickly and without problem.  

When I rebooted, I was still at low resolution.  I read somewhere that I need to edit the xorg.conf and change "vesa" to "intel" I used the command:  sudo nano /etc/X11/xorg.conf.  It took me a little while to figure out the editor.  The up carats mean to hold the ctrl key down.  Once you have made your edits, you press ctrl+X.  You have to press enter to tell it to save your changes.  I think I remember you have to press a y too. When it is done, you are back to your terminal. 

After rebooting again, I was automatically at a good screen resolution.  

Someone had told me I should use the command sudo dpkg-reconfigure -phigh xserver-xorg.  When I did that, I had go back to the editor and change vesa back to intel.  

So, I don't remember if you said you tried to proceed in Safe Graphics mode.  Did you?

---

### Post by glennric on 2009-02-10
If you want to uninstall compiz so that it will not run you need to do
```
sudo apt-get remove compiz compiz-gnome
```

---

### Post by jebslg on 2009-02-11
The specific changes here recommended for xorg.conf didn't work for me--I just had a generic file.  But a web search on 'xorg.conf' and 'Intel 82845G' gave lots of suggestions from other people having problems with the same graphics card.  The changes that worked (at least one time) for me can be found at:
[http://forums.fedoraforum.org/showthread.php?t=207320](http://forums.fedoraforum.org/showthread.php?t=207320)

This solution is for a different linux distribution, so for Ubuntu, I only needed to do step 5, and it didn't require internet access.  I added the 'Option' line and changed the specified 'Driver' but not the 'Identifier'.

To to this, from the boot menu I chose 'recovery mode' and then 'drop to command prompt'.  The steps are very easy to follow, but it is probably a good idea to back up the xorg.conf before changing it by typing:
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

I am not sure what I did when I tried to uninstall compiz before, but if everything is working, I probably should just not worry about it.

---

