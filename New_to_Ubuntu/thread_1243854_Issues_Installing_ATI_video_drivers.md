---
title: "Issues Installing ATI video drivers"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Cashman3000 on 2009-08-18
I am new to Ubuntu and the Ubuntu forums and just recently started using Ubuntu 9.04. I am having a few issues configuring my video drivers. I noticed that many of the games that I downloaded from the repositories would freeze up after a few minutes of playing time. I realized that I needed to configure my video drivers. After reviewing the forum I followed the steps at:

 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#General%20Troubleshooting](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#General%20Troubleshooting)

**I followed the steps and upon entering:**
 sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

**I recieved**: "insmod: can't read '/lib/modules/2.6.28-14-generic/volatile/fglrx.ko': No such file or directory"
 I was wondering if anyone had any ideas on how to resolve my video driver issues.
 This is my video card: 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]


Any help would be greatly appreciated.....

---

### Post by alexandari on 2009-08-18
install Envy. You can find it in the packages in Add/Remove programs. It downloads and installs the latest drivers for nvidia or ati

---

### Post by Mark Phelps on 2009-08-18
> **Cashman3000 said:**
>  This is my video card: 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]


Any help would be greatly appreciated.....
Your card is not supported with fglrx drivers under Ubuntu 9.04.  You will need to uninstall those drivers and replace them with the open source drivers.

---

### Post by Cashman3000 on 2009-08-18
"Your card is not supported with fglrx drivers under Ubuntu 9.04.  You will need to uninstall those drivers and replace them with the open source drivers."


Whats the best way to uninstall those fglrx drivers? I will poke around the forum too to try and find out. Thanks for the help.

---

### Post by Vakman on 2009-08-18
> **Cashman3000 said:**
> "Your card is not supported with fglrx drivers under Ubuntu 9.04.  You will need to uninstall those drivers and replace them with the open source drivers."


Whats the best way to uninstall those fglrx drivers? I will poke around the forum too to try and find out. Thanks for the help.
```
sudo apt-get remove --purge xorg-driver-fglrx
```
That should work out to remove the drivers. Also [this]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") might help you. Choose to install either Standard Open Source Drivers or the open source Edge drivers. I think the Edge drivers should work for your card. I will double check shortly. Anyway hope that helps. The first choice "Open Source Drivers" are probably your best bet. The link will also show you how to install them.

---

### Post by utnubuuser on 2009-08-18
to install ati driver:> sudo apt-get install xserver-xorg-video-ati

---

### Post by Cashman3000 on 2009-08-18
Okay thank you for all the help!

I am going to try and remove the  fglrx drivers first by:

sudo apt-get remove --purge xorg-driver-fglrx
then installing new ATI  driver by:

sudo apt-get install xserver-xorg-video-ati

Hopefully this works. Will removing the fglrx drivers give me any problems after uninstalled?

---

### Post by super kim on 2009-08-18
hi Cashman3000,

what sort of ati card do you have?
```
lspci | grep VGA
```
you may have to set up your xorg.conf to be able to 'optimize' your card if you want to play games to do that you need to know about your card.

---

### Post by goldblattster on 2009-08-18
If you are without a GUI, you can access the CLI by pressing Ctrl+Alt+1.

---

### Post by Cashman3000 on 2009-08-18
Okay I checked my System/Administration/Hardware Drivers and it was completely blank. I decided to just go ahead and run:
sudo apt-get install xserver-xorg-video-ati

It looks like it installed fine from the terminal. But still there is nothing in System/Administration/Hardware Driver.

I never did the initial removal of the fglrx drivers.

Any thoughts on whats the next step to see if everything is installe dcorrectly?

---

### Post by Cashman3000 on 2009-08-18
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

---

### Post by super kim on 2009-08-18
> **Cashman3000 said:**
> Okay I checked my System/Administration/Hardware Drivers and it was completely blank. 


only third party drivers will show up here.
you need to search your synaptics package manager for video-ati make sure its installed.

---

### Post by super kim on 2009-08-18
> **Cashman3000 said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
then you should go here:
[https://help.ubuntu.com/community/RadeonDriver#About%20the%20different%20drivers]("https://help.ubuntu.com/community/RadeonDriver#About%20the%20different%20drivers")

also would be useful to know your architecture. if your using 64bit then [**this**]("http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=2.4.2.3.1&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20") may or may not (i don't have 64bit) be useful. i wouldn't use the propriety drivers though 64 bit or not.

---

### Post by Cashman3000 on 2009-08-19
Thanks. I can't figure it out. I may just bag the whole idea. Ubuntu is working great anyway in its current state. Thought it would be fun to play some old games. Have a good one.

---

### Post by super kim on 2009-08-19
since you have the right driver now you just need to:
a- backup your xorg.conf
b- edit your xorg.conf

the easiest way (for me) is to open a terminal, type "gksudo gedit /etc/X11/xorg.conf" then enter your password. 
a text editor will open first thing to do is click on the "save as" and call it xorg.cof.backup or whatever you like. 
then copy/paste the code below into the editor then "save as" xorg.conf 
then you can press Ctrl-Alt-Backspace. if it all cocks up dont worry just restart with a cd or in low graphics mode if you dont have one, then restore the xorg.conf from your backed up file.

here is what your new xorg.conf should look like
```

# xorg.conf (X.Org X Window System server configuration file)

# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        Option          "AccelMethod"    "XAA"
        Option          "EnablePageFlip" "true"
        Option          "TripleBuffer"   "true"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
EndSection

```if it all cocks up don't worry just restart with a cd or in low graphics mode if you don't have one, then restore the xorg.conf from your backed up file.

---

### Post by Cashman3000 on 2009-08-19
Thanks super kim! I followed your instructions and everything is still working normally. When I hit Ctrl-Alt-Backspace nothing happened though. Does that reboot the computer? I just did a manual shut down, restart.

I just tried playing a game like supertuxkart and it seemed to be working well. It never froze on me like past experiences. How can I tell if the drivers are installed and the video card is working correctly?

---

### Post by 3rdalbum on 2009-08-19
> **Cashman3000 said:**
> I just tried playing a game like supertuxkart and it seemed to be working well. It never froze on me like past experiences. How can I tell if the drivers are installed and the video card is working correctly?

If you can play a 3D game like SuperTuxKart and it works well, without freezing, then your drivers are installed and the video card is working properly :-)

The drivers that Ubuntu comes with are always available, so they don't need to appear in Hardware Drivers. Ubuntu knew that your card is not supported in the official ATI driver, so that's why it didn't offer it to you as a download. Just thought I'd explain that to you.

EDIT: Oh, the Control-Alt-Backspace thing has been disabled. It used to "zap" (force a restart) of the X server, which kills your graphical programs and takes you back to the login screen. It can be re-enabled by the use of the "dontzap" program that's in the repositories. Or you can use the new key combination, which I don't think anyone can remember :-)

---

### Post by super kim on 2009-08-19
oh i didn't know the zap had been disabled, thats because i never do it myself. not the best way and just lazy.

CashMan3000, if your cards working then you can try to squeeze a bit more out of it by changing:
```

          Option             "AccelMethod" "XXA"

```
to
```

          Option             "AccelMethod" "EXA"

```
there might be other things you can enable with the xorg.conf but if EXA works for you then great :)

---

