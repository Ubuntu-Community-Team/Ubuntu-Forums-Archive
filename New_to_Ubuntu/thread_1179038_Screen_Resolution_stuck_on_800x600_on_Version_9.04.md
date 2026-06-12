---
title: "Screen Resolution stuck on 800x600 on Version 9.04"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by maxstephens on 2009-06-05
Hi,

Background:

I only installed Ubuntu 9.04 3 days ago, my first experience into the world of Linix. I have been using Windows since the days of 3.1 currently using XP.

My problem is my Display(DigiMate Model L-1731 LCD Monitor)is not adjustable beyond 800x600, I am trying to set it up to 1024x768. The Display Preferences say that the monitor is "unknown".

I have carried out a number of Google Searches on this issue and they indicate that "Ubuntu is not registering my monitor" and the display defaults to 800x600. 

Please can someone help me with a solution to this problem.

Max

---

### Post by pmlxuser on 2009-06-05
possibly because your display driver is not open source; go to >system >Administration > Hardware drivers 

you will see the display driver is  disabled. enable-install the driver you should be able to change resolution.

viola!

---

### Post by CatKiller on 2009-06-05
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://www.digimate.co.uk/en/productDetail.asp?prod=106") the values you're looking for are

```
        HorizSync       30-80
        VertRefresh     56-75

```

---

### Post by skompier on 2009-06-05
What video card do you have?

---

### Post by Utsukushii Tsubasa on 2009-06-05
haha and my driver wasnt installed either. probably y i cant use the effects:D

---

### Post by SOULRiDER on 2009-06-05
Is it fixed yet? You could also try to reconfig X
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by maxstephens on 2009-06-06
Hi Catkiller,

When I went into xorg.conf the HorzSync and VertRefresh details were not listed. I inserted this code but I forgot to but in "EndSection" at the end.

Saved and rebooted PC and the screen showed Ubuntu Loading up...then I got a lot messages scrolling up the screen...then the screen went blank before loading the desktop.

Help!

Max

---

### Post by CatKiller on 2009-06-06
> **maxstephens said:**
> When I went into xorg.conf the HorzSync and VertRefresh details were not listed. I inserted this code but I forgot to but in "EndSection" at the end.

Saved and rebooted PC and the screen showed Ubuntu Loading up...then I got a lot messages scrolling up the screen...then the screen went blank before loading the desktop.

If you press Ctrl-Atl-F1 you should get a text console that you can log into. You can use ```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
to restore the backup that you made.

```
sudo shutdown -r now
``` will restart the computer, or you can use ```
sudo /etc/init.d/gdm restart
``` to just restart X.

---

### Post by Legace on 2009-06-06
Or you could go to shell, and type in:
```
sudo nano /etc/X11/xorg.conf
```

to edit the xorg.conf file.

---

### Post by maxstephens on 2009-06-06
Hi,

I tried Ctrl-Alt-F1, no text consul just the same blank screen.

I know that the monitor is ok, because I have a PC with Dual Boot setup and I can access XP ok and get a normal screen.

The Graphics etc is intergrated on to the MSI Mainboard(Nivida nForce)Model of Mainboard is K7N420 Pro.

---

### Post by skompier on 2009-06-06
> **maxstephens said:**
> 
The Graphics etc is intergrated on to the MSI Mainboard(Nivida nForce)Model of Mainboard is K7N420 Pro.


Ok, your M/B uses an Nvidia GForce MX graphics chip. I've read every post in this thread and see nothing that says that you're using the Nvidia driver.

In System>Preferences> do you see Nvidia X Server Settings? Since you've been editing your Xorg.conf, what's listed under the "Driver" section?

In addition...do you have a TV tuner card plugged into your computer?

---

### Post by CatKiller on 2009-06-06
> **maxstephens said:**
> I tried Ctrl-Alt-F1, no text consul just the same blank screen.

Sometimes you need to press it twice.

Otherwise, you can boot into Recovery mode, which won't even try to start the graphics. You'll be running as root, so you won't need the sudo at the beginning of the commands.

---

### Post by mal1958 on 2009-06-06
> **maxstephens said:**
> Hi,

I tried Ctrl-Alt-F1, no text consul just the same blank screen.

I know that the monitor is ok, because I have a PC with Dual Boot setup and I can access XP ok and get a normal screen.

The Graphics etc is intergrated on to the MSI Mainboard(Nivida nForce)Model of Mainboard is K7N420 Pro.

Hi max.  From what I have read you **_may_** (just **_may_**) have to do a full reinstall of Ubuntu.  If that is the case when you are up and running with your new Ubuntu screen at 800 x 600 then you have the following things to do.


[LIST=1]
[*]at the top of your screen you will see Applications     Places     System     followed by a firefox logo a little transparent envleope and a questionmark.
[*]Click on the one marked System  then move down to Administration, then Hardware Drivers.
[*]your OS will check for the drivers that can work with your vid card (these drivers are not Open source, so they cannot be installed with the main OS)
[*]A screen will pop up showing you a possible selection of drivers it can install and activate (one should be marked 'Recommended'.  Select that one and then click the activate button.
[*]You will probably have to enter your password at that point, do so.  The system will automagickally download the drivers, installl them and prompt you for a reboot.  Do so.
[/LIST]

Congratulations, you have installed the new video drivers.  You may still be stuck at 800 x 600, or with the new drivers installed you may be at a much higher res.  Now you need to config your default screen res.

To config Nvidia drivers you need to:


[LIST=1]
[*]From the desktop, or anywhere in the Ubuntu OS, press (alt) and (F2) at the same time.
[*]This will bring up a run program box.
[*]Type into the input area   "**gksudo nvidia-settings**"  with out the quotes of course.  This will bring up the Nvidia control panel where you can make your selections.  For 1024 x 768  (which are my res setting BTW) I would recommend that you use a refresh rate of 60.  this is a setting that most monitors can handle with out over heating or burning out.
[*]Once you have your screen res and refresh rate set properly (IE to your satisfaction) then click on the apply, and then save it to the xorg config file.
[*]then you can quit the program and you have just configured your screen to work with your video card.
[/LIST]
This is the method I had to use because, like you, I have an Nvidia graphics card.  Unlike you, my card is a card in an AGP slot, not a chipset on the ole MB.  I got walked through this  proceedure by a fellow Ubuntu user named nandemonai.  So if this works for you and you can help another solve the same problem, simply add your name to the list.

Mike

---

### Post by maxstephens on 2009-06-07
Hi Mike,

First of all I had to reinstall the program again.

I have previously gone down the route of "Hardware Drivers" it finds a Nvidia Driver...I choose this one and reboot.You then get a screen of garbage!!! eg a picture of squares made up of coloured vertical/horz lines.

One can still hover the mouse over the top menus(actually readable) and carefully select hardware drivers and the remove...reboot and you are then back to a "normal Start Screen again that is readable at 800x600.

Tony

---

### Post by 4Orbs on 2009-06-07
It is a good thing that you were able to install the driver through the Hardware Drivers Mgr, and you say the screen was horrible but slightly functional. I think you should reactivate the driver, reboot, then go to the Appearance menu and turn off desktop effects. Then follow some of the other posts to repair the xorg.conf and adjust the resolution.

---

### Post by maxstephens on 2009-06-09
Hi,

I reactivated this driver....went through all of the suggestions previously posted eg Editing xorg.conf.
Still unable to resolve the resolution issue.

As well as seeking help through this forum, I have been in touch(by phone at the PC)with a friend who has more experience than me with Ubuntu eg earlier versions. He has come to the conclusion that the Nvidia Drivers Available through Ubuntu are not compatable with my Hardware. He has 9.04 running on his PC ok.

Is it possible to take a copy of my working Nivida Driver from my Microsoft XP and place this into Ubuntu?.

If so, can someone advise me how to do it.

---

### Post by CatKiller on 2009-06-09
The integrated graphics on your motherboard are rather old (GeForce 2 MX according to Wikipedia) and it is true that NVidia have been removing support for older cards from their closed drivers (which is one of the problems with closed drivers) but if NVidia hadn't claimed the driver was compatible with your graphics card you wouldn't have been offered it. When you select the closed driver, you should see a version number which you can use to see if your graphics chipset is supported by that driver.

You don't **need** to be using the closed nvidia driver to get the resolution that you want, the open-source ones (nv) are perfectly up to that task and should have been selected by default. The resolution problem, IMO, lies with the monitor rather than the graphics chipset. Once you've got that sorted out you might be in a better position to get a useable image from the closed drivers. 

As I said before, resolution problems are usually caused by the monitor not giving the EDID values that allow the resolution to be set automatically. Usually, setting the refresh rates manually is sufficient to allow the modes to be set. Sometimes it is also necessary to also add ```
        Option          "UseEDID"                       "False"
``` to the Device section as well as the HorizSync and VertRefresh lines in the Monitor section because the monitor is giving inaccurate EDID values rather than none at all.

The log file for X, which is at /var/log/Xorg.0.log, should tell you why the modes higher than 800×600 aren't being used. If you want even more information about the modes and why they aren't being used, adding 

```
       Option          "ModeDebug"                       "True"
``` to the Device section will give more output to X's log.

> **maxstephens said:**
> Is it possible to take a copy of my working Nivida Driver from my Microsoft XP and place this into Ubuntu?

No. Linux and Windows are almost entirely different.

---

### Post by maxstephens on 2009-06-15
I recently tried the various suggestions,with no improvement. I am considering fitting a seperarate "Graphics Card - AGP Type" to the PC, in the hope that Ubuntu's Open Source Drivers(nv) will see it ok and give me adjustable Resolution!!. A friend suggested using  an FX5200 with some editing of xorg.conf involved. Perhaps someone else may suggest a "Graphics Card" that the nv drivers will see and NOT envolve any editing.

By comparision, I was able to borrow a fairly new "tower Unit" with on board graphics running an Intel chipset and connect up together with my own monitor and try the Ubuntu Live CD(eg not installing it). When the Desktop appeared the screen resolution was 1280x1024 and adjustable!!.

Unfortunately I cannot yet afford a New PC, hence the Graphics Card solution? to the old one.

---

### Post by CatKiller on 2009-06-15
Out of interest, was this the same monitor that wasn't working before? Did the screen resolution tool correctly identify it rather than listing it as Unknown?

The FX5200 is no longer supported by the proprietary drivers. You can probably pick up a 6200 for cheap which is marginally better and is currently still supported. NVidia will probably drop support for that too at some point in the future, but that's the way of binary-only drivers. I didn't have to fiddle to get mine to work. I haven't tried the nv driver.

---

### Post by maxstephens on 2009-06-16
Yes, this was the same monitor that was not working before. The Screen Resolution Tool identified it as "**NUL 17"** " actual Make was DGM size 17".

---

### Post by CatKiller on 2009-06-16
> **maxstephens said:**
> Yes, this was the same monitor that was not working before. The Screen Resolution Tool identified it as "**NUL 17"** " actual Make was DGM size 17".

So the monitor's providing **some** EDID information. Just not complete information. And potentially the onboard graphics aren't even passing that on to X. Still, you might be able to get the resolution that you want if you tell X to ignore EDID entirely and to just use the timings that you've specified, as I suggested above.

---

### Post by maxstephens on 2009-06-19
I have carried out your previous suggestions, while I can Enter the Resolution info into xorg.conf. The line that tells xorg to ignore EDID, causes the PC to fail to load the Ubuntu Desktop and defaults to a command prompt

---

### Post by CatKiller on 2009-06-19
Any informative error messages?

---

### Post by maxstephens on 2009-06-20
Differcult to see any as text "flew up the screen" very quickly.

I had tried to look at the log file for X......but the system said "Permission Denied".

---

### Post by CatKiller on 2009-06-20
I don't think you need special permissions to read X's log file. ```
less /var/log/Xorg.0.log
``` should be sufficient, but if it isn't, stick a sudo on the front.

---

### Post by maxstephens on 2009-06-21
This time I managed to get into Log ok, I have given you a small part of the log:

(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)

I am not quite sure what I am looking for here, is this enough without attaching the complete log?

---

### Post by CatKiller on 2009-06-21
> **maxstephens said:**
> ```
(II) NV(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
```

I am not quite sure what I am looking for here

This tells you that it's neither receiving EDID values for the refresh ranges, nor using the ones that you've told it are appropriate for your monitor.

---

### Post by jeepfreak2002 on 2009-06-21
Let me give you a non-technical suggestion.  The OS should be able to communicate with your monitor and your video card giving them the EDID values.  I found that sometimes if you have a DVI adapter connected to an old VGA cable, the info will not communicate between your PC and monitor. 

I bought a $6.00 DVI cable and blammo - instantly everything was recognized correctly.  

Good luck - there are some hiccups w/ linux, but I have learned to love it.

Jeepfreak

---

### Post by osx on 2009-06-30
> **jeepfreak2002 said:**
> Let me give you a non-technical suggestion.  The OS should be able to communicate with your monitor and your video card giving them the EDID values.  I found that sometimes if you have a DVI adapter connected to an old VGA cable, the info will not communicate between your PC and monitor. 

I bought a $6.00 DVI cable and blammo - instantly everything was recognized correctly.  

Good luck - there are some hiccups w/ linux, but I have learned to love it.

Jeepfreak

I was having the same problem, but for me the VGA cable was the fix. My monitor has a DVI and VGA port, but my nvidia graphic card only has DVI ports. So, I removed the DVI cable, attached the VGA cable to the VGA port on the monitor, attached the VGA-to-DVI adapter that came with my video card to the VGA cable, attached that to my video card and have had the full 1680x1050 resolution ever since without having to tweak my xorg.conf file. I'm using a Viewsonic VX2025wm monitor (for some reason, the Viewsonics seem to be the most problematic in regards to EDID data).

---

### Post by maxstephens on 2009-07-08
I have tried replacing my VGA cable between the monitor and the onboard graphics output, but with no success. Due to the age of my MSI Mainboard eg equivalent to nForce 1 series and the fact I have been unable to find any drivers that will work, also I thought that I could fit a seperate Graphics Card. But that was ruled out as it had to work with only 1.5V Signals.

So relunctantly I have now abandoned further attempts to get this version of Ubuntu to work with this PC, unless the developers can maybe provide alternative drivers through there future updates.

A question here for any Ubuntu Developers following the Forum postings is how new must a PC be, to be supported, obviously mine at 7 years old is too old?. It still runs MS WinXP SP3 OK. and other Apps.

Many thanks to all the Forum Users out there, who have tried to help me to resolve this protracted issue.

---

### Post by CatKiller on 2009-07-08
> **maxstephens said:**
> obviously mine at 7 years old is too old?.

Mine's nearly ten years old. Although I've changed the bristles and the handle many times, if you know what I mean.

---

