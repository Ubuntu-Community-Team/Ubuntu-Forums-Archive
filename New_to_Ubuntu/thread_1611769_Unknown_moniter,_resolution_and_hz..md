---
title: "Unknown moniter, resolution and hz."
date: 2010-11-02
forum: New to Ubuntu
---

### Post by skatergirl on 2010-11-02
I got the unknown moniter problem. I searched around a little on the site, but i still dont understand what to do. Yeah i know its probably been posted a million times.

Im a noob...

I need to change resolution and change hz? (is that what its called?)

The screen makes my eyes hurt =(

---

### Post by dentharg on 2010-11-02
In Ubuntu/Gnome go to System -> Preferences -> Monitors.

There you can change resolution and refresh rate.

---

### Post by skatergirl on 2010-11-02
Yeah i know but it doesnt work, it says "unknown monitor" and i cant change anything. :)

---

### Post by Peterfc on 2010-11-02
> **dentharg said:**
> In Ubuntu/Gnome go to System -> Preferences -> Monitors.

There you can change resolution and refresh rate.

I have the same problem and there is no way to change the monitor.

---

### Post by skatergirl on 2010-11-02
> **Peterfc said:**
> I have the same problem and there is no way to change the monitor.

Let me know if/how you solve it!

Anyway i think it can be fixed by writing something in the terminal?

But i dont know exactly what and i dont think i dare to try... lol

---

### Post by rlt9999 on 2010-11-02
I'm new here so go easy on me... I just installed ubuntu 10.10 last night.
 
I have basically the same issue. When I ran ubuntu 10.10 from the CD my video resolution was at 1366x768 and I had full control of everything in the "Monitor" menu, and my monitor was correctly identified as an Acer. Now that I have 10.10 installed on the hard drive I am limited to to screen resolutions, 800x600 and 800x480 and none of the other options can be changed. It also lists my monitor as "unknown".
 
My main question I guess is why does the video work correctly and recognise my monitor when run from the CD and not work when it's installed to the computer?
 
Being a complete newbie to ubuntu I have no idea how to fix it or whether it's a video driver issue or something else. If it was a Windows problem I'd be on it in a flash! lol
 
I've done a quick search of the forums here and I must say that there seems to be tons of good advice listed here, I'm just not finding an answer to this seemingly common problem.
 
Thanks in advance for any help...
Best regards,
Bob

---

### Post by Grenage on 2010-11-02
It's usually down to duff EDID data; I have a rough guide [here]("http://www.grenage.com/xorg.html") (fair warning, I wrote it).

If you run through that and have no joy, post back and I'll see if I can help.  An understanding is always better than a plain solution.

---

### Post by skatergirl on 2010-11-02
> **Grenage said:**
> It's usually down to duff EDID data; I have a rough guide [here]("http://www.grenage.com/xorg.html") (fair warning, I wrote it).

If you run through that and have no joy, post back and I'll see if I can help.  An understanding is always better than a plain solution.


Thanks,

ive read through it but i dont quite understand how to do it.

Do you know if there is a more detailed "manual" to follow?

---

### Post by Peterfc on 2010-11-02
Hi Grenage

Thanks for taking the time to try and help us. From what you say the next thing to do is 

sudo apt-get install xresprobe

And then

sudo ddcprobe

Both from a terninal 

Thanks

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by ironic.demise on 2010-11-02
Press the "auto" button on your monitor.

---

### Post by skatergirl on 2010-11-02
So you have to be a semi-hacker to make this work i guess... im about to throw the computer out the window

---

### Post by rlt9999 on 2010-11-02
> **Grenage said:**
> It's usually down to duff EDID data; I have a rough guide [here]("http://www.grenage.com/xorg.html") (fair warning, I wrote it).
 
If you run through that and have no joy, post back and I'll see if I can help. An understanding is always better than a plain solution.
 
Thanks Grenage, but my main question is why does the video work correctly and recognise my monitor when run from the CD and not work when Ubuntu 10.10 is installed to the computer? I am trying to understand why it isn't working more than trying to resolve the problem. I'm the type of person that needs to know why something doesn't work. :confused:
 
Best regards,
Bob

---

### Post by rlt9999 on 2010-11-03
> **Grenage said:**
> It's usually down to duff EDID data; I have a rough guide [here]("http://www.grenage.com/xorg.html") (fair warning, I wrote it).

If you run through that and have no joy, post back and I'll see if I can help.  An understanding is always better than a plain solution.

I just did the ddcprobe and this is the full output that I got:

bob@bob-GL308AA-ABA-m8109n:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: GT216 Board - 0682vb12 Chip Rev
memory: 14336kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

The last line seems to me to be a problem, although I'm not 100% sure what I'm doing... :(

Best regards,
Bob

---

### Post by Grenage on 2010-11-03
**skatergirl**:

If you can post your monitor make and model, your desired resolution, plus the results of:

```
lspci | grep -i VGA
```

I can try and give you a config that works.


**rlt9999**:

I don't know why it often works from the CD, but not an install; I've seen it before, and always assumed that the CD must be using a slightly different system.

Judging by your results, it does appear that EDID is the issue; if you have a spare video cable, you can try swapping that first.  Failing that, we can go the xorg.conf route?

**Peterfc**:

Did you get anywhere?

---

### Post by Peterfc on 2010-11-03
Hi Grenage

sorry no the problem still remains. I am now on a different monitor as i have taken my desktop home as i have more time. now my resolution is 1360 X 768 ( 16:9 ) 

i am now using a 32in Toshiba TV (new) as my home monitor.

I have spent a lot of time in the search section. But can't seem to find an answer.

When i did sudo ddcprobe the reply i got is below


serial: 01010101
manufacture: 255 2009
input: sync on green, analog signal.
screensize: 70 39
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x800@60
ctiming: 1280x1024@60
dtiming: 1360x768@70
dtiming: 1280x768@70
monitorname: TOSHIBA-TV
monitorrange: 31-65, 56-76

---

### Post by Grenage on 2010-11-03
Well it looks like it's getting the right information there, especially if you're running the native resolution.  Are you planning on taking the PC back to the other monitor?

---

### Post by Peterfc on 2010-11-03
Hi Grenage

I took my machine to work so i could run it side by side to another machine that runs perfect. 

Both machines identical Dell Dimensions 1100's

---

### Post by Grenage on 2010-11-03
Ok, so it's not on the Toshiba TV now.  If you're still getting the same problem, and you swapped out the cable, post the current monitor make/model; I can jot a quick xorg.conf that will probably work.

---

### Post by Peterfc on 2010-11-03
> **Grenage said:**
> Ok, so it's not on the Toshiba TV now.  If you're still getting the same problem, and you swapped out the cable, post the current monitor make/model; I can jot a quick xorg.conf that will probably work.

Thanks for the info i will do that as soon as i get home and repost here

Peter

---

### Post by skatergirl on 2010-11-03
> **Grenage said:**
> **skatergirl**:

If you can post your monitor make and model, your desired resolution, plus the results of:

```
lspci | grep -i VGA
```

I can try and give you a config that works.


**rlt9999**:

I don't know why it often works from the CD, but not an install; I've seen it before, and always assumed that the CD must be using a slightly different system.

Judging by your results, it does appear that EDID is the issue; if you have a spare video cable, you can try swapping that first.  Failing that, we can go the xorg.conf route?

**Peterfc**:

Did you get anywhere?

Appreciate your willingness to help!

monitor  SONY CPD-4401 TRINITRON COLOR MONITOR


lspci | grep -i VGA:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

i now have 1024x763... its ok, but i would like to have everything look a little smaller... i dont know which resolution that is. 

But the most important thing is the hz. Right now i cant look at the screen without my eyes hurting.

---

### Post by Grenage on 2010-11-03
> **skatergirl said:**
> Appreciate your willingness to help!

monitor  SONY CPD-4401 TRINITRON COLOR MONITOR


lspci | grep -i VGA:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

i now have 1024x763... its ok, but i would like to have everything look a little smaller... i dont know which resolution that is. 

But the most important thing is the hz. Right now i cant look at the screen without my eyes hurting.

Try this out:

Move the old xorg.conf (if it exists; if not, you'll get an error - ignore it):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.oldconf
```


Edit a new one:
```
gksu gedit /etc/X11/xorg.conf
```

Add this text to the document, then save it:
```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Micron"
	ModelName "CPD-4401"
	HorizSync 30 - 107
	VertRefresh 48 - 120
Modeline "1280x1024_85.00"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82845G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

Then restart GDM, or just reboot the whole machine.  The above xorg.conf should give you a resolution of 1280x1024 at 85mhz refresh, if the monitor can handle it.

**If** that does not work, and you cannot log back into the gnome desktop (you get a terminal prompt), you can simply remove the xorg.conf and reboot:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by skatergirl on 2010-11-03
omg!!!!!!!!!!!!!!!!!!

it worked!!!!!!


Thank you!

Thank you thank you thank you thank you! Thank you thank you thank you thank you! Thank you thank you thank you thank you! Thank you thank you thank you thank you! Thank you thank you thank you thank you! Thank you thank you thank you thank you! 

You dont know how much you helped me right now!

---

### Post by moopere on 2010-11-03
Great stuff Grenage and thanks for helping everyone in this thread.

I'm going to pop over to launchpad now because its simply ridiculous that its 2010 and this problem of displays and resolutions has been with us since day 0 in Linux (well...day 0 for X anyway :).  

Amaizing things happening in Ubuntu land and Linux in general, but we still can't seem to create a dumb and simple tool to do this task which trips up masses of people, newbs and veterans alike.

Cheers, Moo

---

### Post by Grenage on 2010-11-03
> **skatergirl said:**
> omg!!!!!!!!!!!!!!!!!!

it worked!!!!!!


Thank you!

No problem, glad it's been sorted. :)

> **moopere said:**
> I'm going to pop over to launchpad now because its simply ridiculous that its 2010 and this problem of displays and resolutions has been with us since day 0 in Linux (well...day 0 for X anyway :).  

Amaizing things happening in Ubuntu land and Linux in general, but we still can't seem to create a dumb and simple tool to do this task which trips up masses of people, newbs and veterans alike.

I agree.  The detection is great when in works, but I think that there should be the option of manually specifying resolution and refresh rate via the GUI.  Yes, there is the chance that a user will specify settings that the monitor or card can't handle - but it could revert after x seconds.

If there is a tool that does it, I've not seen it; I'd make one myself, but I can't code to save my life (although a basic tool should be simple).

---

### Post by Peterfc on 2010-11-03
> **Grenage said:**
> No problem, glad it's been sorted. :)



I agree.  The detection is great when in works, but I think that there should be the option of manually specifying resolution and refresh rate via the GUI.  Yes, there is the chance that a user will specify settings that the monitor or card can't handle - but it could revert after x seconds.

If there is a tool that does it, I've not seen it; I'd make one myself, but I can't code to save my life (although a basic tool should be simple).

I have been a user since Dapper and not a day goes by when i am glad i am using a system where if i need help it is there. 

Thanks

---

### Post by rlt9999 on 2010-11-03
> **Grenage said:**
> **skatergirl**:
 
If you can post your monitor make and model, your desired resolution, plus the results of:
 
```
lspci | grep -i VGA
```
 
I can try and give you a config that works.
 
 
**rlt9999**:
 
I don't know why it often works from the CD, but not an install; I've seen it before, and always assumed that the CD must be using a slightly different system.
 
Judging by your results, it does appear that EDID is the issue; if you have a spare video cable, you can try swapping that first. Failing that, we can go the xorg.conf route?
 
**Peterfc**:
 
Did you get anywhere?
 
I also tryed to do the dccprobe when running Ububtu from the CD but that didn't work as it wouldn't run giving me a bad command error. I wanted to compare and see if I could find what was causing the problem. When run from CD everything is functional in the "Monitor" panel and it lists my monitor correctly. When running my installed Ubuntu the monitor is listed as unknown and auto detect doesn't do anything. My monitor is an Acer 18.5" LCD (E181H). I'm getting ready to head out to work right now, so I'll post the results of the lspci | grep -i VGA later. 
 
Thanks again,
Bob

---

### Post by Grenage on 2010-11-03
> **rlt9999 said:**
> I also tryed to do the dccprobe when running Ububtu from the CD but that didn't work as it wouldn't run giving me a bad command error. I wanted to compare and see if I could find what was causing the problem. When run from CD everything is functional in the "Monitor" panel and it lists my monitor correctly. When running my installed Ubuntu the monitor is listed as unknown and auto detect doesn't do anything. My monitor is an Acer 18.5" LCD (E181H). I'm getting ready to head out to work right now, so I'll post the results of the lspci | grep -i VGA later. 
 
Thanks again,
Bob

Sounds good.  I'm not at my computer as frequently in the eve as I am the day, but will be around this evening.

---

### Post by rlt9999 on 2010-11-03
> **Grenage said:**
> **skatergirl**:

If you can post your monitor make and model, your desired resolution, plus the results of:

```
lspci | grep -i VGA
```I can try and give you a config that works.


**rlt9999**:

I don't know why it often works from the CD, but not an install; I've seen it before, and always assumed that the CD must be using a slightly different system.

Judging by your results, it does appear that EDID is the issue; if you have a spare video cable, you can try swapping that first.  Failing that, we can go the xorg.conf route?

**Peterfc**:

Did you get anywhere?


Hi Grenage,

Here is the results of the lspci grep -i VGA:

bob@bob-GL308AA-ABA-m8109n:~$ lspci | grep -i VGA
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
bob@bob-GL308AA-ABA-m8109n:~$ 

And my monitor is an Acer E181H TFT LCD (18.5") as posted earlier.

My video cable is hard wired to my monitor so trying another is impossible, although I doubt that is the problem anyway. As I said Ububtu recognises my monitor when run from the CD so I am assuming that something isn't working the way it should during or after the install.

From my experience with Windows, 1366x768 at 60Hz seems to be the optimum resolution for this monitor and 800x600 just ain't gettin' it trying to run Ubuntu! :(

I do appreciate your efforts to help me, I just wish I knew how to make Ubuntu recognise the monitor the way it does when running from the CD. Do you think it might work if I tryed installing a version previous to 10.10?

Thanks again,
Bob

---

### Post by Grenage on 2010-11-04
> **rlt9999 said:**
> Hi Grenage,

Here is the results of the lspci grep -i VGA:

bob@bob-GL308AA-ABA-m8109n:~$ lspci | grep -i VGA
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
bob@bob-GL308AA-ABA-m8109n:~$ 

And my monitor is an Acer E181H TFT LCD (18.5") as posted earlier.

My video cable is hard wired to my monitor so trying another is impossible, although I doubt that is the problem anyway. As I said Ububtu recognises my monitor when run from the CD so I am assuming that something isn't working the way it should during or after the install.

From my experience with Windows, 1366x768 at 60Hz seems to be the optimum resolution for this monitor and 800x600 just ain't gettin' it trying to run Ubuntu! :(

I do appreciate your efforts to help me, I just wish I knew how to make Ubuntu recognise the monitor the way it does when running from the CD. Do you think it might work if I tryed installing a version previous to 10.10?

10.04 'might' prove better, but it's total luck.  So many people have problems with this, and I can't even speculate how many gave up on Linux due to not being able to set a resolution. Try this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "emachine"
	ModelName "E181H"
	HorizSync 31 - 80
	VertRefresh 56 - 75
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GT216"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1366x768"
	EndSubSection
EndSection
```

Assuming that you're using the proprietary Nvidia driver, otherwise swap *nvidia* for *nv* (or even.... *vesa*!).

I never quite understood the whole 1366 and 1360 resolution malarkey.  CVT gives me a modeline with 1368x768, so go with the above, and we can try a 1360*768 if it looks bad.

---

### Post by rlt9999 on 2010-11-04
> **Grenage said:**
> 10.04 'might' prove better, but it's total luck.  So many people have problems with this, and I can't even speculate how many gave up on Linux due to not being able to set a resolution. Try this:

```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "emachine"
    ModelName "E181H"
    HorizSync 31 - 80
    VertRefresh 56 - 75
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "GT216"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1366x768"
    EndSubSection
EndSection
```Assuming that you're using the proprietary Nvidia driver, otherwise swap *nvidia* for *nv* (or even.... *vesa*!).

I never quite understood the whole 1366 and 1360 resolution malarkey.  CVT gives me a modeline with 1368x768, so go with the above, and we can try a 1360*768 if it looks bad.

Hi Grenage,

When I tried to move the xorg.conf file I found that one didn't exist. So I created one as you described and rebooted the machine. It booted to a terminal prompt, so I deleted the xorg.conf file that I had just created and rebooted to the GUI again. I'm totally lost now, where do I go from here? :confused:

Sorry if my total lack of knowledge on this is annoying, :( But I'm not going to just give up as I'm sure that many have by this point!

Thanks again!
Bob

---

### Post by Grenage on 2010-11-04
> **rlt9999 said:**
> Hi Grenage,

When I tried to move the xorg.conf file I found that one didn't exist. So I created one as you described and rebooted the machine. It booted to a terminal prompt, so I deleted the xorg.conf file that I had just created and rebooted to the GUI again. I'm totally lost now, where do I go from here? :confused:

Sorry if my total lack of knowledge on this is annoying, :( But I'm not going to just give up as I'm sure that many have by this point!

Thanks again!
Bob

That means the example I gave you was no good, try using *nv* as the driver.  If that doesn't work, try *vesa*; we just want to see if it's the driver or the settings it doesn't like.

Nvidia uses the proprietary driver.
nv is (I think) the open source one with no real acceleration.
Vesa is really basic.

---

### Post by rlt9999 on 2010-11-05
> **Grenage said:**
> That means the example I gave you was no good, try using *nv* as the driver.  If that doesn't work, try *vesa*; we just want to see if it's the driver or the settings it doesn't like.

Nvidia uses the proprietary driver.
nv is (I think) the open source one with no real acceleration.
Vesa is really basic.

Hi Grenage,

As I mentioned above Nvidia didn't work for the driver parameter. I got home from work just now and tried making the xorg.conf file with the nv instead and it is working now. I am in 1366x768 mode and everything in the "Monitors" panel now has options that can be changed. Thank you very much!

Looking at the code you made for my setup I see you have included:

```
DefaultDepth 24
Subsection "Display"
              Depth 24
```Am I correct that this gives 24bit color mode and that I could replace the 24 with 32 to give 32bit color?

Going a step further, is it possible to now update my drivers the the proprietary Nvidia drivers to make better use of my graphics card or would that set me back to the problems I was having?

Thanks again!

Best regards,
Bob

---

### Post by Grenage on 2010-11-05
> **rlt9999 said:**
> Hi Grenage,

As I mentioned above Nvidia didn't work for the driver parameter. I got home from work just now and tried making the xorg.conf file with the nv instead and it is working now. I am in 1366x768 mode and everything in the "Monitors" panel now has options that can be changed. Thank you very much!

Looking at the code you made for my setup I see you have included:

```
DefaultDepth 24
Subsection "Display"
              Depth 24
```Am I correct that this gives 24bit color mode and that I could replace the 24 with 32 to give 32bit color?

Going a step further, is it possible to now update my drivers the the proprietary Nvidia drivers to make better use of my graphics card or would that set me back to the problems I was having?

Thanks again!

Best regards,
Bob

Ahoy there.

Glad to hear that some headway has been made; you can indeed change the 24 to 32.  Updating to the proprietary driver would probably be beneficial, as the performance is a good deal better.  If no drivers appear under *Administration/Additional drivers*, then you might have some luck on the Nvidia website.  It will basically come down to whether or not it is supported.

EDIT: Apparently, it is: [http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html)

Doing it via additional drivers is better, but at least you have a fall-back.

---

### Post by Peterfc on 2010-11-05
HI Grenage

I did as you suggested and used another cable in fact i got a new one but it didn't help. I have tried another monitor and still this makes no difference. 

If need be i can get used to this if i have to.

1360 X 768 as i use a 32in TV.

Peter

---

### Post by Grenage on 2010-11-05
Hi, Peter.

So are you keeping the TV with that monitor?  You mentioned that you were getting 1366 x 768, what settings do you need to change?

---

### Post by Peterfc on 2010-11-05
Hi Grenage

As i live on my own it's easy to make do with only a TV instead of TV and monitor. The resolution 1024 X 768 seems fine. I do even my work monitor makes no difference. I have two Dell Dimensions and a Dell laptop all Four/ Five years old and every update has worked fine by the last on this open machine. 

Peter

---

### Post by Grenage on 2010-11-05
I think I might be confused, which happens more often than I'd like.  do you want the display on the monitor, rather than the TV, and is it not giving you the native resolution there?

---

### Post by rlt9999 on 2010-11-05
> **Grenage said:**
> Ahoy there.
 
Glad to hear that some headway has been made; you can indeed change the 24 to 32. Updating to the proprietary driver would probably be beneficial, as the performance is a good deal better. If no drivers appear under *Administration/Additional drivers*, then you might have some luck on the Nvidia website. It will basically come down to whether or not it is supported.
 
EDIT: Apparently, it is: [http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.12-driver-uk.html)
 
Doing it via additional drivers is better, but at least you have a fall-back.
 
Hi Grenage,
 
I tried enabling the proprietary Nvidia driver that was found when I went to Additional Drivers. Once activated it made a new xorg.conf file through nvidia-xserver. When I rebooted I was back to running at 800x600 mode with unknown monitor reported by the Monitors panel. I then tried editing xorg.conf to add the code you gave me for my Acer monitor and when I tried booting with that file I was booting to a terminal prompt again. Surely there must be a way to get this running with the enhanced Nvidia drivers even though it doesn't recognise my monitor.
 
At this time I have removed the proprietary driver and have things restored back to where I'm in 1366x768 mode using the xorg.conf code that you provided, with the driver line set as "nv". At least I am making progress with understanding Ubuntu enough to be able to get back to this state by myself! :)
 
BTW. changing the 24 to 32 in my xorg.conf file trying to get 32 bit color also results in booting to the command prompt. No big deal, I figured out how to edit in command mode with nano and got back to the GUI.
 
Best regards,
Bob

---

### Post by rlt9999 on 2010-11-06
Update:

While searching through tons of links relating to this problem I came across a post by someone that mentioned he had a KVM switch attached to his system. And until reading this I had forgotten about mine as I've been using it for more than 2 years. It's an electronic one that switches between computers when the scroll lock key is pressed twice. I'm going to unhook my monitor cable from the switch and go straight to the video card and try another install to see if that makes any difference. I'm hoping that my problem is something this simple and I'll post results later.

Best regards,
Bob

---

### Post by rlt9999 on 2010-11-06
> **rlt9999 said:**
> Update:

While searching through tons of links relating to this problem I came across a post by someone that mentioned he had a KVM switch attached to his system. And until reading this I had forgotten about mine as I've been using it for more than 2 years. It's an electronic one that switches between computers when the scroll lock key is pressed twice. I'm going to unhook my monitor cable from the switch and go straight to the video card and try another install to see if that makes any difference. I'm hoping that my problem is something this simple and I'll post results later.

Best regards,
Bob

I just finished testing the items listed above and have concluded that the KVM switch has nothing to do with my unknown monitor problems. I disconnected the monitor cable from the KVM switch and connected it directly to the video card then booted the computer to Ubuntu and ran ddcprobe. I still get a EDID failure on this machine. So then I decided to try installing Ububtu on the other machine which is also an HP Media Center. This machine was still connected to the monitor through the KVM switch and it installed correctly with the correct monitor listed in the Monitor panel. The only difference is that the other machine has the onboard video enabled and this one has the Nvidia Geforce 220 graphics card.

I am at a total loss now. If I can't get the Nvidia driver to work on this machine running Ubuntu is useless to me. So I guess I am almost at the point of joining the users that tried Ububtu and gave up on it.

I would bet that if I enabled the onboard graphics on this machine and moved the monitor cable to that port that Ubuntu would recognise my monitor the way it should. However, most of the things I use this computer for are highly graphics related and this is why I upgraded the graphics card in the first place.

Anyone have any other ideas regarding how to get this to work with the proprietary driver? I would greatly appreciate it!

Best regards,
Bob

---

### Post by egkeat on 2010-11-06
I am a very new user here and currently running Ubuntu in Vista using an HP monitor. I've had this same problem and for now the only way I could fix it was going to power management and setting my monitor to never sleep. Thing is, I left the computer sleep set to 1hr, and the monitor still powered down to sleep as well. On wake up, my monitor settings were still there, everything was fine.

---

### Post by Grenage on 2010-11-08
> **rlt9999 said:**
> I just finished testing the items listed above and have concluded that the KVM switch has nothing to do with my unknown monitor problems. I disconnected the monitor cable from the KVM switch and connected it directly to the video card then booted the computer to Ubuntu and ran ddcprobe. I still get a EDID failure on this machine. So then I decided to try installing Ububtu on the other machine which is also an HP Media Center. This machine was still connected to the monitor through the KVM switch and it installed correctly with the correct monitor listed in the Monitor panel. The only difference is that the other machine has the onboard video enabled and this one has the Nvidia Geforce 220 graphics card.

I am at a total loss now. If I can't get the Nvidia driver to work on this machine running Ubuntu is useless to me. So I guess I am almost at the point of joining the users that tried Ububtu and gave up on it.

I would bet that if I enabled the onboard graphics on this machine and moved the monitor cable to that port that Ubuntu would recognise my monitor the way it should. However, most of the things I use this computer for are highly graphics related and this is why I upgraded the graphics card in the first place.

Anyone have any other ideas regarding how to get this to work with the proprietary driver? I would greatly appreciate it!

Best regards,
Bob

Hi again; sorry about the delayed reply - busy weekend!

Would you be able to post the xorg.conf nvidia-settings gives you?  We can try tweaking it, and see where that gets us.  As a side-note, I've seen KVMs and Amps cause the EDID problem, too - good call ruling it out.

---

### Post by rlt9999 on 2010-11-08
> **Grenage said:**
> Hi again; sorry about the delayed reply - busy weekend!
 
Would you be able to post the xorg.conf nvidia-settings gives you? We can try tweaking it, and see where that gets us. As a side-note, I've seen KVMs and Amps cause the EDID problem, too - good call ruling it out.
 
Hi Grenage,
 
I'll do that tonight when I get home from work, and thank you again for all of your help.
 
Best regards,
Bob

---

### Post by alil2cul4u on 2010-11-10
Hey Grenage,

I was wondering if you could help me as well? I used the xorg.conf file you made for Skategirl and changed it a little bit to get it to work but I dont know how to change everything and what to change it to... I have a KDS USA K717S monitor and I looked it up on the KDSUSA.com website and it looks like max is

Resolution - 1280x1024
Horizontal Freq. - 31-80 hz
Vertical Freq. - 60 - 75 hz
Bandwidth (thats what the site said) - 135 Mhz

```
This Is what I get when I ran the code you asked to run

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

Thanks in advance...

---

### Post by Grenage on 2010-11-11
> **alil2cul4u said:**
> Hey Grenage,

I was wondering if you could help me as well? I used the xorg.conf file you made for Skategirl and changed it a little bit to get it to work but I dont know how to change everything and what to change it to... I have a KDS USA K717S monitor and I looked it up on the KDSUSA.com website and it looks like max is

Resolution - 1280x1024
Horizontal Freq. - 31-80 hz
Vertical Freq. - 60 - 75 hz
Bandwidth (thats what the site said) - 135 Mhz

```
This Is what I get when I ran the code you asked to run

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

Thanks in advance...

Hi there,

I've never had an SiS card to play around with (not since using Linux), but I believe the driver reference to simply be *sis*.  It might be worth giving that a go?

---

### Post by rlt9999 on 2010-11-11
> **Grenage said:**
> Hi again; sorry about the delayed reply - busy weekend!
 
Would you be able to post the xorg.conf nvidia-settings gives you? We can try tweaking it, and see where that gets us. As a side-note, I've seen KVMs and Amps cause the EDID problem, too - good call ruling it out.
 
Hi Grenage,
 
I've been busy here also and I just got around to getting back to this. I just did a new install of Ubuntu and to my surprise it recognised my monitor when it booted this time. Not sure why it did this time and didn't the past 5 or 6 times. I then enabled the Nvidia driver and I was back to booting to the command prompt again and after renaming the xorg.conf file I'm in the GUI at 800x600 like before.
 
Here is the contents of the xorg.conf that the Nvidia drivers made.
 
 
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
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```
 
I hope that you can help getting this to work with the Nvidia drivers although it was encouraging that the install recognised the vidio to some degree this last time for some reason.
 
EDIT: As an afterthought, when the fresh install booted to the correct video settings and recognised my monitor I went to a terminal and looked for the xorg.conf file to see what was in it but there wasn't one. So I'm really confused now! :confused:
 
Best regards,
Bob

---

### Post by Grenage on 2010-11-12
> **rlt9999 said:**
> EDIT: As an afterthought, when the fresh install booted to the correct video settings and recognised my monitor I went to a terminal and looked for the xorg.conf file to see what was in it but there wasn't one. So I'm really confused now! :confused:

Hi there,

xorg.conf isn't used by default, at least, not these days; the system will however use one if it is present.  Nvidia (and probably ATI catalyst) drivers create one when installed.

I'm curious about the drivers, and beginning to wonder if there is an issue with the drivers being used for your card.  Try this xorg.conf (essentially what we used before):

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "emachine"
	ModelName "E181H"
	HorizSync 31 - 80
	VertRefresh 56 - 75
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GT216"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1366x768"
	EndSubSection
EndSection
```

I suspect that it might not work, and this looks like me might have a 10.10 bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596)

Do you get the option of using an older driver in the *additional drivers* section?  It might be worth trying that.  If that doesn't work, we could try a manual nvidia driver install.

---

### Post by rlt9999 on 2010-11-13
> **Grenage said:**
> Hi there,

xorg.conf isn't used by default, at least, not these days; the system will however use one if it is present.  Nvidia (and probably ATI catalyst) drivers create one when installed.

I'm curious about the drivers, and beginning to wonder if there is an issue with the drivers being used for your card.  Try this xorg.conf (essentially what we used before):

```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "emachine"
    ModelName "E181H"
    HorizSync 31 - 80
    VertRefresh 56 - 75
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "GT216"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1366x768"
    EndSubSection
EndSection
```I suspect that it might not work, and this looks like me might have a 10.10 bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596)

Do you get the option of using an older driver in the *additional drivers* section?  It might be worth trying that.  If that doesn't work, we could try a manual nvidia driver install.

Hi Grenage,

I'm also starting to think that the driver is the problem. I did check the 10.10 bugs link that you mentioned I'm not getting the black screen at boot problem that those people are reporting. I tried the xorg.conf file that you provided and you were correct that it didn't work, it caused me to boot to a command prompt.

I also made a Ubuntu 10.04 disk and installed it to a new partition. I'm getting the same results with it that I'm having with 10.10 except for the fact that when 10.04 complains about the video errors at boot I get a menu that lets me start the x services and I'm able to get to the GUI in in my correct video mode with my monitor recognized. I then downloaded and ran ddcprobe and I'm still getting the "EDID failed" and of course no output.

The only Nvidia driver that I'm seeing listed when I go to "Additional Drivers" is the "nvidia (current version)" and I believe that is 260. I would like to try an older version of the driver but I need some help with that as I have no idea how to do that.

At least now for some reason I am able to get the proper screen resolution without making a xorg.conf. I just don't have accelerated 2d and 3d functions without the nvidia drivers.

Thank you once more for all of the help that you have provided so far, I do appreciate it! I'll check again here this weekend in case you have time to reply.

Best regards,
Bob

Update: I was just now playing around with the menu that I get in 10.04 when the video causes boot problems and I found a couple of error messages that are probably important:

Failed to initialize the Nvidia device
Screens found, but none have a usable configuration

Also, when I'm booting 10.10 I get the error: nouveau Failed to PRAMIN BAR

Hopefully one of these will point you in the right direction of my problem here. I was doing some reading in the Ubuntu manual pages and found a link to the Nvidia website drivers page and was able to determine that the correct driver for my video card is the 260 version so I'm doubting that older drivers will work as my card isn't listed as being support in them.

---

### Post by Grenage on 2010-11-15
Okay, now this is a long shot (and certainly clutching at straws); this is info from elsewhere, so I've never done it myself:

In a terminal:
```
gksu gedit /etc/default/grub
```

Find the the following line (should be near the top):
```
GRUB_CMDLINE_LINUX_DEFAULT=
```

Add a custom memory allocation (vmalloc=256M) to the end of that line; there will likely be other options in there, such as Quiet Splash.  Here's what it might look like afterwards:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```

Save the changes.

Again, from a terminal:
```
sudo update-grub
```

Then reboot the machine.  If it still doesn't work, apparently changing vmalloc from 256 to 192 can help.

---

### Post by jdsakgj on 2010-11-26
I'm so happy i have found this thread. It should be a worl wide sticky.

> **Grenage said:**
> Try this out:

Move the old xorg.conf (if it exists; if not, you'll get an error - ignore it):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.oldconf
```
Edit a new one:
```
gksu gedit /etc/X11/xorg.conf
```Add this text to the document, then save it:
```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "Micron"
    ModelName "CPD-4401"
    HorizSync 30 - 107
    VertRefresh 48 - 120
Modeline "1280x1024_85.00"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82845G"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1280x1024"
    EndSubSection
EndSection
```Then restart GDM, or just reboot the whole machine.  The above xorg.conf should give you a resolution of 1280x1024 at 85mhz refresh, if the monitor can handle it.

**If** that does not work, and you cannot log back into the gnome desktop (you get a terminal prompt), you can simply remove the xorg.conf and reboot:
```
sudo rm /etc/X11/xorg.conf
```

I also tried this one and it worked. But i have different monitor. And maybe that's why i have problems with playing videos? When i open a video, for example mpg or mp4, avi,... in ubuntu vedo player it just close the program. If i want to play it in VLC there is just sound with black screen. If i remove xorg.conf everything plays nice. But my eyes hurt as i can't change resolution and hz. Thnaks for help! It might help you to know this.

Monitor: 
HP71 17" CTR

lspci:
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

---

### Post by Grenage on 2010-11-29
Hi there,

Specs list that monitor as having a maximum refresh rate of 60 at 1280x1024; if you need 85 (or 75), you'll need to go down to 1024x768.  That said, I'm not sure how that would affect the video playback; I would have imagined that to be drivers!

---

### Post by jdsakgj on 2010-11-29
That would be correct. The best option for me is to have it on 1024 and 75 hz. Can you point me somwehere about the drivers. What should i look for and where?

---

### Post by funky_D on 2010-11-29
hi all,
well.. i have the same problem.. low resolution, the screen is asus 22" (16:9), the image is blurred.. awful.. :s - i'm getting crazy, i tried to solve this but i cannot handle this..
thank you all..

~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x900"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

thank you...

---

### Post by BillGod on 2010-11-29
anyone with this problem try this

open terminal

#xrandr

check to see what display is listed. 

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected (normal left inverted right x axis y axis)
   1024x600       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  


Mine says "VGA1 connected" and I can see my max listed here is 1360x768
so in my case I would type in the following

#xrandr --output VGA1 --mode 1024x768
if the size you want is not listed.  you can add them with the following

#xrandr --newmode "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

If you dont know what the settings for your monitor are look them up first.

#xrandr --addmode VGA1 1440x900_59.90
#xrandr --output VGA --mode 1440x900_59.90

screen size should changed.  you can the go into system\admin\monitors and click on make default.  this SHOULD keep the settings.

---

### Post by Grenage on 2010-11-30
> **jdsakgj said:**
> That would be correct. The best option for me is to have it on 1024 and 75 hz. Can you point me somwehere about the drivers. What should i look for and where?

The intel drivers come with the system, and I've not personally seen a case where the drivers needed to be obtained automatically.  You said that you used the previous xorg; since that was for 1280x1024, try something like this:

```
Section "Monitor"
    Identifier "HP71"
    VendorName "HP"
    ModelName "D8901A"
    HorizSync 30 - 70
    VertRefresh 50 - 120
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82801DB"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection
EndSection
```

You may not actually need a *modeline*, so feel free to comment it out; you can always uncomment it later.

---

### Post by Grenage on 2010-11-30
> **funky_D said:**
> hi all,
well.. i have the same problem.. low resolution, the screen is asus 22" (16:9), the image is blurred.. awful.. :s - i'm getting crazy, i tried to solve this but i cannot handle this..
thank you all..

Is 1152x864 definitely the right resolution for your monitor?

---

### Post by jdsakgj on 2010-12-03
Thanks for the help. 
I think you're right about the drivers. When i remove xorg.conf video playback works. If i add it videos doesn't work. Any idea what to do? 
Oh, one more thing. If i have xorg.conf, command xgamma -gamma works, if i remove xorg.conf it doesn't.

> **Grenage said:**
> The intel drivers come with the system, and I've not personally seen a case where the drivers needed to be obtained automatically.  You said that you used the previous xorg; since that was for 1280x1024, try something like this:

```
Section "Monitor"
    Identifier "HP71"
    VendorName "HP"
    ModelName "D8901A"
    HorizSync 30 - 70
    VertRefresh 50 - 120
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82801DB"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection
EndSection
```You may not actually need a *modeline*, so feel free to comment it out; you can always uncomment it later.

---

### Post by Grenage on 2010-12-03
> **jdsakgj said:**
> Thanks for the help. 
I think you're right about the drivers. When i remove xorg.conf video playback works. If i add it videos doesn't work. Any idea what to do? 
Oh, one more thing. If i have xorg.conf, command xgamma -gamma works, if i remove xorg.conf it doesn't.

Did you try adding the resolutions with xrandr, as per BillGod's information?  You might be able to have your cake and eat it. :)

---

### Post by funky_D on 2010-12-04
> **Grenage said:**
> Is 1152x864 definitely the right resolution for your monitor?

hi!
nooo, the letters are huge! i'm getting errors:

:$ xrandr

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       50.0* 
   1024x768       51.0  
   800x600        52.0     53.0     54.0  
   680x384        55.0     56.0  
   640x480        57.0  
   512x384        58.0  
   400x300        59.0  
   320x240        60.0  
~$ xrandr --addmode default 1440x900_59.90
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1440x900_59.90"
 
:(

---

### Post by jdsakgj on 2010-12-04
> **Grenage said:**
> Did you try adding the resolutions with xrandr, as per BillGod's information? You might be able to have your cake and eat it. 

I really hope, one day, as soon as possible! :) I will happily share this cake with all who are helping me out. Thanks! 

So... I removed xorg.conf and restart. Resolution is automaticaly set on 1280x1024 with really hurting hz. When  i go to system/settings/monitor there is no option to choose another  resolution and the hz is set as 0. I can't change nothing. Videos are playing as i want them to. Gamma command in terminal doesn't work.

#xrandr in terminal doesn't work. With xrandr i got this message...

[COLOR=Silver][I]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0*[/I][/COLOR]

None of the BillGod's commands work. I set Grenage's xorg.conf back, restart, and i have this beautiful 1024x768, 75hz enviroment. As i go to settings to change and play with resolutions and hz a bit i find out that this is really the best one to have. I can also set Gamma with gamma comand in terminal. But, i can't play video files.

With xorg.conf still set, i go to terminal and type xrandr. *It gives me this.*

[COLOR=Silver][I]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       85.0 +   75.1* 
   1280x1024      60.0  
   800x600        85.1     75.0  
   640x480        85.0     75.0     60.0  
   720x400        70.1  [/I][/COLOR]

---

### Post by Grenage on 2010-12-06
> **funky_D said:**
> hi!
nooo, the letters are huge! i'm getting errors:

:$ xrandr

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       50.0* 
   1024x768       51.0  
   800x600        52.0     53.0     54.0  
   680x384        55.0     56.0  
   640x480        57.0  
   512x384        58.0  
   400x300        59.0  
   320x240        60.0  
~$ xrandr --addmode default 1440x900_59.90
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1440x900_59.90"
 
:(

Modify your existing xorg.conf, substituting the old resolution for the desired resolution:

```
Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
Option "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"

# HorizSync source: builtin, VertRefresh source: builtin
Identifier "Monitor0"
VendorName "Unknown"
ModelName "CRT-1"
HorizSync 28.0 - 55.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 9400 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x900"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "metamodes" "**1400x900**_60 +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection
```

---

### Post by Grenage on 2010-12-06
> **jdsakgj said:**
> I really hope, one day, as soon as possible! :) I will happily share this cake with all who are helping me out. Thanks! 

So... I removed xorg.conf and restart. Resolution is automaticaly set on 1280x1024 with really hurting hz. When  i go to system/settings/monitor there is no option to choose another  resolution and the hz is set as 0. I can't change nothing. Videos are playing as i want them to. Gamma command in terminal doesn't work.

#xrandr in terminal doesn't work. With xrandr i got this message...

[COLOR=Silver][I]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0*[/I][/COLOR]

None of the BillGod's commands work. I set Grenage's xorg.conf back, restart, and i have this beautiful 1024x768, 75hz enviroment. As i go to settings to change and play with resolutions and hz a bit i find out that this is really the best one to have. I can also set Gamma with gamma comand in terminal. But, i can't play video files.

With xorg.conf still set, i go to terminal and type xrandr. *It gives me this.*

[COLOR=Silver][I]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       85.0 +   75.1* 
   1280x1024      60.0  
   800x600        85.1     75.0  
   640x480        85.0     75.0     60.0  
   720x400        70.1  [/I][/COLOR]

Let's work on the videos issue directly; what happens when you attempt to play a video file?  What program are you using, and does an alternative work (such as VLC) work?

---

### Post by funky_D on 2010-12-09
> **Grenage said:**
> Is 1152x864 definitely the right resolution for your monitor?

hello all,
i was not getting the monitor to work well according to the resolution, when i configured a resolution of 1440x900 the nonitor would not change definition but instead it would change to a bigger area, the result was i had to pan left or right with the mouse on the corner of the screen...

guys i had to downgrade to 10.04.1LTS - i mean a fresh reinstallation... very annoying! now with 10.04.1 i and also with nvidia drivers i have 1680x1050! all is ok now! but not with 10.10...

thank you all,
Dino

---

### Post by jdsakgj on 2010-12-10
> **Grenage said:**
> Let's work on the videos issue directly; what happens when you attempt to play a video file?  What program are you using, and does an alternative work (such as VLC) work?

I have tried with different programs, including VLC in which i only get black screen, the sound works though. In sound and video player which comes with ubuntu i open the file and it opens it, but as soon as the program starts it also shuts down.

---

### Post by sr14 on 2010-12-10
@Skategirl is your graphic card installed ?

---

### Post by L Campbell on 2010-12-12
> **skatergirl said:**
> I got the unknown moniter problem. I searched around a little on the site, but i still dont understand what to do. Yeah i know its probably been posted a million times.

Im a noob...

I need to change resolution and change hz? (is that what its called?)

The screen makes my eyes hurt =(

I'm sorry that this doesn't help you but I have the same problem, too.

---

### Post by alil2cul4u on 2010-12-12
Hey Grenage,

sorry it took so long to reply.. But i am not sure what you mean I am a complete noob to Ubuntu and Linux. Im coming over from Windows. My tower is a Compaq SR1550NX and it has the original mobo all i have changed is the adding the wireless card and that is a Netgear WN311B. I did a clean install today to 10.10 and forgot how I got my screen to stop freezing up. So if you can, please walk me through how to stop it!

---

### Post by Grenage on 2010-12-13
> **sr14 said:**
> @Skategirl is your graphic card installed ?
> **L Campbell said:**
> I'm sorry that this doesn't help you but I have the same problem, too.

That user's problem was resolved.

> **alil2cul4u said:**
> sorry it took so long to reply.. But i am not sure what you mean I am a complete noob to Ubuntu and Linux. Im coming over from Windows. My tower is a Compaq SR1550NX and it has the original mobo all i have changed is the adding the wireless card and that is a Netgear WN311B. I did a clean install today to 10.10 and forgot how I got my screen to stop freezing up. So if you can, please walk me through how to stop it!

How is the screen 'freezing'?  Is in permanent and unusable, and when does it occur? It might be worth posting it as a new thread - this one is becoming rather long.

---

### Post by schm on 2010-12-13
Good morning, everyone,
I have a similar problem with the monitor of my laptop (Amilo pro V2055,  Graphics: S3 Unichrome Pro). After installing Ubuntu 10.04 the resolution is set to "1600 x 1200" and it sais "Monitor: unknown". When I manually change the resolution to 1280 x 800 (as it should be), my screen is blurred and - after a while - switches back to 1600x1200. But under this resolution, part of the screen is invisible to me (the right hand side and the bottom). 
I have tried to follow the advice I could find - but there is not a file "xorg.conf" on the system! That is why I could not activate the VESA driver, either. Nor could I use the "Newmode" - method. I tried xrandr - I found no solution!
You can see I am green in Ubuntu, but it is a wonderful system and I would appriciate any help very much,
thanks 
schm

---

### Post by alil2cul4u on 2010-12-23
It usually happens when I minimize something. It will completely freeze, everything except the mouse. I have to shut down the computer completely. It doesnt happen as much when I have my refresh rate set at 75mhz but according to the specs from the manufactures site the max refresh rate is 85mhz?

---

### Post by Grenage on 2010-12-24
> **schm said:**
> I have tried to follow the advice I could find - but there is not a file "xorg.conf" on the system! That is why I could not activate the VESA driver, either. Nor could I use the "Newmode" - method.

You can create an xorg.conf - X will use one if present.

> **alil2cul4u said:**
> It usually happens when I minimize something. It will completely freeze, everything except the mouse. I have to shut down the computer completely. It doesnt happen as much when I have my refresh rate set at 75mhz but according to the specs from the manufactures site the max refresh rate is 85mhz?

Normally I'd suspect RAM, but as this has only occurred since the reinstall, I will assume drivers.  I have no S3 experience, and this thread is getting quite long, so it's probably worth reposting your issue as a new thread.  It will get more traffic!

---

