---
title: "Success with Acer 3680, Wireless, Sound, and Beryl"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by blakesle on 2007-07-07
I have to thank the many many individuals who contribute to these Forums. Through your knowledge and willingness to share what you know I have been able to bring up my Acer Aspire 3680 in every respect. This is a laptop I purchased for $399.00 and I can't tell you how great it is. Ubuntu Feisty Studio runs quickly and has a real snap to it. (too snappy in some cases) I am going to outline what I did to get this running in the hope that I can provide hope and direction for novice users. My experience with Unix/Linux is minimal but not nil. I understand the structure of the system and how to use some of the basic tools. I have not approached Linux for at least 10 years but it has been very easy to re-acquaint myself with it and get this system going.

The first thing I did was to load a clean copy of Ubuntu Feisty Studio (I actually did this many times when I made errors and had to back track.) 

1. To get Gnome working I had to install the system using ONLY 1024 x 768. If I added any other video  video resolution would result in the system coming up in terminal mode. This was solved by experimenting and by searching for information from others bringing up the 3680 as well.

2. Next I got the sound going by clicking on the sound icon in the upper left part of the screen and enabling Surround Sound. Once I took it off mute I had sound. 

3. To get wireless networking going I had to purchase a PCMCIA card, the Linksys Model WPC54G. This is a Broadcom card. I did this because after many searches of this forum and unsuccessful attempts to get the built in Intel Athos Wireless Card working, I discovered that in my particular model Acer used a newer version of the card, the AR5007G and that is not yet suported. At some point I expect that this card too would be supported and the need to purchase an alternative card will not be necessary, but now it is. This card came up very quickly using the following guide:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=Linksys+WPC54G](http://ubuntuforums.org/showthread.php?t=405990&highlight=Linksys+WPC54G)

4. I installed Beryl and Emerald using the following guide:

[http://ubuntuforums.org/showthread.php?t=491451&highlight=install+beryl](http://ubuntuforums.org/showthread.php?t=491451&highlight=install+beryl)

5. I made the following changes in the xorg.conf file. When you do this copy the orriginal using the code [B]sudo cp xorg.conf xorg.conf.old
[/B]
This is the section for the video device:

Section "Device"
        [B]Option          "XAANoOfscreenPixmaps"  "true"
        Option          "AddARGBGLXVisuals" "True"
        Option          "RenderAccel"   "true"
        Option          "DRI"   "true"
        Option          "NoAccel"       "false"
        Option          "DDC"   "false"
        Identifier      "Intel Video Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        65536[/B]
EndSection

If you change the name of the video "Identifier" make sure you carry that change through to the  Screen section as done below. 


Section "Screen"
        Identifier      "Default Screen"
        **Device          "Intel Video Card"**
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Finally, this section was added on the suggestion of one of the users I read in this forum. 

[B]Section "Extensions"
        Option "Composite"      "enable"
EndSection[/B]



6. I also learned that there is a missing file in Fiesty which prevents Emerald from running. It is **beryl-xgl **and you can download it as a zip file from here:

[http://ubuntuforums.org/showthread.php?t=437800&highlight=beryl-xgl.zip](http://ubuntuforums.org/showthread.php?t=437800&highlight=beryl-xgl.zip)

Once completed Beryl and Emerald worked incredibly well. It puts MS Vista Aireo to shame!!!

This has been a journey I could not have completed without the assistance of quite a number of you. Keep it up! It is truly appreciated. I hope this minor outline of how I completed the setup on the Acer Aspire 3680 helps others and gives hope to many more.

---

### Post by darrenrxm on 2007-07-08
The current version of mint linux (Cassandra) installs at the correct resolution with no problems.

---

### Post by Sparkfist on 2007-08-03
I take it that if you used a PCMCIA Wi-fi card there are no drivers for the built-in Wi-fi card. On that note has you or anyone you know of been able to use a U.S. Robotics Wi-fi card? It's the only one I have lying around.

Thanks for any help.

---

### Post by randytuggle on 2007-10-02
I got my 3680's wireless to run by installing ndiswrapper-common from the install CD (after adding the CD to synaptics) and installing atheros-ar5007eg-installer-0.1b.tar.gz (extract and install). I found this info from the forums somewhere. It works like a charm!

---

