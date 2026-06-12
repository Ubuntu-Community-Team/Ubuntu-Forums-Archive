---
title: "Can I improve my screen resolution?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by flight ltnt on 2009-05-22
Hi,

I'm knew to Linux and have just installed Ubuntu 9.04 via WUBI on my IBM T60 which is using an ATI Technologies Inc M52 [Mobility Radeon X1300].  Is it possible to improve my screen resolution from 1024x768 [4:3]?  Will this graphics chipset allow me to use Compiz so I can try out some desktop effects?

Thanks,
Flight Ltnt

---

### Post by Hospadar on 2009-05-22
It should, you can install the restricted (free but non-open-source) drivers from System->Administration->Hardware drivers.  Also it may be as simple as changing your resolution in System->Preferences (I think is where it is, if not, look around, it's in there somewhere).

If you have troubles with the restricted drivers (I would test everything you want to do and see if it works first, if so, no need to bother with restricted drivers, for some people they are buggy) you may want to try a native install (i.e. non-wubi) sometimes wubi causes mysterious problems.

To enable compiz,  System->Preferences->Appearance->Visual Effects and turn them up to anything but the lowest setting.

If you want more fine-grained control of the specific effects, you can install the "compizconfig-settings-manager" from System->Administration->Synaptic
And then open it in System->Preferences

Hopefully that should get you started
Cheers!

---

### Post by flight ltnt on 2009-05-27
Thanks for the tips.  I've tried enabling the restricted drivers but get the message "No propriety drivers are in use on this system."  Does this mean that there are none available or have I missed a step somewhere?

---

### Post by aeiah on 2009-05-27
> **flight ltnt said:**
> Thanks for the tips.  I've tried enabling the restricted drivers but get the message "No propriety drivers are in use on this system."  Does this mean that there are none available or have I missed a step somewhere?

no, it just means none are in use at the moment. there should be an option to download / install / enable the restricted drivers in that section. are you connected to the internet normally?

---

### Post by flight ltnt on 2009-05-27
Yes, I'm connected to the internet.  There's nothing listed in the window and therefore the enable button is greyed out.  There is no download/install option.

---

### Post by peakshysteria on 2009-05-27
> **flight ltnt said:**
> Hi,

I'm knew to Linux and have just installed Ubuntu 9.04 via WUBI on my IBM T60 which is using an ATI Technologies Inc M52 [Mobility Radeon X1300].  Is it possible to improve my screen resolution from 1024x768 [4:3]?  Will this graphics chipset allow me to use Compiz so I can try out some desktop effects?

Thanks,
Flight Ltnt

The new driver doesn't support any of the older ATI cards anymore. Which cards does ATI no longer support? The ATI Radeon 9500-9800,X300-X2100,Xpress. Complete list:
```
ATI Catalyst Linux 9.4 driver
Release date: April 17, 2009

The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

    * ATI Radeon 9500 Series
    * ATI Radeon 9550 Series
    * ATI Radeon 9600 Series
    * ATI Radeon 9700 Series
    * ATI Radeon 9800 Series
    * ATI Radeon X300 Series
    * ATI Radeon X550 Series
    * ATI Radeon X600 Series
    * ATI Radeon X700 Series
    * ATI Radeon X800 Series
    * ATI Radeon X850 Series
    * ATI Radeon X1050 Series
    * ATI Radeon X1300 Series
    * ATI Radeon X1550 Series
    * ATI Radeon X1600 Series
    * ATI Radeon X1650 Series
    * ATI Radeon X1800 Series
    * ATI Radeon X1900 Series
    * ATI Radeon Xpress Series
    * ATI Radeon X1200 Series
    * ATI Radeon X1250 Series
    * ATI Radeon X2100 Series 
```

My card worked out of the box. No need for extra drivers. Google earth working, Compiz working etc.

Have you tried to go to the Screens and Graphics menu to set your resolution there? (it's not clear from your first post which resolution youare capable of?

---

### Post by flight ltnt on 2009-05-27
So 1024x768 is as good as my screen resolution is going to get?

---

### Post by Chalfont on 2009-05-27
> **peakshysteria said:**
>  Have you tried to go to the Screens and Graphics menu to set your resolution there? (it's not clear from your first post which resolution youare capable of?

I have a similar problem to teh correspondent, have loaded 9.04 Ubuntu onto an old eMachines desktop with VIA graphics chipset, and it gives me two resolutions... 800x600 or 800x480.  Now this isn't good enough, XP gave me up to 1280x...  

Followed the Wikis and guides, did the >System > Adminstration > Display and similar to teh correspondent above it showed the dialogue box empty with the message no proprietary drivers installed.  No button or function at all to get a list (which apparently there should be).  Yes I am on the internet as i am typing this!   

So if I cannot get a decent display then it has to be goodbye Linux and back to being a Micro$oft dupe.  ALSO:  So where is the &quot;Screens and Graphics menu&quot; you refer to above?  I didn't see one.  

Now I also looked at downloading a VIA driver and installing it.  Did teh download, but cannot find where it went, cannot find the command line, and cannot work out the syntax of the Linux DOS.  I wasn't expecting so many problems, beginning to think soem of teh posts I read in ZD Net are correct, its for geeks only.

[EDIT] Now I cannot even get the paragraph breaks to appear in the Forum, ohhh so many doubts creeping in about this OS
[Second EDIT]After 5 attempts the paragraph breaks are finally working.  Is this the norm for Linux?

---

### Post by matey3 on 2009-05-27
I know this is no solution but have you tried the Ctrl Alt + key combo?
+ gives more res and - gives less.



> **Chalfont said:**
> I have a similar problem to teh correspondent, have loaded 9.04 Ubuntu onto an old eMachines desktop with VIA graphics chipset, and it gives me two resolutions... 800x600 or 800x480.  Now this isn't good enough, XP gave me up to 1280x...  

Followed the Wikis and guides, did the >System > Adminstration > Display and similar to teh correspondent above it showed the dialogue box empty with the message no proprietary drivers installed.  No button or function at all to get a list (which apparently there should be).  Yes I am on the internet as i am typing this!   

So if I cannot get a decent display then it has to be goodbye Linux and back to being a Micro$oft dupe.  ALSO:  So where is the &quot;Screens and Graphics menu&quot; you refer to above?  I didn't see one.  

Now I also looked at downloading a VIA driver and installing it.  Did teh download, but cannot find where it went, cannot find the command line, and cannot work out the syntax of the Linux DOS.  I wasn't expecting so many problems, beginning to think soem of teh posts I read in ZD Net are correct, its for geeks only.

[EDIT] Now I cannot even get the paragraph breaks to appear in the Forum, ohhh so many doubts creeping in about this OS
[Second EDIT]After 5 attempts the paragraph breaks are finally working.  Is this the norm for Linux?

I had no problem with Ubuntu 8.04 (I never upgraded to 8.10 so I dont know if 8.10 had similar problem) But I can tell you that everything worked in 8.04, in fact I changed my monitor type to what I have which is an Acer flat screen AL1914 and bingo , Ubuntu gave me a whole lot of choices for high resolution. (I mean I was looking into finding drivers for my on-board S3 Video card but that was not the problem the brand of monitor was).
Now in 9.04 I cannot change my monitor from Unknown to Acer at all.
 But still, I do get a decent  res. 


**BTW** 
I was complaining about the Top **Panel** and how I could Not move it around but that was my bad, the Properties on the Panel has the drop-down menu with 4 sides of screen already in it.
Also if you got to Panel's Properties and Un-check the "Expand" button then you can also drag it around the screen (then you can put the check-mark back in that box if you wanted to)!

---

### Post by CatKiller on 2009-05-27
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

