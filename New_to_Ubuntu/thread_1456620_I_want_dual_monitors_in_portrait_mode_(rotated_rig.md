---
title: "I want dual monitors in portrait mode (rotated right 90 degrees)"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by ddbal on 2010-04-17
GOAL:
 I want dual monitors in portrait mode (rotated right 90 degrees). I am having trouble.  
 

 SYSTEM DETAILS:  
 Monitors: Two Samsung 2443BW LCD (1920 x 1200).  
 Motherboard: GIGABYTE GA-MA790GP-DS4H &#8211; AMD 790GX chipset  
 Video &#8211; Integrated graphics: Radeon HD 3300X w/128 MB sideport memory.
 Note: Board has both DVI and VGA ports  
 OS: Ubuntu 9.10 AMD64 - freshly installed  
 

 WHAT WORKS:  
 Dual monitors works by simply configuring display settings for regular (non-rotated) mode. Works for both mirrored and non-mirrored settings. 
 

 WHAT DOESN'T WORK:  
 Portrait mode (rotated right 90 degrees) does not work - not for a single monitor or dual monitor.  
 

 WHAT I HAVE TRIED:  
 
[LIST=1]
[*]I learned that in my xorg.conf 	file the maximum virtual display is 3840 x 1200. Because of the 1200 	limitation I can not rotate the display to 1200 x 1920 (1920 exceeds 	1200).
[*]I changed the virtual display in 	xorg.conf from 3840 x 1200 to 3840 x 1920. The rotate feature 	appears in the display preferences menu. When I click rotate-right 	=> apply the screen turns black. I must press reset on the 	computer to restore the display.
[*]I reduced the resolution to 1024 x 	768. The rotate feature appears in the display preferences menu. 	When I click rotate-right => apply the screen turns black. I must 	press reset on the computer to restore the display.
[*]I tried to rotate the display with 	xrandr in a terminal window by typing the following:

[LIST=1]
[*]xrandr --output DVI-0 --rotate 		right
[*]I get the error &#8220;crtc 0 failed&#8221;
[/LIST]
 	
[*]I tried downloading new ATI video 	drivers. I installed EnvyNG from Synaptic. EnvyNG says I already 	have current drivers (8.660-Oubuntu4).
[/LIST]
 

 I am out of ideas.
 

 Any help would be appreciated.

---

### Post by steveneddy on 2010-04-17
Possible solution:

[http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989](http://forums.amd.com/forum/messageview.cfm?catid=310&threadid=110989)

---

### Post by brucewagner on 2010-04-17
Before you go crazy with this...

Try the 32-bit Lucid 10.04 (beta2 is now available).

It seems to do this automagically -- out of the box!

I installed it and discovered this ability by accident.

System --> Preferences --> Monitors  ...then select "show monitors in panel"  ...gives you all the options.

PS - I recommend always using the 32-bit version of Ubuntu rather than the 64-bit version.  More reliable. Bugs are fixed faster.

PPS - The proprietary ATI drivers screwed everything up.  The built-in default video drivers in the 10.04 Ubuntu work flawlessly and give me more features and options than I used to have with the proprietary drivers in 9.10

---

### Post by Padakwaak on 2010-05-17
I was unable to get my dual screen setup in the correct orientation (1st screen rotated CW and 2nd rotated CCW). Eventually I found the solution (in the link that steveneddy psoted): you can use the Catalyst Control Center (amdcccle) to rotate the screens...

My setup is as follow:
2x Samsung 2333 @ 1920x1080 (connected with DVI & HDMI respectively)
ATI Radeon HD5670
Ubuntu Lucid Lynx x64 with ATI Driver 10.4

Update:
After I restarted, my screens were rotated 180'. Rotating them back using System > Preferences > Monitors solved the issue and it stayed that way even after restarting.

---

