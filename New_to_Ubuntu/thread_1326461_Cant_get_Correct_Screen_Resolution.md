---
title: "Cant get Correct Screen Resolution"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Christoff228 on 2009-11-14
Hi All,

I am getting close to having a new Ubuntu laptop, everything seems to be ok so far the only problem I have now is that I can't get the correct screen resolution. After install it set to 1600 x 1200 which looked great on the desktop, until connectedto firefox and that resolution is to high to view web pages makes them too big for my screen. When I alter the display settings to any of the others i just get a totally unseeable screen. Luckily in defaults back to the 1600 x 1200 after about 30 secs. Can anyone help me to solve this issue as then my installation will be complete and will be a very happy ubuntu convert. My laptop has no extra graphics card, and is just what is onboard, the motherboard and processor are Via C7-M processor 1.5 GHz.

---

### Post by jbrown96 on 2009-11-14
Sorry to hear about your problems. I need some more information from your system and little clarification about your problem. 
Please post the output of these commands (apps-->accessories-->terminal)
Hardware info: ```
lspci
```


So the resolution looks good until you open Firefox? Then the resolution re-sets to something much lower (making everything really big), or is it just Firefox that looks messed up? If you try to change the resolution at this point, what does it say the resolution is? 

I'm not sure this will work, but can you post some screenshots? Press the PrintScreen button on your keyboard, and a save file dialog should appear. Just save them, and then you can attach them to a forum post. Try taking one with the resolution normal and another with it messed up.

---

### Post by Christoff228 on 2009-11-14
Hi,

No resolution is set to1600 x 1200 by default the only reason that this is a problem and the only time you can tell is when you open Firfox asthe webpage is all moved to the right. I ran the code you suggested however I can't paste output because cant access the forums on the laptop due to the screen problem in firefox. So have run the command on laptop, and am using my still windows (boo) desktop to post my issues. I will try and type below what I was given.

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 as above
00:00.2 as above
00:00.3 Host bridge :VIA Technologies Inc. PT890 Host Bridge
00:00.4 same text as .0 .1 &.2
00:00.7 as above
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE Interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE Interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 as above
00:10.2 as above
00:10.3 as above
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA Bridge VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

Think I got it all correct hope this helps thanks for all your help

---

### Post by Christoff228 on 2009-11-14
With regards your other queries if i go into the display edit area it says 1600 x 1200 (4:3) any thing I then try to change it to makes the screen unreadable. So I think this is the resolution that is set from the install

---

### Post by Christoff228 on 2009-11-14
Hi I have just been checking the VIA website as well and when i try to download supported drivers there is no Ubuntu 9.10 only Ubuntu 9.04 could this be causeing my problems. Should I install 9.04 see what happens and then upgrade to 9.10 once drivers are supported

---

### Post by bacardiandwatermelon on 2009-11-14
If it is just firefox you are having issues with then I would leave it at that res and just use the firefox zoom feature, not sure if you can save the zoom as a default. The hot keys are "Ctrl and +" to zoom in, "Ctrl and -" to zoom out, "Ctrl and 0" to return to default.

---

### Post by Christoff228 on 2009-11-15
Thanks for the tip will give that a try I totally agree if it not totally broke why try and fix. Heres hoping the zoom works

---

### Post by Christoff228 on 2009-11-15
hi Firefox zoom didnt work even on max zoom out makes the page still un usable is way too small to read and still cant seethe scroller at side. Does anyone have any other ideas was trying to get xp back and that not even achievable. Feel like I have totally trashed my laptop :-(

---

### Post by Sir Jasper on 2009-11-15
Hi,

My resolution also defaults to 1600x1200 on booting, but I am able to reset it to 1400x1050. I do realise that your problem is different (as you cannot at the moment try other resolutions) and I only mention this because at this resolution I can see and use the vertical scroll bar in Firefox and it seems to work quickest and best at that setting.

When your problem is resolved you may find the Firefox add-ons ¨Default Full Zoom¨ and ¨Image Zoom¨ to your liking.

My regards

---

### Post by Christoff228 on 2009-11-15
Hi 

Many thanks I am able to change my resolution but when i change to 1400 x 1050 the screen becomes unreadable (glad it defaults back or be doing lots of re-installs) I have treied all the different resolutions and the only one that enables me to see the desktop is the 1600 x 1200 which unfortunately doesnt let me use the web, plus i don't have the bottom panel or the time top right think both of these are off my screen due to this resolution. I am at hair pulling time and think I may have the only machine unable to run Linux. Thank my lucky stars kept my desktop on XP for time being so I am able to post here to get some assistance

---

### Post by Sir Jasper on 2009-11-15
Hi,

Just with the remote chance it may help a little is there a small improvement if you unmaximize or resize your Firefox screen and can you use your arrow keys instead of the scroll bars?

These are only shots in the dark so not much point in answering.  

Good luck

Added:

One final thought - might it be of temporary help if you were to centre your top and bottom panels?

---

### Post by DiamondBuntu on 2010-03-18
I am having the exact same problem and cant see to solve this issue.
my screen resolution is set at 1600x1200 and whenever i try to change to a lower resolution the screen gets distorted and unable to view anything on my desktop.
i tried removing xserver-xorg and re-installing over but still have the same issue.

---

### Post by pj_kare on 2010-03-19
You may need to set a resolution manually.

My monitor is suppose to display at **1366x768** (it's native resolution). Ubuntu sets it at this from Install, which is correct, but anything on the right side of my screen (trash bin, scrollbars etc) are mostly off the screen. After installing nvidia drivers I have to manually change/edit 1366 to 1360 to correct it. Hope this is of some help.

---

