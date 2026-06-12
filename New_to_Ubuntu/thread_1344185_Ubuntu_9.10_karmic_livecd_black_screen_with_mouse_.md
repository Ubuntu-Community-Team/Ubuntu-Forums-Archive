---
title: "Ubuntu 9.10 karmic livecd black screen with mouse pointer. Monitor is Compaq P1100 CR"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by 22ppc on 2009-12-02
(Also happens with Linux Mint 8 Helena)

Preamble:
I am new to forums except as a reader, so if I violate any protocols, help me out by letting me know.

Equipment:
ASRock P4i65GV with Integrated video Intel 82865G

What happened:
A livecd boot seemed to go well until done, then we are left with a black screen with a tiny mouse pointer in the center of the screen. (Linux Mint 7 Gloria (based on ubuntu intrepid) didn't have this problem)

CAUSE:
Resolution is set at 95.2kHz / 60Hz	2048 X 1536
This is above the specified maximum resolution for this monitor of 1920 X 1440 @ 75 Hz (From Service Manual)


Work Around:
We could choose F4-Safe Graphics Mode at the boot screen, but we prefer the following:



Execute the following key sequence "in the dark"

ALT + F1			open the Application menu
RIGHT Arrow twice		skips across to SYSTEM menu
DOWN arrow			selects Preferences from SYSTEM menu
RIGHT arrow			we are at "About Me" in Preferences menu
DOWN arrow 5 times		we are at Display in Preferences
ENTER				opens "Display Preferences" dialog
TAB 3 times			we are at the Resolution drop box
DOWN arrow x times		we used 4 times to select 1600 X 1200
TAB 3 times			we are at the APPLY button
ENTER				applies the new resolution

We should no longer be "in the dark".
Click "Keep this Resolution"

If you now go ahead and install Ubuntu and then boot from the hard drive, you will need the key sequence again.
And again whenever a new user logs on for the first time.

For Linux Mint 8 Helena users the key sequence is:
CTRL + SUPER (Windows key)
SHIFT TAB
LEFT arrow
ENTER
TAB 3 times
DOWN arrow x times		we used 4 times to select 1600 X 1200
TAB 3 times
ENTER

Should no longer be "in the dark".
Click "Keep this Resolution"

PS: I have 2 other computers, 5 different cards, and 3 different monitors. I will do some experimenting and if the results are interesting I will post here again.

---

### Post by 22ppc on 2009-12-02
I did some more testing.

_Fresh install of Windows XP_
Identifies the monitor as:
 Plug and Play Monitor
Driver:
  Microsoft 2001-06-06  Version 5.1.2001.0
Details-->Device Instance:
  Display\CPQ1337\5&351DDC64&0&224688&01&00
infpath:
  monitor.inf
inf section:
  VESADDC.Install
icm profile
  (none)
Maximum selectable resolution:
 1920 X 1440

_Fresh install of Windows XP with Compac drivers installed_
      (sp32484.exe)
Identifies the monitor as:
 Compaq P1100 CRT
Driver:
  Compaq 2006-03-15  Version 4.0.0.0
Details-->Device Instance:
  Display\CPQ1337\4&2744FCE&0&80861100&00&02
infpath:
  oem7.inf
inf section:
  P1100.Install
icm Profile:
  CPQP1100.icm
Maximum selectable resolution:
 1920 X 1440

Testing below done by booting from liveCD
_Asus A7v8X-MX SE Integrated  VIA/S3G UniChrome IGP_
The monitor OSD (On screen display) says it is running at
1600 X 1200 @ 60Hz. The desktop doesn't fit on the screen. If we move the mouse to the bottom of the screen, it scrolls and we can see the bottom panel. When we move the mouse to the top of the screen it scrolls the other way and we can see the top panel. When we open "Display Properties" the Resolution box has us at 1856 X 1392 @ 60 Hz.
(Maximum available) We change this 1600 X 1200 @ 60 Hz to match the monitor OSD. Now the screen is normal. (Linux Mint 8 behaves the same)

_Asus A7v8X-MX SE Radeon 8500 AGP_
The monitor OSD says it is running at 95.3kHz / 60. (We know this is 2048 X 1536. On the top Panel, the Applications and System buttons look like they are covered with fabric. Same for Power button at right end of the Panel. In display Preferences we change to 1600 X 1200 @ 75Hz. Now the panel appears normal but the wallpaper and icons are gone, replaced with a black screen. Change Visual Effects to None, the wallpaper and icons return. (Linux Mint 8 works similar, except we can turn on Visual effects without losing wallpaper and icons)

_Asus A7v8X-MX SE NVIDIA GeForce FX5200 AGP_
Starts at 1920 X 1440 @ 75 Hz. This is the maximum resolution available in Display Preferences. (And is the Max Res listed by Compaq)
Display Preferences lists the monitor name as "Unknown" In tests above it was listed as "Compaq 20"". Everything appears normal. (Linux Mint 8 is the same)

_Asus A7v8X-MX SE NVIDIA GeForce MX400 AGP_
Same result as for the FX5200 card.
we also used this equipment to test 3 other monitors:
  Samsung syncmasters 955df, 793 mb, 753df. 
  955df:
 Starts at 1280 X 1024 @ 75 Hz. The OSD says this is recommended. Change to maximum resolution in Display Properties of 1792 X 1344. The scrren goes black except for the desktop icons which are on a patch of the wallpaper. The other two monitors work OK. We start at the maximum available resolution of 1152 X 864 @ 75Hz. Samsung recommends 1024 X 768 @ 75Hz.

Also tested:
_HP m7277c with Radeon X600 PCI-E_
Windows 7 RC:
  Runs at 1920 X 1440 (Maximum available) Monitor id's as Compaq P1100.
  Works OK
Windows XP SP3:
 Runs at 1920 X 1440 (Maximum available) Monitor id's as PnP Monitor.
  Works OK
Ubuntu Karmic and Mint Helena:
  Works OK at start of 2048 X 1536 @ 60HZ

Comments:
1
If Linux starts with a resolution higher than the maximum resolution for that monitor there is likely to be trouble.
2
Windows never exceeds the maximum resolution (Except for Win7) and never had trouble.
3
If you are in your parts bin looking to assemble a Linux box, you may want to pick a NVIDIA card.
4
I think the resolution to be the default for a given monitor ought to be the highest Preset that monitor has. (The first thing anyone using a P1100 is going to do is turn down the 2048 X 1536 resolution. At least he will if he is over 30!)

Questions:
1In what file is the information for monitor stored?
2
Is it user-modifiable?

---

