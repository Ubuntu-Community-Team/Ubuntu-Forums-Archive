---
title: "ATI Catalyst 9.8 fresh install"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-03
Hi,

I just downloaded the 9.8 drivers from ATI's website and installed them, but when I restarted I got a window saying "ubuntu is running in low graphics mode" with a screwed up resolution.

I logged in and went to ATI Catalyst Control Center but it said it couldn't load, so I uninstalled the drivers but now i'm sort of stuck and not sure what i'm running on. I upgraded from 9.4 which were working okay.

How can I completely refresh my Xorg config file, get rid of all ATI drivers and install 9.8 the correct way from scratch?

My computer specs are in my signature.

Thanks,
Benjamin

---

### Post by automaton26 on 2009-09-03
Did you uninstall 9.4 before installing 9.8?  I always uninstall first, rather than upgrading.

And how did you uninstall?  I uninstall and reinstall like this, and I've never had any problems:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

---

### Post by humphreybc on 2009-09-03
> **automaton26 said:**
> Did you uninstall 9.4 before installing 9.8?  I always uninstall first, rather than upgrading.

And how did you uninstall?  I uninstall and reinstall like this, and I've never had any problems:

[http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")

Yep I just uninstalled everything to do with ATI now and installed the 9.8 drivers from scratch, then ran the aticonfig --initial -f command to set up the Xorg.conf file for the new drivers. I then rebooted and I still got the message "Ubuntu is running in low graphics mode" and so now i'm typing this on a low resolution low graphics mode ubuntu!

How do I get it working properly?

Edit:

This is what I get when I run the fglrxinfo command:

```

benjamin@benjamin-laptop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
benjamin@benjamin-laptop:~$ 

```

---

### Post by automaton26 on 2009-09-03
I've not seen that message before, sorry. All I can suggest is uninstall (restore the default open source drivers) and then go to the monitor configuration to check you're using the most basic bit depth (24?) and refresh rate (60Hz). And then try again.

---

### Post by humphreybc on 2009-09-03
Okay I just installed everything following this guide exactly:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

And I still get the "low graphics mode" and the same error message when I run fglrx.

---

### Post by humphreybc on 2009-09-03
Don't worry, got it sorted - I just chose to install them using the "Hardware Drivers" option and rebooted and it worked perfectly. Now I have the newest drivers with no problem!

And interestingly, the fonts over my whole computer are noticeably much clearer!

---

### Post by automaton26 on 2009-09-03
Great - nice one.

---

### Post by humphreybc on 2009-09-03
Actually scratch that, sorry I mis-read.

The Hardware Drivers actually installed a much earlier version of the drivers. Now I have the flicker problem with OpenGL and Compiz, which disappeared when 9.4 came out. So I'm going to keep trying to get 9.8 to work... if that doesn't want to work I guess I'll have to go back to 9.4.

---

### Post by humphreybc on 2009-09-03
Hmm, odd. 9.8 didn't work again so I tried 9.4 which works fine like it was before I started all this. I'm downloading 9.5, 9.6 and 9.7 to see where the problem starts.

EDIT:

Well, that was a mighty failure! I uninstalled 9.4 and installed 9.5 as a test to see if it would work, and what do you know... it didn't! After the splash screen it just froze with odd colours and the ubuntu logo, virtual terminal or anything wouldn't work.

So I booted into LiveCD (where i'm typing this from) and I've edited the xorg.conf file to use the vesa driver so I can get back into Ubuntu and run the script to uninstall 9.5 and i'll put 9.4 back on.

But, this leaves me with a question - why does it seem that I cannot use anything other than Catalyst 9.4 drivers?

---

### Post by humphreybc on 2009-09-03
********. Changing the Driver to "vesa" still doesn't work and i'm left with an unbootable system. I'm trying to work out how to run the fglrx-uninstall.sh script from the liveCD, but it doesn't want to work until I make my mounted directory the root directory.

---

### Post by automaton26 on 2009-09-03
Use 9.4 drivers if they work for you.

When ATI release a new version every month, they are just fixing bugs and improving performance for those cards that came out most recently. If your card is more than a year old I would bet the binary drivers for it haven't changed for months.

---

### Post by automaton26 on 2009-09-03
Sorry about the double post - forum fail.

---

### Post by remymarathe on 2009-09-03
> **humphreybc said:**
> ********. Changing the Driver to "vesa" still doesn't work and i'm left with an unbootable system. I'm trying to work out how to run the fglrx-uninstall.sh script from the liveCD, but it doesn't want to work until I make my mounted directory the root directory.

Are you SURE it's hanging before you can get to a basic login shell?  If you're using grub, hit escape to bring up boot options, boot the recovery mode kernel, and from the Recovery Menu select something like "Root shell prompt without networking".  

Had to do this last night to run the same script you're trying to get at, like a fool I think I installed both fglrx and the open source ati drivers, and was getting an ugly hang the minute X started, even after I changed xorg.conf back to defaults.  The fix for me was what you're trying to do.  

Now if I can sort out *which* driver and install method I should try first I'm golden, at least I can get back into my system now.

---

### Post by humphreybc on 2009-09-04
> **remymarathe said:**
> Are you SURE it's hanging before you can get to a basic login shell?  If you're using grub, hit escape to bring up boot options, boot the recovery mode kernel, and from the Recovery Menu select something like "Root shell prompt without networking".  

Had to do this last night to run the same script you're trying to get at, like a fool I think I installed both fglrx and the open source ati drivers, and was getting an ugly hang the minute X started, even after I changed xorg.conf back to defaults.  The fix for me was what you're trying to do.  

Now if I can sort out *which* driver and install method I should try first I'm golden, at least I can get back into my system now.

Yeah it's definitely before the login screen. I've gone back to 9.4, just given up on 9.8!

---

### Post by sturdy on 2009-09-04
I'm a nooby in the same boat. I managed to bork my fglrx driver and now cannot logon. I see three small, distorted logon graphics across the top of the screen but nothing else. I'd be very interested in the details of any fix that you find. TIA...

---

### Post by remymarathe on 2009-09-04
Okay just to be clear, for sturdy too, I'm not talking about the gnome prompt you guys are used to logging in with.  That prompt appears after your video driver is already loaded.  You want to jump in while the machine's still scrolling text-only.   

When you power on your computer, you'll see bios information, have a chance to enter bios to change settings.  Let it go.

*Right* after that, you get notification that the bootloader (in my case Grub) will load in a moment.  You should have a few seconds to hit the escape key and see the kernel options for yourself.  

Select the recovery mode kernel.

A menu should come up, one option of which gives you a root terminal with no networking.  This is a basic text login shell.

fglrx shouldn't be able to touch or hang your system until X is run, and there's time before that to break normal system startup and get to a shell for maintenance.  

If you can get to that point, this will remove fglrx:
apt-get remove --purge xorg-driver-fglrx   

though your xorg.conf might need editing too.

---

### Post by humphreybc on 2009-09-04
What remymarathe said was good and should work to get rid of the ATI drivers, but if that command doesn't work then try this to run the ATI uninstaller to get rid of their driver:

```

sh ./usr/share/ati/fglrx-uninstaller.sh

```

and then run this code to get rid of the ATI folder in etc:

```

rm -f /etc/ati

```

And then finally run this command to reconfigure the xorg configuration file to tell the computer to use the default drivers on boot, instead of the (now removed) bad ATI drivers:

```

dpkg-reconfigure -phigh xserver-xorg

```

Once you've done that, exit the root shell (escape I think) and then choose "Resume normal boot." You should be able to login as per usual, at which point you can rollback to the older drivers that worked for you.

---

### Post by sturdy on 2009-09-05
Woooohoooo...thanks guys, I'm back. We noobies love those step-by-step instructions. Have a great day. I'm off to do some computing :)

---

### Post by PeonDevelopments on 2009-09-11
One reason I found that some catalyst drivers don't work, is due to the kernel version, kernel modules, and xorg.

I installed Arch on my laptop and for the life of me, catalyst wouldn't work. 9.8 failed, 9.10 (extracted from koala) failed, when using Ubuntu 8.10 the only catalyst that worked was 8.12.

I've seen the black screen of freeze so many times. It's not fun.

---

### Post by markbuntu on 2009-09-11
The driver will not work from a fresh install without all the updates.

---

