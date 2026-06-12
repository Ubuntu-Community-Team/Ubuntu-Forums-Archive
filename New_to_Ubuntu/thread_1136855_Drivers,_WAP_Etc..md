---
title: "Drivers, WAP Etc."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by TehPriest on 2009-04-25
OK Brand new to all this and not a geek so I need plain English help please.  I thought I would try Linux again after many years to see if it had become more user friendly to the novice like me. I am not a big fan of MS so I though it may be time at last to swap out.

To be safe I tried it first (9.04) on my Toshiba laptop/tablet P3500E. 1 Gig of Ram 1.3Ghz processor and 80 gig HD so no problem with spec.  Installed Ubuntu but had to start in safe graphics mode to get full screen display instead of a sort of letterbox.

Problems are that two things are not performing properly;
The aforementioned display. It gives me the option of 800x600 but not the 1024x768
The Wireless connection which uses WAP enryption that I do not want to change. Atheros drivers used in XP.

Both these work perfect under Win XP

So. How do I go about sorting out the screen driver and how can I use WAP as, reading the forum, no one has been able to sort that one yet.

It is a shame as I am already using the Mozilla offerings in place of MS on XP at the moment so the natural progression would be to use Linux as well but if I cannot sort these small things out it will be back to XP for me :-(

---

### Post by Elfy on 2009-04-25
Have you looked in Hardware drivers - in the system admin menu - start there for both - are the video and wireless recognised?

Before anyone can really help though we will need to know what hardware it is - open a terminal it's in Applications >Accessories.

Run this command

```
lspci
```

Post the result here.

---

### Post by stwschool on 2009-04-25
Any idea what your graphics card is? Also is there an option for 1024x768 if you go to System -> Preferences -> Display?

---

### Post by Sidewinder1 on 2009-04-25
First of all WELCOME!
I can't really help with the WAP problem; but when you go into networking and try to connect it "should" ask for a WAP key, just put in and it should work.
The display issue probably results from a proprietary driver. Not to worry; try clicking on System--->Administration--->Hardware Drivers...; input your password. You then should find some reference to using proprietary drivers that you can click on to solve the problem.
HTH,
Side

---

### Post by TehPriest on 2009-04-25
> **stwschool said:**
> Any idea what your graphics card is? Also is there an option for 1024x768 if you go to System -> Preferences -> Display?

I'll answer this first as it is the easiest. I will have to copy the file for the other stuff onto a usb then post it from this machine so it will take a few minutes.

Video is Trident CyberALADDIN-T graphics controller, 16mb external UMA memory. supports up to 1600x1200, 64k colours but standard is 1024x768.

WIFI 802.11 a/b Atheros

Edit:
Forgot to say. Yes it does find the wireless and the broadcast SSID from the router and I have set it up in netwrok connections as a WAP but that does not work. When I right click the network icon it shows the router but when I try to connect it either does not give me an option for WAP or if it does it keeps asking me for the passphrase over and over untill it fails..


OK I will get the other info now and post in a minute or two.

Thanks for the fast replies.

---

### Post by TehPriest on 2009-04-25
> **Sidewinder1 said:**
> First of all WELCOME!
I can't really help with the WAP problem; but when you go into networking and try to connect it "should" ask for a WAP key, just put in and it should work.
The display issue probably results from a proprietary driver. Not to worry; try clicking on System--->Administration--->Hardware Drivers...; input your password. You then should find some reference to using proprietary drivers that you can click on to solve the problem.
HTH,
Side

Answer to the above is "No proprietary drivers are in use on this system"

Here is the display for the lspci command

tablet-pc@ubuntu:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 41)
00:0c.1 USB Controller: NEC Corporation USB (rev 41)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
tablet-pc@ubuntu:~$ AD


Thanks again.

---

### Post by TehPriest on 2009-04-25
Just ran a report and got the output I have uploaded here.

[http://www.landrover6pot.org/tmp/submission.xml.html](http://www.landrover6pot.org/tmp/submission.xml.html)

Hope this is of help.

---

### Post by TehPriest on 2009-04-25
Just noticed another thing. When I go to display settings it says my monitor is unrecognised. Could this be the problem with the screen size?  I notice several people are having this problem in the posts.

---

### Post by TehPriest on 2009-04-25
No ideas?  Anyone?

---

### Post by Favux on 2009-04-25
Hi TehPriest,

This thread has a Toshiba Protege 3500 with the same problem in Intrepid.  He fixed it, basically using the xorg.conf in post #13.  Take a look at the thread:  [http://ubuntuforums.org/showthread.php?t=1102194](http://ubuntuforums.org/showthread.php?t=1102194)

Because you are in Jaunty you probably only need the video stuff.  The keyboard, mouse, Synaptics, Wacom, and "ServerLayout" sections are probably not wanted by Jaunty.  So compare it to the xorg.conf you have and see if it suggests anything.

Hope this helps.

---

### Post by TehPriest on 2009-04-25
Thanks but I beat you to it by seconds :)

Now have full screen and as you ssay only use the video/monitor bit (or it screws up completely) copy and paste it into xorg.conf (after backing up though 9.04 has an auto recover as well very handy :oops:

The part in question;

> Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    0
    Vendorname    "Trident"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1024x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection

Section "device" # 
    Identifier    "device1"
    Boardname    "Trident CyberBlade (generic)"
    Busid        "PCI:1:0:0"
    Driver        "trident"
    Screen    1
    Vendorname    "Trident"
EndSection

Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection

Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSectionNow can anyone help me solve the WAP problem and prevent me returning to XP ???

---

### Post by Favux on 2009-04-25
Hi TehPriest,

Nice job!  Though if you check the xorg.conf I linked you to you'll see the video part's much simpler.  I guess it partly depends on what version of the Xorg trident driver you have.

There's several threads on getting Atheros wireless to work.  But since it keeps asking for your password I'll link you to this thread:  [http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)  I suppose it's possible a little editing with Gconf editor could fix your problem too.

---

### Post by TehPriest on 2009-04-25
You are again correct and I have now tried the one you pointed to.  It works well except the monitor is still shown as unknown and there is no rotation available.  The WPA suggestion refers to version 8 and I am not sure where to look in 9.  All in all a very disappointing day as I will now have to return to Windows XP to have a useable laptop. Maybe in a few years time they will make it easier for a non techy like me.  Funny thing is when the lappy/Tablet was new tere was a Linux option using a version now taken over by Mandriva called Lycoris. I believe this actually provided what is needed but is no onger available :(

Thanks everyone for your help on this.  I have learned a lot. ):P

---

