---
title: "No graphics (Out of scan range) -- console login OK"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by wco on 2009-01-01
I just installed xubuntu 8.10 on an older system (using alternate install cd -- could not get regular graphical installation to work).  Install seems to have completed successfully, but cannot get video to work in graphics mode--after boot up, monitor shows "Out of scan range."  After hitting CTRL-ALT-F1, I am able to login using console.

I ran sudo dpkg-reconfigure xserver-xorg but only got questions about keyboard-no monitor or video questions.  xorg.conf file is barebones (can post if required).

Search of the forums and google does not reveal anything specific.  I tried manually changing xorg.conf file based on other postings without success.

System specs:
Athlon 800Ghz
256Mb RAM
ATI Rage 128 32Mb video card
Monitor: Sony CPD 220VS

I can post xorg log if helpful.  It seems I am using the "r128" driver.  I am willing to troubleshoot myself but need some guidance on how to proceed.

---

### Post by mgranet on 2009-01-02
Yes, please post the xorg.

---

### Post by wco on 2009-01-02
Ok - can't attach or copy and paste the entire log file, since the computer is not connected to network as of yet.  Here are the highlights (retyped) including all WWs and EEs:

....

(II) Module r128: vendor="X.Org Foundation"

....

(II) Loading /usr/lib/xorg/modules//libint10.so
....
(II) R128(0): initializing int10
(EE) R128(0): No V_BIOS found
....
(WW) R128(0): Video BIOS not found!
....
(WW) R128(0): Can't determine panel dimensions, and none specified.  Disabling programming of FP registers.
(WW) R128(0): Video BIOS not detected, using default PLL parameters!
....
(II) Reloading /usr/lib/xorg/modules//libint10.so
....
(EE) R128(0): No V_BIOS found
....
(WW) R128(0): Unable to estimate virtual size


If there are other sections of interest in the log file, I can type them also.

---

### Post by mgranet on 2009-01-02
Well, I was thinking it might be something simple, like a xorg.conf problem. But I've never seen the Video Bios not found problem. All I can suggest is to make sure you have defined resolution and refresh rates in your xorg.conf file. I hate to make you type it all out manually, but posting your xorg.conf file will be helpful.

---

### Post by wco on 2009-01-02
My xorg.conf file is essentially empty -- it is all set for autodetection at boot time (this is apparently how newer versions of Ubuntu work).  I attempted to make changes using dpkg-reconfigure, but that doesn't address video options at all.

Here's my xorg.conf file (nothing really in it):

Section "Device"
 Identifier "Configured Video Device"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection


That's it.


I also tried Xorg -configure which created a more specific xorg.conf file.  Using this file made no difference.

I also tried manually adding HorizSync 30-70 and VertRefresh 50-120 (following my monitor's manual specs) to the Monitor Section with no change

I also tried using gtf 1024 768 60 to create a Modeline.  The result was 

Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 772 795 -HSync + VSync

which I added to the Monitor Section, and then added a Display Subsection to Screen with 

Modes "1024x768_60.00"

None of those changes made a difference.

I suspect the can't find V_BIOS might be part of the problem.  I do see occasional postings about a "black screen" with ATI Rage cards (essentially what I get) but no clear answer.  The steps sometimes mentioned are the ones I outlined above.  

How can I tell (from the ctrl-alt-f1 virtual terminal) exactly what resolution and refresh rates are been sent to my monitor?  I can only assume that the monitor is receiving a rate that it cannot process.

---

### Post by mgranet on 2009-01-02
Just to make sure, you have the xserver-xorg-video-r128 package installed?

---

### Post by stderr on 2009-01-02
> **mgranet said:**
> Just to make sure, you have the xserver-xorg-video-r128 package installed?

Might be worth purging and reinstalling it too.

```
sudo apt-get purge xserver-xorg-video-r128
sudo apt-get install xserver-xorg-video-r128
```

The output of 

```
glxinfo
```

may help us.

Also, have you tried booting the recovery kernel and running x-fix?

---

### Post by wco on 2009-01-02
Yes, dpkg -l | grep r128 shows:

ii xserver-xorg-video-r128   6.8.0-1ubuntu2    X.Org X server - ATI r128 display driver

---

### Post by mgranet on 2009-01-02
> **stderr said:**
> Might be worth purging and reinstalling it too.

```
sudo apt-get purge xserver-xorg-video-r128
sudo apt-get install xserver-xorg-video-r128
```

The output of 

```
glxinfo
```

may help us.

Agreed on the purge. It may re-write the xorg correctly.

Also post the relevant lines of ```
lspci
```

---

### Post by wco on 2009-01-02
Keep in mind that I have no internet connection.  If I purge the package, will I be able to get it back (is it stored locally?)

I tried glxinfo, but unfortunately I got the following message:

The program 'glxinfo' is currently not installed.  You can install it by typing: sudo apt-get install mesa-utils.

I tried that and I got the following:

Package mesa-utils is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.


Sounds like I can't easily install packages without internet connection (of course I wanted to get my graphical output first, then use some of the GUI tools before I proceeded to work on configuring my wireless card).

---

### Post by wco on 2009-01-02
I did try x-fix from the menu in the install disk.  The output was the same as when I ran sudo dpkg-reconfigure -phigh xserver-xorg

I am awaiting some confirmation that the purge is reversible without internet or network connection.

As for lspci, here is the line:

01:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

---

### Post by mgranet on 2009-01-02
Ahh. Then, no, don't purge the driver; unless you know how to get a deb off the install disk.

---

### Post by wco on 2009-01-02
I just checked the card physical and it is well seated and is a Rage 128 ATI

---

### Post by mgranet on 2009-01-02
I'm fresh out of ideas. Poking around Google, it seems this card has been problematic. You might even consider getting a different card.

---

### Post by wco on 2009-01-02
I understand.  A bit hard to justify getting a new card for an older system (and hard to find one that will be compatible with the older AGP 1x motherboard).  This card I actually found 2 years ago at a church sale for $5, which replaced an older 3dfx one that blew.  Well, I did get my money's worth out of it--maybe it's time to trash the whole system....that's what the wife's about to do if I spend too much more time on it...:D I was hoping to squeeze a few more years of life out of it with Ubuntu after W98 finally was corrupted beyond help.

---

### Post by mgranet on 2009-01-02
> **wco said:**
> I understand.  A bit hard to justify getting a new card for an older system (and hard to find one that will be compatible with the older AGP 1x motherboard).  This card I actually found 2 years ago at a church sale for $5, which replaced an older 3dfx one that blew.  Well, I did get my money's worth out of it--maybe it's time to trash the whole system....that's what the wife's about to do if I spend too much more time on it...:D I was hoping to squeeze a few more years of life out of it with Ubuntu after W98 finally was corrupted beyond help.

You can get a new AGP card (Nvidia FX 5200) from newegg for $25USD. It's not a terrible amount to soak into an old computer...

---

### Post by abn91c on 2009-01-02
if you have a wired network type[COLOR="Blue"]** dhclient eth0**[/COLOR] to connect at the prompt
I have that card on my dell gx240, if you installed the restricted drivers, that is your problem i did that to try to get compiz working ended up having to reinstall.

---

### Post by wco on 2009-01-02
> **mgranet said:**
> You can get a new AGP card (Nvidia FX 5200) from newegg for $25USD. It's not a terrible amount to soak into an old computer...
I just realized after talking about a new card --- this is not an AGP card but an older PCI card (I was confusing the card with another one of my systems) -- I wonder whether that is part of the problem...I saw somewhere there is an "AGPMode" parameter within xorg for this driver ... I will try to research...

---

### Post by mgranet on 2009-01-02
There's hope yet. It probably can't find the video BIOS if it's looking on the wrong bus.

---

### Post by wco on 2009-01-02
> **abn91c said:**
> if you have a wired network type[COLOR="Blue"]** dhclient eth0**[/COLOR] to connect at the prompt
I have that card on my dell gx240, if you installed the restricted drivers, that is your problem i did that to try to get compiz working ended up having to reinstall.
Sorry but I don't understand what you asking me to do about the network.  Are you saying that the driver that came with the xubuntu install disk is restricted and that I need to reinstall from the internet source?

---

### Post by abn91c on 2009-01-02
> **wco said:**
> Sorry but I don't understand what you asking me to do about the network.  Are you saying that the driver that came with the xubuntu install disk is restricted and that I need to reinstall from the internet source?
no **dhclient eth0** will **enable** your network connection if you are using a wired setup to your router/modem. that way you can install files from the internet.
if you installed the xubuntu restricted drivers repositories and ran an update that's what "killed" your video. What I had to do was reinstall the OS

---

### Post by wco on 2009-01-02
I made an incorrect statement before (I needed to get some sleep, really) -- the card is AGP.  Part of my confusion was that the motherboard has older AGP 1x/2x slot without the extra card retaining mechanism that I am used to seeing in the AGP 4x slots, but it is AGP for sure.

I tried all AGPMOdes in the xorg.conf with no success

---

### Post by wco on 2009-01-02
Ok, I cannibalized another AGP card (ATI Radeon 9000 PRO) from another system and put it in---boots great with graphics, so we confirm that the card is causing the problem.

Now I will setup internet connection and try one more time to purge and reload the r128 driver package and see if I get this card to work.

---

