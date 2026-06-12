---
title: "low screen resolution"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by falconfox on 2009-08-01
Hello,

I just installed ubuntu 9.04 and the screen resolution is LOW. I searched google and forums for a solution and most of them involved command line solutions. None of these "solutions" worked. I also tried the nvidia GUI, but that didn't help either. Is there a GUI program that can fix my resolution?

Thanks,
Patrick

---

### Post by CatKiller on 2009-08-01
> **falconfox said:**
> Is there a GUI program that can fix my resolution?

That depends on why it's broken.

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

---

### Post by JavaBeanHead on 2009-08-04
Hi . . . I'm having somewhat of the same issue (new install, noob here). The highest resolution that will display is 1024x768.  I am running 8.10 and the graphics card is an ASUS EN7300GT 256M (nVIDIA-based).  1024x768 isn't so bad, but I have a 22" monitor and I _know_ that card will do better than that.  Unfortunately, ASUS has posted no Linux drivers for the card.  
 
I took it upon myself to install envyng-gtk and ran 'envyng -t' at the console to install an nVIDIA driver, and that's how I got to 1024x768.  Is there a better way or better driver suited for this card? 
 
I thought the xorg.conf file was not being used (or at least deprecated) in the later versions of Ubuntu?

---

### Post by CatKiller on 2009-08-04
You haven't said what monitor you're using. That's generally the critical factor. See my post above.

> **JavaBeanHead said:**
> I thought the xorg.conf file was not being used (or at least deprecated) in the later versions of Ubuntu?

For some functions (setting mouse options is one of them, I believe) xorg.conf is ignored. For many other things xorg.conf is used if it includes an appropriate configuration, with the newer methods used otherwise.

---

### Post by wizard10000 on 2009-08-04
> **falconfox said:**
> Hello,

I just installed ubuntu 9.04 and the screen resolution is LOW. I searched google and forums for a solution and most of them involved command line solutions. None of these "solutions" worked. I also tried the nvidia GUI, but that didn't help either. Is there a GUI program that can fix my resolution?

Did you install Ubuntu's restricted drivers for your video card?  I'd do that before I messed with X at all.

Look in System --> Administration --> Hardware Drivers

Install the drivers and reboot.

Hope this helps -

---

### Post by JavaBeanHead on 2009-08-05
Hi CatKiller . . . 

I just edited my xorg.conf file and CTRL+ALT+Backspace to restart GDM.  I then went into System >> Preferences >> Screen Resolution and found that nothing had changed - still 1024x768 at max.  The monitor I am using is a [KDS K-22MDWB]("http://www.kdsusa.com/K22mdwb.asp").

Here's my current xorg.conf file:
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection

Section "Monitor"
        Identifier      "KDS K-22MDWB"
        VendorName      "KDS"
        HorizSync       30.0 - 82.0
        VertRefresh     56.0 - 76.0
EndSection

```

Any additional help you could provide is greatly appreciated.

---

### Post by JavaBeanHead on 2009-08-05
> **wizard10000 said:**
> Did you install Ubuntu's restricted drivers for your video card?  I'd do that before I messed with X at all.

Look in System --> Administration --> Hardware Drivers

Install the drivers and reboot.

Hope this helps -

Hi Wizard . . . You asked if I'd installed Ubuntu's restricted drivers.  No idea.  As mentioned, I installed something called envyng-gtk, which is a utility that allows you to install either an ATI driver, or nVIDIA driver.  I selected the latest nVIDIA driver from the options.  If you're puzzled at this tool, try it in Snytaptic .  .  . it's easy install/uninstall and non-invasive (i.e. you don't actually have to install the driver just to preview the tool).  I learned about it in a book from No Starch Press called, "Ubuntu For Non-Geeks, 3rd Edition".

System >> Administration >> Hardware Drivers tells me that "Proprietary drivers are being used to make this computer work properly"  "NVIDIA accelerated graphics driver (version 180) [Recommended]" is activated.

---

### Post by CatKiller on 2009-08-05
> **JavaBeanHead said:**
> Any additional help you could provide is greatly appreciated.

Sometimes a monitor will provide inaccurate EDID numbers rather than none at all (mine does this). In those cases, X will use the EDID numbers rather than the ones you've provided to safeguard the monitor. You can tell X not to do this by putting ```
        Option          "UseEDID"                       "False"
``` in the Device section.

X's log is at /var/log/Xorg.0.log. You could look in there to see why the modes you want aren't being used. If there's not enough information in there, you can use ```
        Option          "ModeDebug"                     "True"
``` in the Device section to tell it to be more verbose.

Some people have found it helpful to specify (non-VESA) modes to help them be picked up as options for X to consider. In your case, that would be something like

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection
```

That's all I can think of at the moment.

---

### Post by JavaBeanHead on 2009-08-05
I am not quite sure what happened here, but I fixed it.  

First of all . . . relative n00b here . . . I have to learn NOT to use System >> Preferences >> Screen Resolution when using an NVIDIA card . . . gotta change screen resolution via System >> Administration >> NVIDIA X Server Settings. 

But that wasn't the core of the problem because even the NVIDIA X Server Settings wasn't giving me the resolution I wanted. After creating about 5-6 different versions of my xorg.conf file . . . and even installing/uninstalling envyng-gtk . . . I resorted back to the xorg.conf.failsafe. 

```
cp xorg.conf.failsafe xorg.conf
```Reboot.

It finally came out of low graphics mode. *whew*

Anyway after reading a bajillion threads on the subject, I was convinced that it had to do with the HorizSync and VertRefresh issue (as mentioned previously) but had not gotten it to work. So after going back to the drawingboard with the failsafe xorg.conf, I simply added the HorizSync and VertRefresh values specific to my model of monitor an NOTHING ELSE. 

No 
```
Option          "UseEDID"                       "False"
```in the Device section.

And no
```

Section "Screen"
              Identifier      "Default Screen"
              DefaultDepth    24
              SubSection "Display"
                           Depth           24
                           Modes           "1680x1050"
              EndSubSection
EndSection
```either.

Lesson learned: Start with the xorg.conf.failsafe file to be at ground zero, work your way up. No EnvyNG (just not specific enough, and it was enough to throw me off completely because I used that as a springboard to start editing a **dirtied** xorg.conf file.

Threads that helped me out most:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%207.10]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%207.10")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Sir I am grateful for your attempt, and I'm sorry if I've wasted your time. I can only redocument what I have not found yet, and hope that it makes things better. 

Now, off to fix a printer that won't connect.

---

### Post by CatKiller on 2009-08-06
No worries. Glad you've got it working.

---

### Post by JavaBeanHead on 2009-08-06
Ohhh man  . . . I want so badly to be like you guys . . . I work in IT, and I feel pretty adept at normal geekery . . . but Linux is a relatively new world.  

Help a brother out (and I know you will).  Whenever I reboot, it goes back to a default resolution.

Why?

---

### Post by JavaBeanHead on 2009-08-09
Answer is: 

```
sudo nvidia-settings
``` from command line.  

Make your setting changes, and choose Save to X Configuration File.

---

