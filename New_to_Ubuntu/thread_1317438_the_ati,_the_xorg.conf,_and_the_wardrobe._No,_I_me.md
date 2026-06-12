---
title: "the ati, the xorg.conf, and the wardrobe. No, I meant LCDTV!"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by josephobrien2000 on 2009-11-06
Hi

Well I've been using ubuntu 9.04 for 4 weeks and 9.10 since release. 9.04 worked straight away on my Gericom EGO laptop, running ati Radeon 9700 display. Wireless worked, USB worked, screen worked, and DVD worked. Used the getting started guide to install DVD facility and a whole bunch of other stuff!

I started playing with the display settings which is bad thing with an ati radeon 9600. I first installed the fglx ati driver from the ubuntu addremove program and lost my display! A quick search on google (on my works PC) yielded info on the fact the latest ati driver is not compatiable with ubuntu 9.04, other it is with previous versions. I tried this [http://omgili.com/jmp/jHIAmI4hxg_KeEHHeqhJ_Vw3l0dFe1Wz7vd1qI6bsgBWEf_..T88MK181a2nsyPTFBknEm2Psc0uSPPUaLUZZoiTIUxkMgC2hkZs_dFPujWj2qfU8MaiOVU.2bGZOK4fbrEXvGfx0dIMP9847IyuPuJ4U3pKTsDwLiJwyLNvdO8YOdegCPFmRIRQ4mif7rckmUTrrRvLkXE7kJd2sTYt8g--](http://omgili.com/jmp/jHIAmI4hxg_KeEHHeqhJ_Vw3l0dFe1Wz7vd1qI6bsgBWEf_..T88MK181a2nsyPTFBknEm2Psc0uSPPUaLUZZoiTIUxkMgC2hkZs_dFPujWj2qfU8MaiOVU.2bGZOK4fbrEXvGfx0dIMP9847IyuPuJ4U3pKTsDwLiJwyLNvdO8YOdegCPFmRIRQ4mif7rckmUTrrRvLkXE7kJd2sTYt8g--)
and completely totalled my laptop and had to reinstall which was actually painless!

So, Im very skeptical about ati and their support for Ubuntu and I steer clear of mucking with my display

One afternoon I wanted to play a video on my LCDTV so connected it to the laptop using VGA lead. The tv was detected and I asked to mirror the image (my preferred option for dual screen). Ubuntu then asked to install a virtual display driver to get it working which I said yes to. This mucked up the laptop display a bit (funny looking band on right hand side, 1" thick) but the lcdtv was happy so I played my video. The video did play ok on the laptop screen but not on the lcdtv - the window was there but no video just grey. I played a bit with other video players and stumbled across a solution - open the video twice on two seperate players, pause the 1st window and the 2nd window will play fine (works for VLC player and Totem). 
Anyway, this virtual display driver would notshake off! When I rebooted the horrible artefact disappeared but I lacked few resolution options whereas before I had loads!. Did a bit of research :
[http://ubuntuforums.org/showthread.php?t=1114168](http://ubuntuforums.org/showthread.php?t=1114168)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and realized that it all come down to one file: xorg.conf

So I opened up mine and it said this:
 
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2640 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection


And this did not seem right. No mention of ati driver so I lost quite a lot of 3D support .

I spent ages trying to find a xorg.conf that would work for me but most I saw online had lots more info to hardware that was not installed. So using the guide above (the latter) icame up with this one:

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
EndSection



..........and surprisingly it worked (although I have to admit, the above is edited - some stuff was removed as I lost my display!)

So if you are unlucky enough to have an ati 9600 (mv350) display that has been dropped by ati/amd (even though their website leads you to think it is!) and you've innocently plugged it into your lcdtv and it has mucked up your display, try the above xorg.conf.

You can edit it using gedit using the command sudo gedit /etc/X11/xorg.conf

---

### Post by josephobrien2000 on 2009-11-17
Hi

I installed KDE but discarded it immediately as the sound did not work. Simple fix for that see my other post on subject. 

KDE supports multiple monitors far better than GNOME with my ati 9600. No artifacts. All works well, although I still have to open a video twice before it is seen on LVDTV.

Im sticking with KDE

Joe

---

