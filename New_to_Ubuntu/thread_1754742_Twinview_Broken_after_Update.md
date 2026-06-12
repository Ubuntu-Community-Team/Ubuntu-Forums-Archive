---
title: "Twinview Broken after Update"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Frustrated_Frustrated on 2011-05-10
I am running Ubuntu 10.04 (can't figure out how to upgrade, not sure I want to) and after a recent update, find that my two-monitor setup using Twinview no longer functions.  An error message as X Windows starts up indicates the stored size is invalid.  I tried restoring xorg.conf from backup to no avail.  I also installed the prior version of nvidia-current, again to no avail.

Any ideas or advice?

---

### Post by taseedorf on 2011-05-11
This is what I would try.

I would install the latest nvidia drivers from their website, not the drivers provided from ubuntu.

second, or try this instead... completely delete xorg.conf and run sudo dpkg-reconfigure xserver-org ...orsomething like that, i forget. ;)

---

### Post by Frustrated_Frustrated on 2011-05-11
> **taseedorf said:**
>  delete xorg.conf and run sudo dpkg-reconfigure xserver-org ...orsomething like that, i forget. ;)

See, that's not very helpful, given that I'm an absolute beginner.

---

### Post by Frustrated_Frustrated on 2011-05-12
So, how does one get help with a problem with an update?

---

### Post by astex on 2011-05-12
Haha.  You're in the right place.

That command was actually correct.  Backup your xorg.conf file, delete it, then run:

```
 $ sudo dpkg-reconfigure xserver-org 
```

from a terminal window.  You will have to reboot to notice changes.

---

### Post by Frustrated_Frustrated on 2011-05-13
Well, that command didn't work, but substituting xserver-xorg did.  Then I restarted, started Nvidia, followed the instructions of creating a new xorg.conf file, restarted, and...


No change.  Still says the same thing upon startup, and my second monitor still doesn't work.

---

### Post by Frustrated_Frustrated on 2011-05-13
I tried using that command, no change.

I then downloaded the latest driver from NVidia.  After an immense amount of difficulty, I got it installed.  My computer starts up, and gives me an error saying the system is in low resolution mode.  I follow the prompts to reconfigure for this setup and restart.  The same error persists, and now I have incorrect settings - refresh rate is screwed up.

I redid the reconfigure, same thing happens as described above and the error still persists.

---

### Post by Frustrated_Frustrated on 2011-05-13
Now I'm stuck in an endless loop.

The driver I installed isn't functioning, it says:

Please see the nvidia-177-kernel-source package for building the kernel modulerequired by this package. This will provide nvidia-kernel-<version>


I don't know how to do this.  And also, it is using the "stock" driver for Ubuntu, but the display is not correctly configured and I don't know why, despite using my backedup xorg.conf file.


When I try to run the NVIDIA x server GUI, it says I have to recreate my xorg.conf file, but when I do that and restart xserver, I have to restart and I'm back to the error in the previous post.  Something keeps deleting my xorg.conf file but not saving it correctly.  I'm not logged in as root when I do all this, if that makes any difference.


Also, I was able to track down why the driver doesn't work.  I have to configure it per the kernel, and have no idea how to do this.  Here is a link to the README file for the driver:
[http://us.download.nvidia.com/XFree86/Linux-x86/270.41.06/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86/270.41.06/README/installdriver.html)

I really have no idea what I'm doing.  Sorry, but I'm not proficient at this Linux thing yet.

---

### Post by corncob on 2011-05-13
> **Frustrated_Frustrated said:**
> I am running Ubuntu 10.04 (can't figure out how to upgrade, not sure I want to) and after a recent update, find that my two-monitor setup using Twinview no longer functions.  An error message as X Windows starts up indicates the stored size is invalid.  I tried restoring xorg.conf from backup to no avail.  I also installed the prior version of nvidia-current, again to no avail.

Any ideas or advice?

Maybe you should upgrade:  System > Administration > Update Manager >  Settings... > Show New Distribution Releases and change it to Normal Releases.  That way the option will show up on your Update Manager.
I haven't used Twinview in a long time.  In the last couple Ubuntu releases at least, I've gone to System > Preferences > Monitors.  There you can detect monitors (if not already detected), turn them on or off, set resolutions...  You probably want to uncheck 'Same image in all monitors'.

---

### Post by Frustrated_Frustrated on 2011-05-13
> **corncob said:**
> Maybe you should upgrade:  System > Administration > Update Manager >  Settings... > Show New Distribution Releases and change it to Normal Releases.  That way the option will show up on your Update Manager.
I haven't used Twinview in a long time.  In the last couple Ubuntu releases at least, I've gone to System > Preferences > Monitors.  There you can detect monitors (if not already detected), turn them on or off, set resolutions...  You probably want to uncheck 'Same image in all monitors'.

Ummm...updating was what got me here in the first place.  I want to get to a stable system, duplicate my hard drive, THEN try upgrading.

No one has yet to tell me how to undo the update that broke my system in the first place.


Also, I cannot use the Ubuntu monitor tool as it says my driver isn't supported.

---

### Post by Frustrated_Frustrated on 2011-05-13
I followed these instructions here:

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

Still the same problem.  It's like its trying to use the driver I didn't successfully install, but hardware drivers indicates otherwise.

---

### Post by Frustrated_Frustrated on 2011-05-13
I followed the instructions here:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and the problem with the startup went away, but the initial problem still remains.

HELP!

---

### Post by astex on 2011-05-13
Please post your xorg.conf file.

---

### Post by Frustrated_Frustrated on 2011-05-13
I went back and tried the initial fix.  It finally fixed the error of not recognizing the sizes, but the second monitor still doesn't work, and the Nvidia GUI still won't let me use TwinView (it's greyed out.)

Posting my xorg.conf file won't do much good I fear.  I am using the original one from before it broke because when I tried to restart using the new xorg.conf, the resolution was cut down and it didn't recognize my monitor at all, and wouldn't let me detect.

I suspect that part of the problem may be that I am using an XFX clone of an NVIDIA GeForce 8600GT car and the driver isn't compatible.  All I want is for whatever broke the system after an update to be removed so I can go back to how it was.

But, here's my xorg.conf file:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.29  (buildmeister@swio-display-x86-rhel47-02.nvidia.com)  Wed Feb 23 16:38:34 PST 2011

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA720"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
# Added ", CRT-1" to line below
    Option         "TwinViewXineramaInfoOrder" "CRT-0, CRT-1"
# Added two options: "UseDisplayDevice" and "TwinViewOrientation"
    Option         "UseDisplayDevice" "CRT-0, CRT-1"
    Option         "TwinViewOrientation" "CRT-1 LeftOf CRT-0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x960 +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Frustrated_Frustrated on 2011-05-15
I posted the file.  What now?

---

### Post by Frustrated_Frustrated on 2011-05-17
I've posted my xorg.conf file.  This problem still persists.  It is extremely frustrating.

Anyone?

---

### Post by Frustrated_Frustrated on 2011-05-18
Can someone please help me with this problem?

---

### Post by GypD on 2011-05-18
I'm also an absolute beginner, but for me to get to 11.04. I had to update 10.04 to 10.10 then up to 11.04,( I had to start from 7.04) on my pc

---

### Post by Frustrated_Frustrated on 2011-05-18
> **GypD said:**
> I'm also an absolute beginner, but for me to get to 11.04. I had to update 10.04 to 10.10 then up to 11.04,( I had to start from 7.04) on my pc

Honestly, why would I upgrade when I can't even get this version working?

First things first - get the system working, then back it up completely, THEN try upgrading.

I went through this nightmare before - when updating, I lose Virtual Machine.  It took three days of frustration and lost productivity to get it back.  I learned my lesson...until I forgot.

---

### Post by Frustrated_Frustrated on 2011-05-18
Going to try something new.

I have to "screen" sections in xorg.conf; which I am studying.  I'm going to comment out the first one (see above) and see what happens.

---

### Post by Frustrated_Frustrated on 2011-05-28
So, I tried upgrading my system to 11.04.

Do I have to tell you what happened?  How many of you already know my system won't even start now unless I use Grub to boot an older kernel?

I copied my system to another drive before I upgraded, but I cannot boot from that drive.  So I do not know what to do, either to fix this problem, or better yet, get rid of the upgrade and go to 10.10.

HELP!!!

---

### Post by corncob on 2011-05-28
I upgraded one computer to 11.04 and that was enough for me.  The four others I'm leaving with 10.10.

---

