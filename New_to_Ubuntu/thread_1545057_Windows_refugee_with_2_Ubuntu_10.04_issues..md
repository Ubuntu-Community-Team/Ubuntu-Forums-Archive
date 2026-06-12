---
title: "Windows refugee with 2 Ubuntu 10.04 issues."
date: 2010-08-03
forum: New to Ubuntu
---

### Post by J.Alec.West on 2010-08-03
I've only been using Ubuntu for 3 days and I'm already very happy with it.  But, I have two issues I can't seem to solve and am hoping there's help for me.

First, is there any way to totally disable hibernation?  In the Power Management Preferences area, I've checked NEVER under both "Actions" and "Display."  But even so, the monitor still dims out and dies after a few minutes of inactivity - requiring me to enter my password to resume.  I'd like to run some rather time-consuming applications that may not complete if the system hibernates.

Secondly, my system's NVIDIA display has a driver for Linux.  But, it doesn't allow me to change my widescreen monitor display size to 1280x800 - like I can in Windows.  Is this an NVIDIA issue with the Linux driver that may (hopefully) be resolved in the future?  Or am I stuck with a 1360x768 display size?  It's beginning to hurt my eyes (grin).

Any help appreciated.

---

### Post by surfer on 2010-08-03
the dimming of the monitor is just the screensaver. your computer should not hibernate when inactive (unless you set it up that way). to switch off the password prompt: System -> Preferences -> Sreensaver and untoggle "Lock screen when screensaver is active".

---

### Post by surfer on 2010-08-03
i used to install 'nvidia-settings' on older ubuntu machines. this was a GUI that generatred X config files which could also be used for dual head graphics (one output on the laptop screen, the other on a beamer or so).

i have not tried this for a long time, so no guarantees.

---

### Post by Perfect Storm on 2010-08-03
Try this in the terminal:

```
gksudo nvidia-settings
```

Make your changes, restart X.

---

### Post by lancest on 2010-08-03
The system will prompt you to install the Nvidia proprietary driver.
Once you have done so nvidia-settings control will be located under System.

---

### Post by J.Alec.West on 2010-08-03
Surfer,

That solved the hibernation problem.  To tell you the truth, though, the "Screensaver" control window would have been the last place I looked to solve the problem (since I don't use screensavers).  Thanks for pointing me in the right direction.

Artificial Intelligence & lancest,

The "gksudo" command in terminal only brought up the same NVIDIA settings screen I've already been to.  Oddly, on that settings screen, clicking on the Advanced button opens up a panning window that left me with the impression that a user could set up a customized setting.  But when I entered 1280x800 on that line and applied it, it defaulted back to the original settings (sigh).

But, thanks for trying to help.  This appears to be an issue of the Linux driver for NVIDIA that has yet to be resolved.

---

### Post by da burger on 2010-08-03
> **J.Alec.West said:**
> Surfer,

That solved the hibernation problem.  To tell you the truth, though, the "Screensaver" control window would have been the last place I looked to solve the problem (since I don't use screensavers).  Thanks for pointing me in the right direction.

The problem was a difference it terms, you computer wasn't hibernating as you thought (which means basically turning off and saving the current status to a special file whilst the screen dimming is a screensaver which simply turns off of changes the display on the screen.

---

### Post by JKyleOKC on 2010-08-03
I'm migrating from the 8.04 LTS version to 10.04 as the result of an intrusion that left me not trusting the existing systems, and have run into essentially the same problem of video resolution choices. The 10.04 does not use xorg.conf by default, and since my Acer X173w LCD monitor sends an invalid EDID packet, the system defaults to low resolution: 800x600 on 8.04 and 1024x768 on 10.04, rather than the 1400x900 that's the native setting for my monitor.

Fortunately I did have a copy of the old xorg.conf in my backups, and was able to restore that to /etc/X11 -- but that immediately created a new problem in that the 10.04 install had not installed the Nvidia driver that the old config file was calling for! Here's the solution I arrived at after a day and a half of searching, trial, and error (note that I'm using Xubuntu and its menu settings are slightly different, but Ubuntu has similar ones):

1. Select the "Hardware drivers" item from the Applications->System menu, and activate the recommended one (three will show up; the last one was flagged as recommended here). This will install the driver, after quite a long time spent downloading and creating it. Be patient.

2. From a terminal, do "sudo nvidia-settings" and configure the display to the maximum size it allows. Then save the configuration file.

3. Copy the old xorg.conf file, which contains modelines and other settings for 1440x900, from the backup to /etc/X11/xorg.conf, overwriting the copy just saved in step 2, and reboot.

4. From the settings->display menu, select 1440x900 resolution and apply it. All now works.

Hope this helps! The forced low resolution is really a major problem for those of us with hardware that's not being recognized!

---

### Post by J.Alec.West on 2010-08-03
Jim,
.
That's true - the 1440x900 display is the native size.  But Windows allows me to reset the NVIDIA driver to display 1280x800.  Ubuntu's Linux NVIDIA driver won't.  1440x900 might be nice if I had a huge monitor on a desktop system.  But my monitor is a 17" laptop monitor - and 1440x900 is the ONLY widescreen size allowed.

I thought I'd found the answer on this page:

[http://www.highdisplay.com/graphics-card-for-linux-and-widescreen-lcd-monitors/](http://www.highdisplay.com/graphics-card-for-linux-and-widescreen-lcd-monitors/)

They suggested "editing" the xorg.conf file.  In the Screen section and Display subsection, they suggested I add this:

Modes Modes "1920x1080" "1440x900" "1600x1200" "1440x1440" "1280x1024"  "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600"  "720x400" "640x480"
EndSubSection

As you can see, my preferred 1280x800 display is listed.  However, when I tried to save the edited file, I got a warning message saying the file was "read-only" (sigh).

Hmm.  This might be a question better directed to NVIDIA customer support.  Thanks for your reply.

---

### Post by marshmallow1304 on 2010-08-03
When editing /etc/X11/xorg.conf, you need root privileges to save, so use

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by JKyleOKC on 2010-08-03
> **J.Alec.West said:**
> However, when I tried to save the edited file, I got a warning message saying the file was "read-only" (sigh).

Hmm.  This might be a question better directed to NVIDIA customer support.  Thanks for your reply.Marshmallow1304 gave you the answer. You have to set up root privileges to edit any of the files in /etc. Just be very careful when you do this, and shut down the editor ASAP after making the change and saving it.

You'll probably have to reboot after saving the change to xorg.conf before it will take effect. At least, I did here...

---

### Post by J.Alec.West on 2010-08-03
marshmallow1304,

That solved the "save" issue.  Thanks.  But, it didn't solve the display issue.  So, I removed all the lines I'd previously added and modified the "metamodes" reference to 1280x800 as shown below:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1280x800 @1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Originally, metamodes showed 1440x900 instead of 1280x800.  But, that modification didn't work either (sigh).  So, I made a post to the NVIDIA user forum thread shown below:

[http://forums.nvidia.com/index.php?showtopic=176110](http://forums.nvidia.com/index.php?showtopic=176110)

Hope someone there has an answer.  My eyes are really hurting.

---

### Post by JKyleOKC on 2010-08-03
I also have a bit of a vision problem, and found that setting the font sizes that default to 9-point in Xubuntu, up to 12 points, helps greatly in making the 1440x900 resolution usable. There's also an option in the accessiubility settings to make all the type bigger, but for me that one is over-kill...

---

### Post by J.Alec.West on 2010-08-03
Bless you, Jim (grin).  Your advice saved the day.  However, I also had to apply separate settings to Firefox to do the same thing.  This will solve my problem until the NVIDIA problem is solved.

FWIW, I did find a guy who says he solved the problem and got the 1280x800 display I'm looking for.  But I can't for the life of me figure out how he did it since his explanation is pretty brief.  Here's the URL where the "solution" is mentioned:

[http://adorio-research.org/wordpress/?p=7922](http://adorio-research.org/wordpress/?p=7922)

---

### Post by J.Alec.West on 2010-08-03
New question, same issue.  There are 3 drivers available via:

System > Administration > Hardware Drivers

They are the current version (176) and two older versions (173 and 96).  I tried all three ... same problem.  However, on the NVIDIA website, they allow for the download of a driver file:

NVIDIA-Linux-x86-256.44.run

How would I install this driver?  Does it have to be in a specific directory to install?

---

### Post by ubunterooster on 2010-08-03
> **J.Alec.West said:**
> New question, same issue.  There are 3 drivers available via:

System > Administration > Hardware Drivers

They are the current version (176) and two older versions (173 and 96).  I tried all three ... same problem.  However, on the NVIDIA website, they allow for the download of a driver file:

NVIDIA-Linux-x86-256.44.run

How would I install this driver?  Does it have to be in a specific directory to install?
How about:[quote=nvidia]Installation  instructions: Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-256.44-pkg2.run[/quote]

---

### Post by J.Alec.West on 2010-08-03
> **ubunterooster said:**
> How about:
OK ... I installed root and, after invoking .sh, tried to run the file you mentioned.  But it balked on the "-pkg2" part.  So, I just tried the filename as I downloaded it.  It recognized the file but said "permission denied."  Is this something I need to chmod?

---

### Post by ubunterooster on 2010-08-03
prefix the command with sudo

---

