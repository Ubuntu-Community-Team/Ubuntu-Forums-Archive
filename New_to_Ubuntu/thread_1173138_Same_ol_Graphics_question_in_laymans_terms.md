---
title: "Same ol Graphics question in laymans terms"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by krisarnold on 2009-05-29
Hi all!
Had been daabling in Ubuntu 8.10 since March. Windows finally took a fat load on me and is unrepairable. Used the disk to run ubuntu for about a week before I finally installed. It is great. I feel like I have a new computer. 
I see all the neat effects for desktop and they look better than vista. I liked when I saw the wobbly windows. My problem is I think my laptop is too old to do these. It is a Dell c610. When I go to enable normal or extra, I get the desktop effects cannot be enabled. I tried to enable the driver, but it doesn't show any. I read something about compiz. I installed it, I see all the features, but obviously still cannot enable them. I am guessing that my video card(if I have one) cannot run these. 

I've looked at this subject before, but everywhere I checked was very technical and CLI driven. I am interested to get into the CLI, but not yet. I have a couple different command line protocols at work and they are all different. One at a time. 
Is there anyway to make desktop effects work? I am commited to Ubuntu either way (may consider Kubuntu). I would just like to show my sister that my 7 year old laptop can be better than her new one with vista. 
Any and all help is greatly appreciated, 
Thanks
-Kris

---

### Post by steviefordi on 2009-05-29
Usually, if desktop effects are 'greyed out' and you can't select them, you don't have a grpahics card capable of 3D acceleration. Could be the driver for the card isn't capable, but judging by the age of your laptop, it's the card.

I would install Xbuntu on a machine that old. It uses a more lightweight desktop environment than gnome or KDE. If you were planning on showcasing desktop effects superior to Vista on this machine to your sister, I'm sorry but it ain't going to happen.

Vista is a big resource hungry lug. Put Ubuntu on a machine with a similar spec to one running vista and you will blow the vista machine away. Unless you can seriously upgrade that old laptop, it's not going to show your sister all that 'eye candy'.

Oh, by the way, even without the effects your 7 year old laptop running ubuntu IS better than any Vista machine. I'd be happier doing financial stuff online using it, and you have places you can go with stability problems.

---

### Post by Hospadar on 2009-05-29
Step one is to figure out what video hardware you have.  Fastest way to do that is for you to open up a terminal (Applications->Accesories->Terminal) and type in (sans-quotes) "lspci" and post the output of that command here.

It is possible that you have a capable machine and your hardware just isn't getting detected correctly, but maybe not.

Also, since it sounds like you have a fresh install, I would suggest trying out the latest version (9.04) and seeing if that just works out of the box (and even if it doesn't, if you're not too attached to your current installation, it might be a good time to upgrade)

---

### Post by krisarnold on 2009-05-29
Thanks fellas,
I do admit my machine is old. But to its credit, the half gig of RAM and 20 gig Hard drive are doing great. Ubuntu runs very fast on it. Hence why I never did the smaller one. I have no real problem with going to version 9, but I did hear from a local Linux guru, that it still had quite a few problems, and may have even more problems considering the age of my machine. 

I'm in full learning mode and willing to play with a little. Except for CLI. Very strange compared to other cli's and will slowly work torwards that. 

Will use terminal as described in above thread and post results.

---

### Post by krisarnold on 2009-05-29
Here is the results of typing lspci into the CLI:

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0d:00.0 Network controller: RaLink RT2600 802.11 MIMO

ATI Video?

---

### Post by Gen2ly on 2009-05-29
This is an older post but relates directly to your video card and could still be a problem.  I'd try this-first:

[http://ubuntuforums.org/showthread.php?p=4125128](http://ubuntuforums.org/showthread.php?p=4125128)

---

### Post by krisarnold on 2009-05-29
I followed the above advice. After going to several different links, it seems like the fixed it. Only problem is that their lingo is not native to me and I have no idea what they are saying. Any help?

---

### Post by overdrank on 2009-05-29
> **krisarnold said:**
> I followed the above advice. After going to several different links, it seems like the fixed it. Only problem is that their lingo is not native to me and I have no idea what they are saying. Any help?

Hi and welcome, I have a similar graphics card in a laptop. I have not used 8.10 with it but Hardy 8.04 and Jaunty 9.04 work well with it. You have no drivers located under system, administration, hardware driver correct?
Edit and can you post the output of this command ```
lspci | grep VGA

``` You can copy and past the command.

---

### Post by krisarnold on 2009-05-29
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
 
That is what it says after said command. You are right, there is nothing under the drivers. I'm assuming edit meant to put that code in the CLI?

---

### Post by overdrank on 2009-05-29
> **krisarnold said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
 
That is what it says after said command. You are right, there is nothing under the drivers. I'm assuming edit meant to put that code in the CLI?

Yes thanks :)
And I am assuming the answer to my first question about the driver is no. 
Ok you may try configuring your xorg with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in the terminal. Then restart x with the ctrl, alt, backspace keys.

---

### Post by krisarnold on 2009-05-29
Yeah I tried that, it did restart my laptop, but I still can't find any drivers, and its the end of the day for me. I may pick up this subject after vacation. Thanks for all who helped

---

### Post by Gen2ly on 2009-05-30
Not a problem.  The post Ireferred to talks about modifying the X server configuration-file.  The X server is responsible for displaying the graphics on Linux.  By editing the Xserver configuration file as suggessted (located at /etc/X11/xorg.conf) and removing the AccelMethod line mentioned has fixed problems in the past, allowing DRI (the Direct Rendering Infrastructure) to work again.  Edit this file, restart, and see ifCompiz now works.

---

### Post by krisarnold on 2009-06-08
So yeah....Vacation is over. Back to the UBUNTU scene. I don't know how to get to the place where I can edit the x server???? So much to learn....

---

### Post by overdrank on 2009-06-08
> **krisarnold said:**
> So yeah....Vacation is over. Back to the UBUNTU scene. I don't know how to get to the place where I can edit the x server???? So much to learn....

You can edit the xorg with this command ```
gksu gedit /etc/X11/xorg.conf
```
Be sure to save a backup copy in case you have to replace it.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by krisarnold on 2009-06-08
Thanks. Here goes......

---

### Post by krisarnold on 2009-06-08
No such luck. Oh well. I guess its not that important.

---

### Post by overdrank on 2009-06-08
> **krisarnold said:**
> No such luck. Oh well. I guess its not that important.

Ok if you would like to keep trying I have a few ideas. How much system memory? 
And can you post you xorg also?

---

### Post by krisarnold on 2009-06-08
I'm bored at work, I'm up for trying a few other things. I've got a half a gig of memory. So it might not be enough to do anything cool. A pentium 3. After putting the command  gksu gedit /etc/X11/xorg.conf,  I get the following


Section "Device"
    Identifier    "ATI Technologies Inc Radeon Mobility M6 LY"
    Driver        "radeon"
    BusID        "PCI:1:0:0"

#Optimized values (changed from driver default)
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "on" #Faster than default (off)
    Option        "SWcursor" "off" #Faster than default (on)
    Option        "EnablePageFlip" "on" #Faster than default (off)
    Option        "DynamicClocks" "on"
    Option        "BIOSHotkeys"   "on"

#These are not mentioned in man page for driver
    Option        "AGPSize" "32" # default: 8
    Option        "EnableDepthMoves" "true"
EndSection

Section "Module"
    Load    "dri"
    Load    "extmod"
    Load    "glx"
    Load    "GLcore"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon Mobility M6 LY"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1400x1050"
    EndSubSectiongksu gedit /etc/X11/xorg.conf
EndSection

---

### Post by overdrank on 2009-06-08
You may try [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")
As that resolution of Modes "1400x1050" may be a little to high.

---

### Post by krisarnold on 2009-06-08
After doing the compiz thing, all pass except for it failed checking hardware software. This is what it said.


Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M6 LY
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

---

### Post by overdrank on 2009-06-08
Ok in your xorg change this ```
Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M6 LY"
Driver "radeon"
BusID "PCI:1:0:0"
```
To this ```
Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M6 LY"
Driver "ati"
BusID "PCI:1:0:0"
```
Then restart x after saving your xorg. You can use the ctrl, alt, backspace keys.

---

### Post by krisarnold on 2009-06-08
I changed it. Saved it. And restarted it. Still says desktop effects could not be enabled. Any other ideas?

---

### Post by krisarnold on 2009-06-08
I also get the exact same thing after running compiz check again...

---

### Post by overdrank on 2009-06-08
> **krisarnold said:**
> I also get the exact same thing after running compiz check again...

Last one for the day :)
You can use the keys ctrl, alt, F1 to reach command line and login.
Then use this command ```
sudo /etc/init.d/gdm stop
```
Then 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When complete ```
sudo /etc/init.d/gdm start
```
Then check your xorg to in sure that is it using the ati driver.

---

### Post by krisarnold on 2009-06-08
Not real fond of those commands. Anyway, after running xorg thing, it doesn't have crap. See what you think....
And thanks for giving me a hand.

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

---

### Post by JellicleHacker on 2009-06-08
I recently crashed the desktop that I'd had for 8 years.
In fact, I'm not even sure what Ubuntu it had...
But, I had the same problem.
Whenever I switched from the normal setting to the fancy one, a little message would come up saying that it had failed (or something like that.)
I just installed Jaunty on my laptop, and when I switched to the fancy effects setting it worked.
Maybe it has something to do with the oldness of your computer?
But, I have to say, even an old computer with an old version of Ubuntu is better than anything with Vista.

---

### Post by krisarnold on 2009-06-08
I would agree with that. My old laptop feels new. I don't need all the visual effects, but it was the first thing that had me look at another OS other than my XP. From there on, Liked it more and more. If I get it good, if not....oh well. Maybe on my next laptop.

---

