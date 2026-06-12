---
title: "How do I properly install the new ATI Catalyst 9.1?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-01
Here is the link: [_http://ati.amd.com/support/drivers/linux/linux-radeon.html_](http://ati.amd.com/support/drivers/linux/linux-radeon.html).  It isn't available in the repos, as far as I can see..  I was told that just installing anything from the file is bad, because I can't use Adept to uninstall it.  What should I do?  It also doesn't show up in my EnvyNG install.

---

### Post by Muffinabus on 2009-02-02
Following the installer instructions worked well for me.

---

### Post by Gotaro on 2009-02-02
I'm trying, but it wants to install Driver 8.573, not 9.1.  When I go to "Generate Distribution Specific Driver Package" I can't find Ubuntu..  But it says Ubuntu 8.10 is now supported?  Also, I'm getting a terminal version of the installer, but the pictures show a GUI!  :(  I'm doing the instructions exactly..

---

### Post by Muffinabus on 2009-02-02
8.573 is the 9.1 driver.  I'm not sure why you're not getting a GUI, and you don't want to generate a distro package, you just select the automatic install, it installs, you type in aticonfig --initial, and it SHOULD work, though most run into problems...

---

### Post by Gotaro on 2009-02-02
> **Muffinabus said:**
> 8.573 is the 9.1 driver.  I'm not sure why you're not getting a GUI, and you don't want to generate a distro package, you just select the automatic install, it installs, you type in aticonfig --initial, and it SHOULD work, though most run into problems...
Okay, I installed it.  At first, I was like "OMG MY GPU FAN IS FINALLY QUIET!  THEY FIXED IT!"..  But after a minute or so, it started to pick up speed again..  :(

I tried to aticonfig --initial, and got:
```
gotaro@gotaro-linux:~$ aticonfig --initial
Parse error on line 34 of section Module in file /etc/X11/xorg.conf
        "Disable" is not a valid keyword in this section.
```
Where do I go to check which driver is enabled?  And by the way, the line in xorg.conf it's referring to is this:
```
Disable	"dri2"
```

Also, how do I get to the Catalyst Control Center?  Navigating through ATI's website, trying to get the proper CCC version for my card, it took me to the same driver I just downloaded..

---

### Post by Gotaro on 2009-02-02
I think I solved the problem.  I edited the mentioned xorg.conf file, following these instructions:
> Delete the entire line. DRI2 is a lie (at least in Intrepid).
To check my drivers, I did this:
```
gotaro@gotaro-linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.1.8395 Release
```

And, finally, to get to Catalyst Control Center, I ran "amdcccle" from a terminal.

Thanks for all the help, guys......

---

### Post by Muffinabus on 2009-02-02
Yep, looks good (:.  I'm not sure if this happened for you, but the driver by default didn't put the catalyst control center on my applications menu, so FYI, you can access it by typing amdcccle in a terminal.

---

### Post by Gotaro on 2009-02-02
> **Muffinabus said:**
> Yep, looks good (:.  I'm not sure if this happened for you, but the driver by default didn't put the catalyst control center on my applications menu, so FYI, you can access it by typing amdcccle in a terminal.
Lol..  Well, thanks for the response!  That must have been just seconds before my edit lol.

---

