---
title: "How to set screen resolution on Dell laptop"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-06-24
I am running Intrepid on my Dell Inspiron 1300. 
How can I set the screen resolution? 
The highest available option is only 1024 X 768.
How can I get a better screen resolution?
Thannks

---

### Post by MooseMagnet on 2009-06-24
Bump. Sorry, but I really need to use my laptop today.
I was able to set the res with 915resolution, but that's no longer available.
What can I do to set the resolution? And why was 915res removed?
Thanks

---

### Post by Gaweph on 2009-06-24
Hello,

What kind of graphics card do you have installed, and are the drivers installed.

(fingers crossed its nvidia) i always havfe much better luck with that and ubuntu

---

### Post by MooseMagnet on 2009-06-24
I don't know what graphics card. Yes the drivers are installed.
I had the resolution set with 915resolution, and all was fine.
But now that application is no longer available.
How can I set the resolution?
I rebooted and it says Intel 915GM/910GML Graphics
And Native Resolution = 1280 X 800
But this highest resolution available via System -> Screen Resolution is 1024 x 768

---

### Post by MooseMagnet on 2009-06-24
Moan....

Nobody knows????

WHY did they remove 915 resolution? WHY WHY WHY???

Open source? More like open SORE.

Sorry, but it's very frustrating. It's the same laptop battles with Ubuntu again and again and again.

Does anyone know how to set the screen resolution on a dell laptop? Previously it was marvelously managed with 915resolution, but that has for some reason been removed.

How can I set the resolution? 

Please help. Thanks.

---

### Post by MooseMagnet on 2009-06-24
Maybe this is the card:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by m4tic on 2009-06-24
Try upgrading to 9.04 maybe it'll work

---

### Post by MooseMagnet on 2009-06-24
That's too risky. It's never worked before. It's always been a problem getting the screen resolution correct with Ubuntu. 915resolution did the job really well, but for some reason it has been removed.

I found this:

[http://www.geocities.com/stomljen/download.html](http://www.geocities.com/stomljen/download.html)

Can you tell me how I can install it?

Thanks

---

### Post by mikewhatever on 2009-06-24
Can you post the output of **xrandr -q** command.

---

### Post by MooseMagnet on 2009-06-24
rich@rich-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2384 x 768
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 640x480+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9* 
TV disconnected (normal left inverted right x axis y axis)
rich@rich-laptop:~$

---

### Post by mikewhatever on 2009-06-24
Try changing the resolution to 1280x800 with the following command:
xrandr -s 1280x800

---

### Post by MooseMagnet on 2009-06-24
rich@rich-laptop:~$ sudo xrandr -s 1280x800
[sudo] password for rich: 
Size 1280x800 not found in available modes

---

### Post by mikewhatever on 2009-06-24
How about this one to add the desired mode:
xrandr --addmode LVDS 1280x800

---

### Post by MooseMagnet on 2009-06-24
rich@rich-laptop:~$ xrandr --addmode LVDS 1280x800
xrandr: cannot find mode "1280x800"
rich@rich-laptop:~$

---

### Post by mikewhatever on 2009-06-24
That's odd. Have you tried getting and installing the 915resolution package from hardy repositories? It only have two dependencies and should, I think, install fine. Hope it works as expected too.
[http://packages.ubuntu.com/hardy/915resolution](http://packages.ubuntu.com/hardy/915resolution)

If that doesn't work, I think your best shot would be to manually modify xserver.xorg. Here is a good example.
[http://ubuntuforums.org/showthread.php?t=1148731](http://ubuntuforums.org/showthread.php?t=1148731)

---

### Post by MooseMagnet on 2009-06-24
Can't copy/paste from the package installer window. I'll try to get all this right.


 xserver-xorg-video-intel conflicts with 915resolution
  915resolution (version 0.5.3-1ubuntu1) is to be installed.
dpkg: error processing /tmp/915resolution_0.5.3-1ubuntu1_i386.d
 conflicting packages - not installing 915resolution
Errors were encountered while processing:
 /tmp/915resolution_0.5.3-lubuntu_i386.d

---

### Post by mikewhatever on 2009-06-24
It looks like 915resolution package conflicts with the graphics driver in Intrepid. That usually means that the conflicting package will be removed before the desired one is installed, in which case, installing 915resolution isn't a good idea.

---

### Post by MooseMagnet on 2009-06-24
But that's what I did.

Now I've got to get the Intrepid driver installed again. Can you tell me how to do that?

---

### Post by mikewhatever on 2009-06-24
**sudo apt-get install xserver-xorg-video-intel**

It looks like for the time being you are stuck with the wrong resolution or Hardy.:)

---

### Post by MooseMagnet on 2009-06-24
It doesn't even work after re-installing intel.
I can't believe this. SOOOOOO  frustrating.

Such a mess. Do the developers realize there are more than 3 or 4 people using laptops? Never mind.

I'll have to re-install 915resolution.

I can NOT believe this is SO difficult.

---

### Post by MooseMagnet on 2009-06-24
It has turned into a huge problem. It's a mess with 915resolution, and a mess with the intel driver also.

I need some serious help. Please.

It was working fine until I changed the screen resolution using with System -> Screen Resolution. Now I can barely use it. 

I need help, please.

---

### Post by mikewhatever on 2009-06-24
Well, what's the problem now?

---

### Post by MooseMagnet on 2009-06-24
I re-installed the intel driver.

All is well on the external monitor. But only part of the screen is visible on my laptop. The screen display on my laptop is not useable.

This is a nightmare.

The refresh rate is slow and video streams are shaky, and it's tough to click on links and buttons. 

Basically the entire screen display function of the laptop is gone.

---

### Post by blackened on 2009-06-24
There is a specific order you have to follow to add available resolutions to xrandr and, thus, the display settings dialog.

The correct way is best described here -> [https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions"), but I'll be happy to help if you have any additional questions.

---

### Post by MooseMagnet on 2009-06-25
Very Excellent. Thank you!!

I'll post again any problems or successes.

Thank you.

R-

---

### Post by machadoug on 2009-06-25
MooseMagnet,

I had 8.10 installed with 915resolution on my ACER Aspire 5610, with the same Intel graphic card. 
I bought a secondary monitor and wanted to use extended instead of cloned and didn't work, and I was told it would work if I upgrade to 9.04, which worked out of the box, however I got the same screen resolution problem. After trying several possible fixes I decided to downgrade to 8.04.

My best Ubuntu experience so far is with 8.04. Surprisingly even better than 8.10. I didn't have to install 915resolution neither any other hack to make my wireless driver work. Although I still don't have the dual monitor working, I recommend you to downgrade from 8.10 to 8.04. 8.04 will be supported until 2011. At least it worked for me. :)

Regards,

---

### Post by blackened on 2009-06-26
> **MooseMagnet said:**
> Very Excellent. Thank you!!

I'll post again any problems or successes.

Thank you.

R-

Gladly. 

> **machadoug said:**
> MooseMagnet,

I had 8.10 installed with 915resolution on my ACER Aspire 5610, with the same Intel graphic card. 
I bought a secondary monitor and wanted to use extended instead of cloned and didn't work, and I was told it would work if I upgrade to 9.04, which worked out of the box, however I got the same screen resolution problem. After trying several possible fixes I decided to downgrade to 8.04.

My best Ubuntu experience so far is with 8.04. Surprisingly even better than 8.10. I didn't have to install 915resolution neither any other hack to make my wireless driver work. Although I still don't have the dual monitor working, I recommend you to downgrade from 8.10 to 8.04. 8.04 will be supported until 2011. At least it worked for me. :)

Regards,

The ever-popular displayconfig-gtk utility is probably what you are missing in later versions. It was removed after Hardy largely because of its fatal reliance on the newly spartan xorg.conf. The maintainers decided to scrap the project in favor of a proper rewrite, though that may have stalled before it ever got started (others would know better than I) as I haven't seen any news concerning said project, though it was proposed ages ago.

---

### Post by ernstv on 2009-10-14
To set up dell inspiron 1300 screen resolution:

cvt 1280 768 60

Then place in /etc/gdm/Init/Default (using the cvt outputs):

xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode LVDS 1280x768_60.00
xrandr --output LVDS --mode 1280x768_60.00

Logout and log in again...
Voila!

---

