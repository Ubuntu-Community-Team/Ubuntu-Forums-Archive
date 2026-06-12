---
title: "I killed x! Can I restore from live cd?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by oepott on 2010-06-19
While trying to install an updated nvidia driver, I somehow "lost" my (mother's!) desktop! After rebooting, I get the background color/splash screen, but no desktop. No gnome, no icons. I've managed to kludge my way back into the computer enough to get it running with a live cd, and that's what I'm typing from now to post this. And the computer sees things as if I'm running from it's installed system, except that the icons for Chrome and opera, etc, are missing. No big deal as far as that goes, I can reinstall them in a minute. But what can I do to get the start up to go past the splash screen and load gnome?
 Part of the (attempted) nvivdia  "fix" was to blacklist previous drivers. So there may be some digital wrenching required. Be nice to just "whack something" from the terminal and let Ubuntu fix itself, if that's possible. And as far as the graphics go, I've obviously got something working now since I have a monitor working to send this.

---

### Post by cariboo on 2010-06-19
Start in recovery mode, at the menu choose drop to root prompt. Once at the prompt type:

```
nvidia-xconfig
```

Once the command is finished, reboot. You should have a working desktop.

---

### Post by nhasian on 2010-06-19
i would remove the nvidia driver that you installed and unblacklist whichever drivers you removed to get you back up and running.  perhaps you installed the wrong nvidia driver for your graphics adaptor.

you can see which graphics adaptor you have with the terminal command:

```
lshw -C display
```

---

### Post by pottzie on 2010-06-19
Just so we're all on the same page here, what I've got when I boot is the background (color) splash screen and the mouse "arrow." Nothing else.
 I just tried reinstalling with "sudo apt-get install ubuntu-desktop," and it seems to think all is well. And for some unknown reason I get an authentication error when I use my password to log in as su. Even though I was able to use it to start x when I tried starting in safe mode. So although sudo seems to work, I can't get the "su" password to work. 
 From doing all this, I'm no longer in the live cd and am typing this from another computer. I'll see if I can get back in with the live cd, but I have to "fudge it," as the computer won't boot of the cd. Got it to work before by booting into recovery mode and then closing the cd drive with the cd in it.
 Just tried doing that twice, failed on both attempts. I can ctrl/alt f2 to get into the terminal but still get an authentication failure when I use the password to get su privileges.

---

### Post by jocko on 2010-06-19
> **pottzie said:**
> I just tried reinstalling with "sudo apt-get install ubuntu-desktop," and it seems to think all is well.That will not do anything at all except to reinstall some default applications you may have uninstalled.

> **pottzie said:**
> And for some unknown reason I get an authentication error when I use my password to log in as su. Even though I was able to use it to start x when I tried starting in safe mode. So although sudo seems to work, I can't get the "su" password to work.
The root password is disabled by default in ubuntu, so "su" on it's own will not work, as it asks for the root password.
Use "sudo *command*" and your user's login password to run a single command with root privileges. To get complete root access in a terminal session, use "sudo -i" (once you are done with whatever you needed to be root for, log out root and switch back to your normal user with "exit").

---

### Post by oepott on 2010-06-19
I got it! I haven't had to use the "safe" option at start up, and didn't notice that one of the choices was to use "dpkg fix broken packages." When I did that (and resisted restarting when everything went dark during the process..got lucky and hit the space bar, making the screen turn on after it timed out..)
 A whole lotsa stuff scrolled across the screen a s this was going on. What i hoped was that since I (happily) saw stuff for gnome, X, and nvivdia that Ubuntu would sort itself out and undo whatever I had done. And thankfully, it did.
 Now to fix the original problem..which, after checking with the local computer repair guys, is most likely a bad monitor!

---

