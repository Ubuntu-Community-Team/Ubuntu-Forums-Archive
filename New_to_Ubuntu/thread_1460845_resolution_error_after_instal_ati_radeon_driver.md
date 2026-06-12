---
title: "resolution error after instal ati radeon driver"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by chuuninkid on 2010-04-23
hello guys this is my first post :) so please dont be too harsh on me :D

due to tight budget :P i've been using ubuntu 8.04 for 1 month (that means im a total noob in linux) and i recently realize that my ati radeon (hd5750) cards is not being used by ubuntu and makes me stuck in 800x600 res and disabled visual effects. i must install the driver manually.

so i goooooogled all the way and finally managed to install the ati fglrx driver with that sh thingy :D

problems begins then.

when i enable the driver in hardware driver menu and then restart it, the monitor goes "out of range" right when it supposed to display the login screen, so i suspect only the login screen that went wrong. then i tried enable auto login (after going thru the recov mode) but still out of range :( 

a friend of mine tells me to upgrade to 9.10 or wait until 10.4 released.
another friend of mine (which already tried the 9.10) told me that i should avoid the 9.10 and that my monitor is not supported and told me to bought an lcd (which is out of question :P)

my computer spec:
-amd athlon2 x2 250 3ghz
-mobo biostar 790gx
-ram 2gb dual channel
-ati radeon hd5750
-17" panasonic CRT monitor with 1280x1024 max resolution

at the time post this i actually already bought a windows7, but ubuntu leaves mark in my heart :D for that freeware photoshop-like software (gimp), as PS cs4 cost as much as 400 bux

any help will be so much appreciated

---

### Post by arrrghhh on 2010-04-23
I know it's not final yet, but 10.04 actually does handle video cards extremely well.

I always had to fiddle with my nvidia cards in Ubuntu (even tho support from nvidia is pretty good in respect to Linux) but with 10.04, they "just worked"!

So give 10.04 livecd a shot, I think the RC was just released.  Otherwise I think final is just a few days away!!

---

### Post by chuuninkid on 2010-04-23
yes, i'll install the 10.4 final... alot of ppl told me that the RC is already good enough and very stable

but for the meantime is there anyway to change the screen resolution before login to ubuntu? or from command line? i'm so desperate to use GIMP again :D

---

### Post by arrrghhh on 2010-04-23
> **chuuninkid said:**
> yes, i'll install the 10.4 final... alot of ppl told me that the RC is already good enough and very stable

but for the meantime is there anyway to change the screen resolution before login to ubuntu? or from command line? i'm so desperate to use GIMP again :D

There is, but it's painful since xorg.conf really doesn't have much to do with the config again... Which is why I suggested the 10.04 route.  Not the quickest solution, but I think in the long run you'll be happiest :D  So in the end, it is the best solution!

And yes I've been running it since beta1 and other than moving the stupid buttons over to the left I've been very very happy with it!!

---

### Post by quadproc on 2010-04-23
> **chuuninkid said:**
> hello guys this is my first post :) so please dont be too harsh on me :D

due to tight budget :P i've been using ubuntu 8.04 for 1 month (that means im a total noob in linux) and i recently realize that my ati radeon (hd5750) cards is not being used by ubuntu and makes me stuck in 800x600 res and disabled visual effects. i must install the driver manually.

so i goooooogled all the way and finally managed to install the ati fglrx driver with that sh thingy :D

Some more information would be helpful:
By "sh thingy" do you mean the downloaded file from ATI which has a name of <file_version_identifier>.run?
Which ATI driver version did you get?
Did you thereafter modify your xorg.conf file to specify the fglrx driver?
What does your xorg.conf file contain now? (A good way to show this is to enter "cat /etc/X11/xorg.conf", copy this, paste it into your reply message, and put CODE tags around it.
> 
problems begins then.

when i enable the driver in hardware driver menu and then restart it, the monitor goes "out of range" right when it supposed to display the login screen, so i suspect only the login screen that went wrong. then i tried enable auto login (after going thru the recov mode) but still out of range :( 
I have learned that the "Hardware Drivers" utility (which is actually named jockey-gtk) does not necessarily tell you what is happening in your system.  I do not trust it.  Fortunately, you do not need to use it.> 

a friend of mine tells me to upgrade to 9.10 or wait until 10.4 released.
another friend of mine (which already tried the 9.10) told me that i should avoid the 9.10 and that my monitor is not supported and told me to bought an lcd (which is out of question :P)
I started using Ubuntu at version 8.10 and found a couple of problems related to my HD4870 cards.  One problem was that the display resolution and colors were corrupted if I logged out and logged back in as another user.  Another was that having more than one graphics subsystem in the computer would prevent X windows from running; the workaround for this was to include a BusID in xorg.conf for the primary video card.

Since then I have used 9.04 and 9.10.  The transition to 9.04 was difficult and required a lot of work to get things running again, partly in the graphics area and partly elsewhere.  The transition to 9.10 had a problem that was my own fault: I did not uninstall the fglrx driver before I upgraded.  This caused corruption of the driver and the system came up in "low graphics mode". Removing and reinstalling the same driver corrected this problem; this was not a big problem.

Personally, I would suggest that you try 9.10 because it has been out for enough time to shake out the major bugs.  Version 10.04 will be out in a few days but it will probably have a bunch of problems at first.  Waiting a couple of months for the worst of those bugs to get fixed would probably save you some work.

All of the above assumes that you can get new versions of Ubuntu at low or no cost.  If you incur significant expenses in getting a release then your strategy should allow for that.

Please let us know the additional information requested and we will see what we can do.

quadproc

---

### Post by chuuninkid on 2010-04-23
> **quadproc said:**
> Some more information would be helpful:
By "sh thingy" do you mean the downloaded file from ATI which has a name of <file_version_identifier>.run?
Which ATI driver version did you get?
Did you thereafter modify your xorg.conf file to specify the fglrx driver?
What does your xorg.conf file contain now? (A good way to show this is to enter "cat /etc/X11/xorg.conf", copy this, paste it into your reply message, and put CODE tags around it.
yes it is "sh" and then the driver name
it is the latest from amd.com which is catalyst 10.3
i don't see any trouble during installation which going smoothly (like installing it on windows) or is there somethin i skipped? because the things that i do is keep pressing the "next" during installation (after read the instruction ofkorz :D)
about the xorg.conf, i'll do it tomorrow becoz im in home now.
> **quadproc said:**
> Personally, I would suggest that you try 9.10 because it has been out for enough time to shake out the major bugs.  Version 10.04 will be out in a few days but it will probably have a bunch of problems at first.  Waiting a couple of months for the worst of those bugs to get fixed would probably save you some work.
the guy who told me that i should avoid the 9.10 explain that in every *.10 release is an experimental release for the devs to do new things. he also shows me in 9.10 visual effect is disabled every time he logout/restart. since i have the same video cards as him, that'll enough to convince me :D.

but ok i'll give it a try


thx

---

### Post by arrrghhh on 2010-04-23
> **chuuninkid said:**
> the guy who told me that i should avoid the 9.10 explain that in every *.10 release is an experimental release for the devs to do new things. he also shows me in 9.10 visual effect is disabled every time he logout/restart. since i have the same video cards as him, that'll enough to convince me :D.

but ok i'll give it a try

thx

I don't think that's true, they release a new OS every 6 months.  One in April (.04) and one in October (.10) - Now there's LTS (Long-term Support) releases, which as *supposed* to be more stable, better for servers, etc... but that's not always the case.  Ubuntu tries to tell you it is, and they may try... but it doesn't always work out like that ;)

---

### Post by quadproc on 2010-04-23
> **chuuninkid said:**
> yes it is "sh" and then the driver name
it is the latest from amd.com which is catalyst 10.3
OK, that sounds good.> 
i don't see any trouble during installation which going smoothly (like installing it on windows) or is there somethin i skipped? because the things that i do is keep pressing the "next" during installation (after read the instruction ofkorz :D)There may have been something omitted: somehow, you need to tell the system to put the new driver's name into the xorg.conf file.  The ATI installation script may have done this for you, or you may have used initialize or reconfigure; in any event, the xorg.conf listing will tell us what you have now.> 
about the xorg.conf, i'll do it tomorrow becoz im in home now.OK, I will look back then.> 
the guy who told me that i should avoid the 9.10 explain that in every *.10 release is an experimental release for the devs to do new things.No, the developmental versions are designated as alpha and beta and as RC (release candidate).  From time to time the Ubuntu folks will produce a Long Term Support (LTS) version which will be supported for three years; so far as I know, these happen with the x.04 releases and not the x.10 releases.  The last one of these was 8.04.  But the regular releases occur about every 6 months and are intended for general usage.  There are also a lot of updates which are released in between the regular releases; these usually contain security fixes, bug fixes, and so forth.
>  he also shows me in 9.10 visual effect is disabled every time he logout/restart. since i have the same video cards as him, that'll enough to convince me :D.I am running 9.10 right now and I do not see that problem.  System hardware and software configurations vary sp it is easily possible that he has touched some kind of a bug in 9.10.  It might be worth reporting the bug to the Ubuntu folks.

quadproc

---

### Post by chuuninkid on 2010-04-25
sorry for the late reply, but here is my xorg.conf file contents:
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by chuuninkid on 2010-05-01
bump :D

guys i already install the lynx (fresh install x64). and the same problem is still bugging me.... its seems ubuntu makes a wrong guess about my monitor max resolution... the lynx still went out of range as soon as i restart the computer after installing the video driver...

then i come up with weird but working idea :D. i went to recovery mode then i put a shortcut of monitor control panel to the desktop, memorizing the keyboard button sequence to change resolution ( LOL ) and finally managed to get a desktop with enabled visual effects......  *phew*

last problem still remains.... the LOGIN SCREEN is still goes out of range :( my office is a busy place and i have to be able to log out sometime...

and here is my lucid lynx xorg.conf file content if needed
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
```any help will be so much appreciated

---

### Post by chuuninkid on 2010-05-01
problem solved... my geeky friend shows his magic by inserting this god-knows-what line in my xorg.conf file

```
SubSection "Display"
        Depth     1
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1280x960" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

EndSection
```

---

