---
title: "Display/font problem"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Hagavik on 2009-06-27
Installed ubuntu 9.04 just now on old my Dell Latitude c400. Pentium III, 1,2GHz, 512mb RAM. Screen/computer has worked fine in windows until yesterday.
At first the display of Ubuntu is fine but gradually letters in text/headings etx starts "disappear" behind small grey boxes or small notches of black "paint". This happens gradually more and more until text is unreadable and I'll have to re-login.
This happens in text-editors, firefox, vlc, even in the terminal
In what I've written all g's and l's are hidden behind grey boxes. artifacts? or font-driver problem?
edit: after posting; all v's are hidden behind grey boxes, while g's & l's are back to normal....
I also run a Live CD of Fedora and got something similar, but there it was even worse. All text were unreadable from begin with. 

Is this some kind of screen-driver problem or a font problem? Please help :confused:

---

### Post by QIII on 2009-06-27
Driver or hardware.  One of the two, I'd guess.  Although the specificity of affected characters is interesting.

Specs on your video card?  Is your card getting hot?  Have you cleaned out the inside of the machine lately?

What driver are you using?

---

### Post by Hagavik on 2009-06-27
No video card... I think. Computer has always been hot, but never experienced any display problems in windows.. So havent cleaned it lately.
Driver? Tried to install  a proprietary drivers by click "System-> Administration-> Hardware Drivers" but no drivers where found.... So I guess I use the Free Software version still.

---

### Post by QIII on 2009-06-27
No "card" because it has integrated graphics. I should have been more clear.

Do you know your integrated graphics specs?

Edit:  Sorry.  Not sure of your level of experience, so I should tell you how to find out, eh?

Go to Applications | Accessories | Terminal and type

lspci  (that's a small "el", not a one)

Cut and paste the results back here.

---

### Post by Hagavik on 2009-06-27
Hmmm now all text disapeared.... cant even see what I'm writing. Headers in firefox still on.. have to reboot. ;-)

---

### Post by Hagavik on 2009-06-27
Back!!! Very basic user, yes :-)
Here is the result:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
03:00.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

Thanks for you time, really.

---

### Post by Hagavik on 2009-06-27
Found some similar problems while googling on the chip-set.
[www.sternasky.com/?p=188](www.sternasky.com/?p=188)

Dont really know what it means. 
Editing this "xorg.conf" seems scary since i dont know editing in linux. Hear about pico but never used it....

---

### Post by LewRockwell on 2009-06-27
At least you've found something to try out to solve your problem for the time being

You can always keep your eyes open for a replacement

keep us posted on your progress

---

### Post by Hagavik on 2009-06-27
Found at string on: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)
**Giving the final hint....**
Have tried out to edit the xorg.conf by:
sudo pico \etc\X11\xorg.conf
*<< then add the following in the "*Section "Device""
              [B]Identifier      "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
              Driver          "intel"
       Option "AccelMethod" "EXA"
       Option "MigrationHeuristic" "greedy"
       Option "ExaNoComposite" "false"[/B]
EndSection
<<*exit  and login.*

Works fine!!! [B]:-)
[/B]

---

### Post by QIII on 2009-06-27
I'm glad it worked!

Sorry I was out of the loop for a while.  I was doing some testing on my Karmic machine.

Could you please go back up to your original post and edit it, putting "SOLVED:  " in front of the title?

That will give others a chance to know what you did.

Happy Ubuntuing!

---

