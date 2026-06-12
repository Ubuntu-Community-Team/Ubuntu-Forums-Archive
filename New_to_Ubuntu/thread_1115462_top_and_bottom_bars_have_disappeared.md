---
title: "top and bottom bars have disappeared????"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Larryjb on 2009-04-03
All was going well, until the top and bottom "bars" just disappeared.  This is a really old computer and I was trying a suggestion to correct a problem with boot up.  I added acpi=force to the boot up command (temporary, I thought) and when it booted up, nothing at the top or bottom.  Rebooted again, but still gone. Any ideas about how to fix this?  I am thinking I may need to reinstall.

---

### Post by SunnyRabbiera on 2009-04-03
There should not be any need to re install, by the way we call these bars "panels"
:D

---

### Post by theozzlives on 2009-04-03
> **SunnyRabbiera said:**
> There should not be any need to re install, by the way we call these bars "panels"
:D

Tell him how to fix it. First try moving the mouse to the top or bottom, make sure autohide isn't on.

---

### Post by Larryjb on 2009-04-03
> **theozzlives said:**
> Tell him how to fix it. First try moving the mouse to the top or bottom, make sure autohide isn't on.

No luck, mouse, goes to top and bottom side to side and just sits there.

---

### Post by Ms_Angel_D on 2009-04-03
try this then

1)ctrl-alt-f1 to drop to terminal
2)log in using your normal username and password
3)then try this command: *sudo apt-get install xfce-panel* (**unless your running xfce4** then it would be *sudo apt-get install xfce4-panel*)
4)Then ctrl-alt-f7 to get back to the GUI.

[edit]
Edited for Xfce
[/edit]

---

### Post by theozzlives on 2009-04-03
Try reverting back to the backup menu.lst (if you used gedit it will be menu.lst~).

---

### Post by SunnyRabbiera on 2009-04-03
He said he is running Xubuntu folks

---

### Post by Larryjb on 2009-04-03
> **MetalHellsAngel said:**
> try this then

1)ctrl-alt-f1 to drop to terminal
2)log in using your normal username and password
3)then try this command: *sudo apt-get install xfce-panel* (**unless your running xfce4** then it would be *sudo apt-get install xfce4-panel*)
4)Then ctrl-alt-f7 to get back to the GUI.

[edit]
Edited for Xfce
[/edit]
No joy

---

### Post by Ms_Angel_D on 2009-04-03
> **Larryjb said:**
> No joy

sorry :( I hope you can get some help with this.

---

### Post by Larryjb on 2009-04-03
> **theozzlives said:**
> Try reverting back to the backup menu.lst (if you used gedit it will be menu.lst~).
no comprehindo!  Until yesterday, I had never heard of xubuntu, and just today I learned how to pronounce it.  Mucho hand holding will be greatly appreciated.

---

### Post by Larryjb on 2009-04-03
> **MetalHellsAngel said:**
> sorry :( I hope you can get some help with this.

re-install is looking pretty good!

BTW got back this message:
xfce4-panel is already the newest version
0 upgrades, 0 newly installed, 0 to remove and 194 not upgraded.

---

### Post by JKyleOKC on 2009-04-03
Can you right-click on the desktop and get a menu to pop up? If you can, select "Settings" from it to get a large window with icons for various settings. One of these is "Panel" and if you open it, you can configure one of the two panels at a time.

If you don't get the menu, perhaps a reinstall would be the simplest way out since apparently it's a very new installation without much cusomizing to be lost...

---

### Post by Larryjb on 2009-04-03
> **JKyleOKC said:**
> Can you right-click on the desktop and get a menu to pop up? If you can, select "Settings" from it to get a large window with icons for various settings. One of these is "Panel" and if you open it, you can configure one of the two panels at a time.

If you don't get the menu, perhaps a reinstall would be the simplest way out since apparently it's a very new installation without much cusomizing to be lost...

when I right click on the DT i get a small gray square.  that won't go away until i I right click again. Right clicking again makes the square appear again.

---

### Post by lisati on 2009-04-03
From a terminal (I forget for the moment what to right-click on the Xubuntu desktop) type in
```
xfce4-panel &
```
and the panels should "magically" re-appear

---

### Post by Larryjb on 2009-04-03
> **lisati said:**
> From a terminal (I forget for the moment what to right-click on the Xubuntu desktop) type in
```
xfce4-panel &
```
and the panels should "magically" re-appear

I pressed ctrl-alt-f1 to get a terminal session,
logged in and typed xfce4-panel &
and got the following:
[1] 4691
larry@xubuntu:~$
(xfce4-panel:4691): Gtk-WARNING **: cannot open display:

Then I pressed ctrl-alt-f7 and returned to the desktop...

no magic or joy just a desktop without panels:(

---

### Post by Larryjb on 2009-04-03
Thanks everyone.  I am going to bed now, will try some more tomorrow.

---

### Post by theozzlives on 2009-04-04
Where did you add ASCPI=force?

---

### Post by ScoobyDan on 2009-04-04
To get the run window, press

ALT & F2

then type

```
xfce4-panel
```

and click on "Run".

Job done!

Daniel

---

### Post by Larryjb on 2009-04-05
Well, I gave up and reinstalled.  Now I have a whole new problem.
I pretty much had everything back to where I had it before I lost the panel.  I decided I needed to install some plugins into firefox.  I thought I needed the adobe reader plugin, so I figured I needed to install adobe reader first.  I got it downloaded to the desktop (some sort of .bin file)  I double clicked on it thinking would run it, but it wanted me to decide what program use to run it.  I looked at the possibilities I was presented with and thought Software solutions was a good choice.  After i clicked that, the system went into a tizzy.  The program displayed a partially painted window and the hard drive just went crazy reading.  This went on for over 30 minutes and I decided I should just reboot.  I managed to get the shutdown window to show up and a pressed restart.  When it restarted, it got as far as light blue screen with the mouse pointer in the middle.  The hard drive is reading like crazy but nothing else is happening.  It is like it is still trying to run that software solution program that I tried to kill with restart.  Does xubuntu try to restore the system to what it was doing when it it was last shut down?  
Anyway this is really getting frustrating.  I think I have two major things working against me.  1) My only point of reference to how use xubuntu is Microsoft windows, so that is how I approach things.  2) This computer is just too old and slow to run a modern graphical operating system.

---

### Post by Larryjb on 2009-04-05
> **theozzlives said:**
> Where did you add ASCPI=force?

I hit esc during bootup and then added it to the boot command.

---

### Post by Larryjb on 2009-04-05
Update:
I was able to get the system working again by powering off by hitting the hardware reset button. (These old computers had that button, remember?)

Is there some secret way of installing a .bin file I download from the internet?  Why can't I just double click?

---

### Post by theozzlives on 2009-04-07
go to the terminal and type:
```
chmod +x <filename>.bin
```
then:
```
./<filename>.bin
```

---

### Post by FMDCER on 2009-04-26
> **lisati said:**
> From a terminal (I forget for the moment what to right-click on the Xubuntu desktop) type in
```
xfce4-panel &
```
and the panels should "magically" re-appear
Re: top and bottom bars have disappeared????
From a terminal (I forget for the moment what to right-click on the Xubuntu desktop) type in
Code:

xfce4-panel &

and the panels should "magically" re-appear
__________________
Toshiba A100, Celeron M, 222Mb, Ubuntu 9.04
Toshiba M200, Intel Dual Core T5450, 2Gb, 64-bit 9.04 & Vista Home Premium
Compaq SR1520AN desktop, Sempron 3200+, XP+9.04
Digital Venturis FX5133, Pentium, 64Mb, Win98SE

"The Ubuntu Counter Project - user number # 15782"
A genuine Kiwi | An unashamed plug| YouTube channel 

I used this trick as I too lost the top and bottoms bars. Needless to say, I was in a panic but it worked !. Also might suggest backingup often since one never knows (just like the bars disappearaing suddenly) what can happens. Thanks everyone

Ben

---

### Post by skalrynd on 2009-07-07
> **ScoobyDan said:**
> To get the run window, press

ALT & F2

then type

```
xfce4-panel
```

and click on "Run".

Job done!

Daniel

Was having same problem.  This worked for me!!!  Thanks! :)

---

### Post by RobHK on 2009-07-07
> **Larryjb said:**
> Update:
I was able to get the system working again by powering off by hitting the hardware reset button. (These old computers had that button, remember?)

Is there some secret way of installing a .bin file I download from the internet?  Why can't I just double click?

Larry: As you're new to Linux I'd, for the moment, only install stuff available on the repositories. There's a quite serviceable PDF viewer called Evince, and it should be installed by default, I think. When you try to open a PDF in Firefox it will open a window for Evince. I think this is preferable anyway, given the number of times I've tried to open a big PDF in FF in Windows and have my system lock up for 2 minutes.

If your computer is too old and slow for Xubuntu, try installing the ultra-lightweight Fluxbox Desktop Manager. Go to Synaptic Package Manager and select and install it there. When it's installed, log off. At the log-in screen, near the bottom, it says "Session". Click there and select Fluxbox. Then log in. To get the menu. rightclick anywhere on the desktop. 

See how you like it. I'm using it at the moment and have found it difficult to set wallpaper. If you like it and want to stick with it I'd suggest a clean new installation of the Fluxbox version. (Wallpaper wasn't an issue when I last did this.) Not sure if it's available for Ubuntu proper, but it certainly is for Linux Mint, which is just Ubuntu with a few minor additions and changes.

Finally, if your computer is just too old and slow for any of this, try Puppy Linux, which is designed for just such boxes.

---

### Post by Ugluk on 2009-07-07
Open Synaptic, find xfdesktop package, and tell us which version does it have.

---

