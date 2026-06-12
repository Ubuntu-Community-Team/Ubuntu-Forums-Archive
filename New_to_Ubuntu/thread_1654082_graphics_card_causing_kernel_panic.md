---
title: "graphics card causing kernel panic?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-12-27
This is my first time ever to have a graphics card, I've been limping along on onboard graphics for what seems like eternity. 

I'm running Karmic on an older Sony Vaio desktop (dell monitor). I got an nvidia FX 5500 256 mgb card. I installed it today, first using envyng to choose the drivers. I didn't notice much difference in performance as far as watching streaming vids on crunchyroll, so I tried the hardware drivers. Nowhere in the process would it even enable 'normal' desktop effects - and there really wasn't a whole lot of difference in graphics though there was some improvement.  The recommended hardware driver skewed the resolution though, so I tried the other one and it did fix the resolution difficulty however, when I shutdown, then restarted awhile later - I got a kernel panic - not syncing.  I couldn't even get it to start puppy linux on cd until I ran a ram check, it finally did boot it. In the end, I wound up pulling the card. Now I am not sure if I have bios set properly but at least I got to the point where Karmic has booted by choosing to run in low graphics mode for one session. 

Right now when I check the video in the terminal I get -

```
lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```and
```
sudo lshw -c video
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:c0000000-c7ffffff(prefetchable) memory:cfee0000-cfefffff ioport:bc00(size=128)

```Is it possible to get this video card to work at all without causing kernel panics? ( and me to panic, too for that matter!) The desktop effects are not as important to me as just getting a better quality video. Any help at all that I can get would be great, I'm the first to admit I'm functioning in ignorance here.

edited to add - The first hardware driver (administration/hardware drivers) I chose showed the proper resolution in the drop down but the toolbar across the top was not visible) 

I have not removed the the nvidia drivers at present.

thanks in advance,

mystmaiden

---

### Post by mystmaiden on 2011-01-01
I wound up having to pull the card when xorg crashed completely. In my search to figure out how to get it the machine to recognize the onboard graphics again I discovered the difficulty was the fact that the new Nvidia drivers aren't compatible with Virtualbox. I think the kernel panic had to be operator error because it hasn't repeated even though I've had multiple other problems.

I've found two workarounds. One is to download and install the virtualbox for any host and the other is to use the archived drivers from Nvidia.  Which would be better or should I try both? Also the archived drivers I found are .run files - will they work with Ubuntu?

mystmaiden

---

### Post by HermanAB on 2011-01-01
Howdy,

Nvidia is the Microsoft of video processing.  Their driver software is dreadful and bug ridden.

You should try the latest version from Nvidia, or if all else fails, use the universal VESA driver (the one used during installation of Linux).

---

### Post by sandyd on 2011-01-01
> **mystmaiden said:**
> This is my first time ever to have a graphics card, I've been limping along on onboard graphics for what seems like eternity. 

I'm running Karmic on an older Sony Vaio desktop (dell monitor). I got an nvidia FX 5500 256 mgb card. I installed it today, first using envyng to choose the drivers. I didn't notice much difference in performance as far as watching streaming vids on crunchyroll, so I tried the hardware drivers. Nowhere in the process would it even enable 'normal' desktop effects - and there really wasn't a whole lot of difference in graphics though there was some improvement.  The recommended hardware driver skewed the resolution though, so I tried the other one and it did fix the resolution difficulty however, when I shutdown, then restarted awhile later - I got a kernel panic - not syncing.  I couldn't even get it to start puppy linux on cd until I ran a ram check, it finally did boot it. In the end, I wound up pulling the card. Now I am not sure if I have bios set properly but at least I got to the point where Karmic has booted by choosing to run in low graphics mode for one session. 

Right now when I check the video in the terminal I get -

```
lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```and
```
sudo lshw -c video
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:c0000000-c7ffffff(prefetchable) memory:cfee0000-cfefffff ioport:bc00(size=128)

```Is it possible to get this video card to work at all without causing kernel panics? ( and me to panic, too for that matter!) The desktop effects are not as important to me as just getting a better quality video. Any help at all that I can get would be great, I'm the first to admit I'm functioning in ignorance here.
[B]Plug the Nvidia FX5500 card back in before you do the bottom steps.

To boot at least without a kernel panic, Press Shift/ESC when booting up.
Choose recovery mode.
Run
```

sudo rm /etc/X11/xorg.conf
sudo apt-get remove nvidia -*
```
[/B]
edited to add - The first hardware driver (administration/hardware drivers) I chose showed the proper resolution in the drop down but the toolbar across the top was not visible) 
[B]Just use these.
Adjust the monitor (horizontal/vertical) positions and size until you can see the toolbar.
Im pretty sure it should work since my mom's computer uses the same card.
[/B] 
I have not removed the the nvidia drivers at present.

thanks in advance,

mystmaiden
.

---

### Post by mystmaiden on 2011-01-01
HermanAB wrote:

> Nvidia is the Microsoft of video processing. Their driver software is dreadful and bug ridden.
You should try the latest version from Nvidia, or if all else fails, use the universal VESA driver (the one used during installation of Linux).Unfortunately, the latest drivers from Nvidia are the ones that caused the difficulty when used with virtualbox onboard and reading what synaptic had to say about Vesa wasn't very encouraging - if the older nvidia drivers won't work I may have to resort to vesa though.


sandyd wrote: 
> To boot at least without a kernel panic, Press Shift/ESC when booting up.
Choose recovery mode.
Run```
sudo rm /etc/X11/xorg.conf
sudo apt-get remove nvidia -*
```Thanks so much for the reply. 
I actually didn't see your post until just now but I used a command I found somewhere else on the forums

```
sudo apt-get purge nvidia-* 
```Unfortunately, it also removed my desktop though so after purging Nvidia, I reinstalled the desktop. The machine I had in Virtualbox was inaccessible and nothing I did fixed it, so I uninstalled vbox and will upgrade and reinstall shortly. I'll post the results here in case anyone else should stumble upon this issue. 

I'm not at all sure how to adjust horizontal and vertical that via xorg.config. Honestly, not having a xorg.config file in Karmic is a little confusing to me still. Setting the monitor refresh to 85 worked but I did not get to the point of editing xorg to make it persistent and I wasn't sure if that was the right refresh rate for this monitor.

So that I could make a note of the resolution settings for when I try all this again, I just now ran -

```
sudo Xorg -configure 
```This is what it returned - 


```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```So I don't even know how to generate a config file for reference...


The good news is - currently, I have a desktop, and don't have kernel panics, blinking and vbox warnings upon restart. In other words, I'm right back where I started!

---

### Post by sandyd on 2011-01-01
> **mystmaiden said:**
> HermanAB wrote:

Unfortunately, the latest drivers from Nvidia are the ones that caused the difficulty when used with virtualbox onboard and reading what synaptic had to say about Vesa wasn't very encouraging - if the older nvidia drivers won't work I may have to resort to vesa though.


sandyd wrote: 
```
sudo rm /etc/X11/xorg.conf
sudo apt-get remove nvidia -*
```Thanks so much for the reply. 
I actually didn't see your post until just now but I used a command I found somewhere else on the forums

```
sudo apt-get purge nvidia-* 
```Unfortunately, it also removed my desktop though so after purging Nvidia, I reinstalled the desktop. The machine I had in Virtualbox was inaccessible and nothing I did fixed it, so I uninstalled vbox and will upgrade and reinstall shortly. I'll post the results here in case anyone else should stumble upon this issue. 

I'm not at all sure how to adjust horizontal and vertical that via xorg.config. Honestly, not having a xorg.config file in Karmic is a little confusing to me still. Setting the monitor refresh to 85 worked but I did not get to the point of editing xorg to make it persistent and I wasn't sure if that was the right refresh rate for this monitor.

So that I could make a note of the resolution settings for when I try all this again, I just now ran -

```
sudo Xorg -configure 
```This is what it returned - 


```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```So I don't even know how to generate a config file for reference...


The good news is - currently, I have a desktop, and don't have kernel panics, blinking and vbox warnings upon restart. In other words, I'm right back where I started!
I meant adjust the vertical/horizontal position with the monitor.
your monitor should have onscreen settings that show up after you press a button on it (mine arent buttons, their just touch sensitive, but you get the idea)

---

### Post by mystmaiden on 2011-01-03
Ah, thanks. I wish it were that simple but the monitor physical controls don't seem to work with Ubuntu. None of mine ever have - I'm not at all sure why that is.

mystmaiden

---

