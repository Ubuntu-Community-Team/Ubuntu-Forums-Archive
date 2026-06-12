---
title: "How could I get answers here?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Mariane on 2010-01-23
I have been trying to get my sound to function properly for a few days now, and I have posted here several times about it. But either I get no answer at all or just one and no follow up when I reply it didn't work. 

I am polite, I am willing to run any test I would be told to run, and I can't believe no-one here knows how to sort out my problems. I don't think I deserve a RTFM either, as I have stared at the alsa wiki until I could nearly quote the contents by heart. So why don't people answer me, what am I doing wrong??? 

My basic problem is that I can't get the headphones to work. 

alsamixer says:
alsamixer: function snd_ctl_open failed for default: No such device

alsamixer -c 0
displays the equaliser but the column corresponding to the headphones is set to zero volume and can't be raised. 

Typing "say hi" says it twice through the laptop speakers, as if there was an echo. 

Could someone please help me, even by simply suggesting a way to post about that that would attract people's answers? 

Mariane

---

### Post by zeroseven0183 on 2010-01-23
Have you tried looking in the archives, say [http://ubuntuforums.org/archive/index.php/t-337276.html](http://ubuntuforums.org/archive/index.php/t-337276.html) ? Where the solution says, you add your user to **plugdev** group.

> **Mariane said:**
> Could someone please help me, even by simply suggesting a way to post about that that would attract people's answers? 

I'm not a technical person. I'm still learning my way through these things. But I would suggest that you BUMP your thread every now and then so it would pop in the first page of the thread.

I hope you'll get the solution ASAP.

---

### Post by nitstorm on 2010-01-23
i dont know the answer to your audio question, but it so happens that sometimes people view the question and don't respond, some times questions don't get answered, has happened to me too before, annoying i know, just try bumping the thread every once in a while....

---

### Post by e-Gee on 2010-01-23
Right click on sound icon on upper panel and go to Sound Preferences and on the tab input choose your headphones instead of Internal Audio Analog Stereo

---

### Post by e-Gee on 2010-01-23
Sorry this is for Ubuntu but it has to be similar in Kubuntu

---

### Post by kansasnoob on 2010-01-23
Sorry you're having trouble finding a solution, unfortunately that happens. Sometimes it's hard to find someone that's had the same problem and found a solution.

The only help I can offer is that if this is Karmic (aka: 9.10) Crimsun made some notes here:

[http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

Be sure and look at his link:

[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

You might even try adding a post to that forum thread and see if someone there has an idea.

Sorry I can't be of more help, I just happen to have been lucky regarding audio issues other than the first few months Hardy was out and pulse audio was brand new to us all.

---

### Post by Mariane on 2010-01-23
Thank you all for replying. 

@zeroseven0183
Thank you. I had seen this page before but as I couldn't understand the beginning I had not read it to the end. Now I did and typing 

asoundconf list
said "Names of available sound cards:
Intel"

so typing 
asoundconf set-default-card Intel
got alsamixer to function without the -c 0 parameter. But it didn't get the headphones to function. 

@e-GeeWhen I right click on my speaker icon in kde I get KMix options. KMix mixer window has a tab called "Switches" with options "Headphone", "Caller ID" and "Off-hook". When I tick "Headphone" it doesn't change anything and the option doesn't stick, when I open this window again it is again unticked. 

Mariane

---

### Post by Mariane on 2010-01-23
@kansasnoob
Most of the stuff on your 2 links goes way above my head. I just saw there were problems with Realtek and unfortunately my audio is Realtek. 

Mariane

---

### Post by warfacegod on 2010-01-23
> **zeroseven0183 said:**
> Have you tried looking in the archives, say [http://ubuntuforums.org/archive/index.php/t-337276.html](http://ubuntuforums.org/archive/index.php/t-337276.html) ? Where the solution says, you add your user to **plugdev** group.



I'm not a technical person. I'm still learning my way through these things. But I would suggest that you BUMP your thread every now and then so it would pop in the first page of the thread.

I hope you'll get the solution ASAP.

By every once in a while, read that as about once a day or so not every two or three hours. Doing as thorough a search as possible is always a good idea. If you don't find an answer to your specific issue, some one with a similar one may have found a solution that will work for you anyway.

---

### Post by Mariane on 2010-01-23
Foolowing up on kansasnoob links I found a way to disable pulse audio: 

touch ~/.pulse_a11y_nostart
echo autospawn = no|tee -a ~/.pulse/client.conf
killall pulseaudio

Should I type that, is it dangerous? Maybe it is completely u
nrelated to my problem? 

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009531.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009531.html)

Mariane

---

### Post by warfacegod on 2010-01-23
It doesn't look specifically dangerous but keep in mind that if you stop pulse you'll need to have something else installed first to run your audio card other wise you won't have any sound at all.

---

### Post by Mariane on 2010-01-23
> **warfacegod said:**
> By every once in a while, read that as about once a day or so not every two or three hours.


OK :) 

And this post is not just to bump. Can someone please tell me how I can find out whether I'm using pulse audio or not? Or the Ubuntu version of my system? I got confused with 9.10 upgrade, now grub shows about 15 different Ubuntu options and none of them are numbered so I don't know which I'm using anymore, I just know that it's the second not-failsafe from the top of grub list. 

Mariane

---

### Post by Mariane on 2010-01-23
> **warfacegod said:**
> It doesn't look specifically dangerous but keep in mind that if you stop pulse you'll need to have something else installed first to run your audio card other wise you won't have any sound at all.

Thank you warfacegod. That's what I call dangerous, lol. I don't know what else is available, nor how I could install it unless someone tells me the package name. And BTW if I stop it how can I restart it if the other option turns out not to function? 

Mariane

---

### Post by warfacegod on 2010-01-23
> **Mariane said:**
> Thank you warfacegod. That's what I call dangerous, lol. I don't know what else is available, nor how I could install it unless someone tells me the package name. And BTW if I stop it how can I restart it if the other option turns out not to function? 

Mariane

Simplest way is to reboot. I don't know the command for starting pulse. A nice way to get around the 24 hour bump rule is to post updates on what you've tried or on changing behavior of the problem.

I'm not very familiar with the sound systems of Ubuntu because mine always worked properly. A good thing to do though is post the exact audio card you have.

From your Terminal:

```
sudo lspci
```

Mine looks like this:

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
02:04.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:04.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

Specifically: 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

FYI: To copy and paste inside of the Terminal you need to use: Shift+Ctrl+C or V

---

### Post by Mariane on 2010-01-23
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:07.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0c:07.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0c:07.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0c:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


Another thing: people talk about adding themselves to the group "plugdev" as a way to sort out audio problems. But it also seems to be about mounting devices and I have no problems (currently) for mounting a usb key or something. Would someone please have a link which explains what plugdev is and how to use it? 

Mariane

---

### Post by Roger Allott on 2010-01-23
Check your hardware drivers. (System > Administration > Hardware Drivers)

If you find that you've got a Software Modem activated, deactivate it.

I had hours of frustration trying to get my audio to work in 9.10, including compiling my own version of alsa and very nearly getting rid of pulseaudio, but simply deactivating that hardware driver did the trick for me.

---

### Post by philinux on 2010-01-23
> **Mariane said:**
> I have been trying to get my sound to function properly for a few days now, and I have posted here several times about it. But either I get no answer at all or just one and no follow up when I reply it didn't work. 


Mariane

It would appear you are not alone with this.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574)

[From a search]("http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=7hN&q=ubuntu+karmic+Intel+Corporation+82801H+%28ICH8+Family%29+HD+Audio+Controller&btnG=Search&meta=&aq=f&oq=")

---

### Post by J V on 2010-01-23
Oxymoron much?

---

### Post by Mariane on 2010-01-23
> **Roger Allott said:**
> Check your hardware drivers. (System > Administration > Hardware Drivers)

If you find that you've got a Software Modem activated, deactivate it.

I had hours of frustration trying to get my audio to work in 9.10, including compiling my own version of alsa and very nearly getting rid of pulseaudio, but simply deactivating that hardware driver did the trick for me.

I also compiled alsa with
module-assistant a-i alsa-source

I have system/hardware drivers managers but this tells me I only have NVIDIA accelerated graphics driver and that this is not in use (it is in use in fact but that's not the problem). 

I think you gave me gnome instructions and as you are the second person to do this I'll log into a gnome session and try to sort out the problem from there. Maybe if I solve it under gnome it will also solve it for kde. Who knows?

I'm happy to know I'm not the only one with this problem, though I admit it is a very selfish attitude. But from my point of view it makes it more likely that people will know the fix.

Mariane

---

### Post by Mariane on 2010-01-24
Introduction: the headphones are still not working

I opened a Gnome session and I was surprised to see it saying it was not up-to-date. Updates done in Ubuntu used to update the whole system but not anymore. Now it seems I ll have to open a Gnome session periodically to update it. Do you thing Xfce will also have to be updated individually? 

If you wonder why I keep session types I seldom use, it is for security. It has happened to me that one session type stopped working so I could at least use the others (for example to come here to ask for help). 

After updating Gnome it wanted to be rebooted and - HORROR! - it didn t even reach the login screen. It said : Ubuntu is running in low graphics mode. Your screen graphics could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself. 

I tried Configure, test the current settings, and there I was offered to go back to the previous settings. I clicked on that and the screen went black. I could see part of the display only after going over it with the mouse. Like a foggy window, you can only see through it in the places where you wipped it with your hand. There I was wipping the black off with the mouse pointer (which had become a large X). I powered off manually and after reboot the display was OK. What a relief! 

This problem came from nvidia 173.14.12. When booting if it says it is going to use this module the display is unusable. When it is not using the module the display is OK. It doesn t matter if the module is installed and it doesn t matter if when you are booting you see a screen with the nvidia logo. As long as in hardware drivers it says that the module is not being used it is OK. So if you have the same problem just try to find system/hardware drivers (if you can still see enough of your screen to reach that) disable the module and reboot. 

Now for what I was told to do under Gnome. 

e-Gee, right clicking on the speaker icon gives me access to preferences and there I have volume control preference only. 
Select device: I have HDA Intel (Alsa mixer)

Below I have:
Master
PCM
Front
Front Mic
Front Mic Boost
Surround
Center
LFE
Side
Line-in
CD
Microphone
Mic Boost
PC Speaker
Capture
Capture 1

I thought Line-in could be it but it wasn t. Selecting Line-in made no difference. So I put it back to Master like it was before. 

Roger Allott
System > Administration > Hardware Drivers
Only has:
NVIDIA accelerated graphics driver (latest cards)
Which is disabled

The *** nvidia has the cheek to say:
This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards. 
If you wish to enable desktop effects, this driver is required. 
If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games. 

A black desktop which has to be wipped with the mouse pointer and comes out completely distorted after that is what they mean by desktop effects. Some effects. 

They should say:
If this driver is enabled, you will not be able to get rid of crappy desktop effects and will not be able to run software that requires 3D acceleration. As far as games are concerned you will not even be able to play freecell. 

Summary: the headphones are still not working

Mariane

---

### Post by warfacegod on 2010-01-24
I use the same driver with an nVidia Geforce Go5200 64 MB card and I've never had a problem with it.

It sounds like your entire desktop environment got treated as though it were a Paint project. I've never heard of a display acting up that way. In fact you just got my vote for strangest issue of the day.

---

### Post by Mariane on 2010-01-24
My guess would be it had to do with refresh. When you move your mouse over an otherwise static screen the display is re-calculated in the area immediately surrounding the mouse pointer. It has to be re-calculated because the mouse pointer has to be drawn and to simplify matters the redrawn area is usually a square. 

So as I was moving my mouse around my display was being re-calculated in a square area surrounding the pointer. This happens all the time but it only becomes noticable if the display is wrong to start with: in this case the display started out completely black so it was extremely noticable. 

Mariane

---

