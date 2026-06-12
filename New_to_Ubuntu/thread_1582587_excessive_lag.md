---
title: "excessive lag"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Ballbrekr on 2010-09-26
Let me start this off by saying I love Linux.

Got that out of the way.

I have some troubles here and not sure where to turn.  I will describe them best i can.

[B]_description:_
Lucid Lynx has become slow and laggy and sometimes unresponsive to commands.  World of Warcraft is getting about 9 frames per second in Dalaran (for those who know that place).  To initialize the game takes a considerable amount of time (15-30 seconds).  [/B]

Knowing that, I do want to say, please help.  I do not like windows.  HELP ME PLEASE!

Here are some solutions I have tried to correct the issue.  This has been going on for a little over four weeks now.  Going on so long now I have WoW on usb stick to help get files transferred.

_**Solutions tried:**_
[B]All versions of Wine have been installed and tried.  Play on Linux has been tried and removed.  CrossOver trial version is currently installed and working (still same old lag issue).  My ATI radeon HD 5770 card has been replaced with an Nvidia GT240, and then swapped back after that failed ( oh and those drivers also very difficult to install i.e. kill all this  then install and then restart something else then you can configure it after the reboot if it reboots to gui).  Then went back to my original ATI card.  ATI drivers are even worse, download latest driver and install them ( ok fine but after that you cant make any adjustements because the config app wont work).  Finally figured out (after 7 fresh installs) that fglrx-modalias update is garbage.  So in short more than 4 weeks have gone by, ive used 3 different video cards( onboard video also), all versions of wine, and have used the downloaded and the recommended drivers for all of those.

[/B]Nothing in 4 weeks has brought me closer to my goal.  My goal is to have Linux as an Operating system and be able to play World of Warcraft at a decent frame rate (more than 9 frames per second).

[B][U]This is what I am working with:
[/U]Release version Ubuntu 10.04
Kernel 2.6.32-24 generic
Gnome 2.30.2

hardware:
ATI radeon hd5770
AMD phenom 9150e Quad core
8 gig mem

$top =
with 1 program running I have 2 gig of memory being used

I have glxinfo | grep rendering
this is the result of Unigine tropic:

[/B]**Tropics Demo v1.3**

  FPS:**47.9**
 Scores:**1207**
 Min FPS:**13.0**
 Max FPS:**100.4**
  **Hardware**

  Binary:Linux 32bit GCC 4.3.2 Release May 20 2010
 Operating system:Linux 2.6.32-24-generic x86_64
 CPU model:AMD Phenom(tm) 9150e Quad-Core Processor
 CPU flags:1800MHz MMX+ 3DNow!+ SSE SSE2 SSE3 SSE4A HTT
 GPU model:ATI Radeon HD 5700 Series 3.2.9756 Compatibility Profile Context 1024Mb
  **Settings**

  Render:opengl
 Mode:1920x1080 fullscreen
 Shaders:high
 Textures:high
 Filter:trilinear
 Anisotropy:4x
 Occlusion:disabled Reflection:enabled
 Refraction:enabled
 Volumetric:enabled

sorry bout the fonts there.  So if this tells me anything, I think it says that my video card and drivers are pretty good.  Oh also I have done all the WTF.conf file tweaks and the registry tweaks as well.  I am at wicks end there is no more information to look up on the internet that i have not tried.  Maybe im just doing something wrong or maybe this guppy needs to go back the kiddy pool.  Any information or something new to try would be great any new directions to move toward would be great.  Also others that i know using linux have no problems with closely similar hardware.  Thank you for your time.

Very respectfully and sincerely,
Ballbrekr

---

