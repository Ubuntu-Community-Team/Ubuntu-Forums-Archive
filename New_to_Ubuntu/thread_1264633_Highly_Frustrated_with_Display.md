---
title: "Highly Frustrated with Display"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by cedarview on 2009-09-12
I have spent days trying to get a display of 1280x768 within a screen of 1280x768

I have an HW19D display (HANNS-G) and a VIA s3g Unichrome Pro 1GP graphics card.

Currently I have a workspace (desktop) of 1080x768 but the screen is still 800x600. The last time I use a resolution of 800x600 was in the last millennium. Oh sorry I believe my iPAQ uses that resolution

I have seen adverse comments about windows in these forums but I have never had problems about getting full resolution and display size when using windows.

Well I am new to UBUNTU and would appreciate some help in solving this problem.

I have not loaded any additional graphics drivers.

Assume I am an idiot 

My current xorg.conf is 
-----------------------------------------
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    SubSection "Display"
        Depth 24
        Virtual 1280 768
        Modes "1280x768@75" "1024x768@75" "1024x768@60" "800x600@60" "640x480@60"
    EndSubSection
EndSection

Section "Device"
    Identifier "Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "True"
EndSection
-----------------------------------------------------------------------------

I did manage to get the Bootup Splash screen to a good resolution

:confused:

---

### Post by mac9416 on 2009-09-12
Hey, cedarview,

> I have seen adverse comments about windows in these forums but I have never had problems about getting full resolution and display size when using windows.

Actually, I never had until I reinstalled XP once. I then had to search down all the proper drivers. Then I installed Win7 and had to install the drivers in a compatibility mode. I couldn't help but show off to the person I was doing all this for when I booted the live CD and the resolution was right.

I assume that the problem is that you haven't installed proprietary drivers. The easiest way to install proprietary drivers is go to System>Administration>Hardware Drivers

Good luck
-mac

---

### Post by mgranet on 2009-09-12
> **cedarview said:**
> 

My current xorg.conf is 
-----------------------------------------
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    [B]SubSection "Display"
        Depth 24
        Modes "1280x768"
    EndSubSection
EndSection

Section "ServerFlags"
    Option    "DontZap"    "True"
EndSection[/B]
-----------------------------------------------------------------------------


Try editing your xorg.conf to match the bold text. (Make sure to back up the old one!) Most LCD panels operate at 60Hz natively, so it may be a problem of trying to set the refresh too high.

---

### Post by cedarview on 2009-09-16
This puts me back to the start with 800x600
:(

---

### Post by cedarview on 2009-09-16
> **mac9416 said:**
> Hey, cedarview,

I assume that the problem is that you haven't installed proprietary drivers. The easiest way to install proprietary drivers is go to System>Administration>Hardware Drivers

Good luck
-mac

Just get
"No proprietary drivers are in use in this system"
 then just have HELP and CANCEL buttons available

as if I didn't know
:confused:

---

### Post by mapes12 on 2009-09-16
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

