---
title: "Dual-Monitor Flickers"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by horgabob on 2009-04-14
I just finished setting up my system using a TV as my second monitor. My idea was to use it to watch videos while I use the other monitor for other applications. 

For some reason, whenever I play a video the video flickers constantly. I've done some searching/googleing, and I can't seem to figure out how to fix it. I saw something about a xorg file or something, but not sure what to do.

Also note that I have used dual monitors on this system before, about 3 years ago with Windows. This is my first attempt at ubuntu.

Please help! (let me know if you need further info/how to get it)

---

### Post by horgabob on 2009-04-14
bump....please help!

---

### Post by horgabob on 2009-04-14
anyone?

---

### Post by overdrank on 2009-04-14
Hi and I see in your other thread that you are having issue with a black screen now. Could you tell us the model of the graphics card and version of Ubuntu you are using?
If you are not able to reach the desktop you may try and boot into recovery mode and use the xfix option to correct the graphical issues. When xfix it complete you should be given the option to boot normally.

---

### Post by horgabob on 2009-04-14
OK, I tried running Xfix and it says "xserver-xorg postinst warning: overwriting possibly-customised configuration file"

I'm running ubuntu 8.10, and to be honest I bought the vid card 3 years ago and I'm unsure what the model is.

Earlier I ran recovery mode to what looked like an older version, and it worked, but my second monitor just cloned the first, and I couldn't open CCC to reconfigure it.

I feel like i messed up bigtime here lol...any ideas? Should I just reinstall ubuntu and start over?

---

### Post by horgabob on 2009-04-14
ok, right now i'm running under what seems to be a recovered mode from earlier. Again, the second monitor is simply a clone, and Catalyst Control Center won't load, still says I don't have the drivers installed.

So I went through EnvyNG again, and it downloads them all and says I have them already...I'm gonna try to go through and reinstall all of them and see what happens.

---

### Post by horgabob on 2009-04-14
No luck CCC still won't load...

---

### Post by horgabob on 2009-04-15
ok so when i go into System >Administration> Hardware Drivers I can activate the different driver. Then dual monitors works. However this i when i get the black screen error mentioned in my other post. 

When I do the fix on boot, it works, but it goes back to cloned monitors instead of one big extended one. Any ideas?

---

### Post by Cybie257 on 2009-04-15
You need to figure out what card you have in your system. Open up your box and look at the card. Many times you will find the model number on the card itself. I'm assuming it's a dual-head card. 

Is there 2 VGA ports, 1-VGA and 1-DVI, or 2-DVI ports?

What was the description on the driver you enabled via Hardware?

What version of Ubuntu are you running? 32-bit? 64-bit?

I have an ATI card that has done that in the past and during the different stages of updates. Ubuntu Jaunty 64-bit... Updates have seemed to fix that problem. Also, note that TV's are a bit different than monitors. I have issues when trying to run my TV as a monitor with ANY OS... So, is this flickering just on the TV side, or do you also get the flicker with the regular monitor?

In order to help you out with your situation, you're going to have to provide more information. Also, make sure you apply all the latest updates and even try installing VLC Media Player (if not already done). You can do that via the Synaptics Package Manager. That has also proven to help me in the past when the default Movie Player 'Totem' would flicker while playing vids.

-Cybie

EDIT: This information will also help with your other issue to be answered also, not just the flickering.

---

### Post by horgabob on 2009-04-15
It has 1-VGA and 1-DVI, and the card says, it's an ATI, and i can't seem to find the model number, though on a bar code it has "UPC X1300PC1256" and "757448003642". Note: I just ran lspci in terminal and it seems to be telling me that it is a Radeon X1300/X1550 Series


I'm 99% sure I'm running 32 bit Ubuntu though I'm not sure how to verify that.

I got the flicker on both monitors, just just the TV. Also, this system worked with dual monitors a few years ago (not a TV though) on windows.

I do have VLC installed as well.

The driver that I activate through the hardware drivers section is called "ATI/AMD proprietary FGLRX graphics driver. It says "This driver is required to fully utilise the 3D potential of some ATI graphics cards". And it seems that activating it is the only way to get the dual monitor (or CCC for that matter) to work, but I keep getting that black screen.

Edit: if it provides any extra info, none of the Compiz fuctionalities are working either (cube, wobbly windows, etc) maybe that has something to do with the video card as well?

---

### Post by Sylslay on 2009-04-15
meaby try command line;

gnome-display-properties

more pations, some peaple from forum did setup dual-head card , for sure.
PS. If You use GNOME.

---

### Post by Cybie257 on 2009-04-15
> **horgabob said:**
> It has 1-VGA and 1-DVI, and the card says, it's an ATI, and i can't seem to find the model number, though on a bar code it has "UPC X1300PC1256" and "757448003642". Note: I just ran lspci in terminal and it seems to be telling me that it is a Radeon X1300/X1550 Series

Yes, X1300. I have an X1600 and always had some sort of issues with dual monitors. That is, until I ran 64-Bit Jaunty (9.04). 100% awesomely easy to do and switching a monitor on or off, moving it around (IE: top, left, bottom of other), extremely simple. Works as good (if not better) than in Windows.

SUGGESTION: You might want to try to download Jaunty (either 23 or 64 bit) and try it on the live CD. You might be amazed. Then again, are you already? Still not sure on the version of the OS you are running. 


> 
I'm 99% sure I'm running 32 bit Ubuntu though I'm not sure how to verify that.


DO THIS: uname -a

Post the output. :)

> 
I got the flicker on both monitors, just just the TV. Also, this system worked with dual monitors a few years ago (not a TV though) on windows.


Just realize that these cards were designed and drivers programmed for Windows. So, yeah, I'm sure it worked just fine.

> 
I do have VLC installed as well.


I assume the flicker occurs with this also, so leaving it alone.


> The driver that I activate through the hardware drivers section is called "ATI/AMD proprietary FGLRX graphics driver. It says "This driver is required to fully utilise the 3D potential of some ATI graphics cards". And it seems that activating it is the only way to get the dual monitor (or CCC for that matter) to work, but I keep getting that black screen.

Never had much luck (though it did work) with getting the proprietary drivers to function so well. ATI is working on getting things better for Linux, but still some work to do. 

Again, not sure about 32 bit, but the 64 Bit Jaunty default drivers work great. :) I'm not even sure if ATI has 64 Bit proprietary drivers yet. Haven't checked. LoL

> Edit: if it provides any extra info, none of the Compiz fuctionalities are working either (cube, wobbly windows, etc) maybe that has something to do with the video card as well?

Does it just not let you enable them? I never played around with Compiz much, but with 8.10, I had to tweak things to get it to work. With the little bit of playing around, Jaunty again, was very easy. 


:idea:   :idea:   :idea:

AH HA! That just reminded me of something. See this thread below. I had this same exact problem. Turn off desktop effects altogether. That fixed a flicker problem I had with 8.10 and my ATI x1600 Dual-Head. :) Report back and let's see if that fixes it. 

[http://ubuntuforums.org/showthread.php?t=1109579&highlight=video+flicker+x1300+ati](http://ubuntuforums.org/showthread.php?t=1109579&highlight=video+flicker+x1300+ati)


-Cybie

---

### Post by horgabob on 2009-04-15
That didn't seem to help much, and now, even if i unplug my second monitor the video skips, when before it didn't do this.

UGH this is frustrating.

---

### Post by horgabob on 2009-04-15
OK, here's the output for that command
2.6.27-11 generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 1686 GNU/Liunx

I just completely uninstalled Compiz, so I'm gonna reboot and see if that helps, although the monitors are still clones at the moment. 

I'm gonna try all these out and I'll post the results, if nothing works, I'll probably try Jaunty and see what happens.

Thanks so much for all your help so far!

---

### Post by horgabob on 2009-04-15
So, after uninstalling Compiz, I activated the proprietary driver, and it seems to be working!!! They're set up as one big desktop instead of clones, and there's no skipping or flickering!!

Thank you SO much! Kind of annoying that after all that Compiz was the issue lol. I guess no wobbly windows or cube for me =(

---

### Post by Cybie257 on 2009-04-15
> **horgabob said:**
> So, after uninstalling Compiz, I activated the proprietary driver, and it seems to be working!!! They're set up as one big desktop instead of clones, and there's no skipping or flickering!!

Thank you SO much! Kind of annoying that after all that Compiz was the issue lol. I guess no wobbly windows or cube for me =(
=D> Glad I could help. 

Actually, you could still have them. Just disable Desktop Effects when your going to watch video. Other than that, everything else seemed to function ok on my system. 

Preferences -> Appearance -> Visual Effects (TAB) -> Select None

-Cybie

---

