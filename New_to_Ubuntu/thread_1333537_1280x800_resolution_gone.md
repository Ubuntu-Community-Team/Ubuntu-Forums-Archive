---
title: "1280x800 resolution gone"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by luadraman on 2009-11-21
Hi, I'm running 9.10 and after since I used an S-Video cable for watching movies from my laptop on to a TV I haven't been able to get 1280x800 mode on the laptop. It's completely disappeared from options in Display Settings. I have an ATI graphics card using the proprierty FGLRX graphics driver. I've tried fixing it by following other threads but I'm not sure what I'm doing to be honest. I don't know what xorg or xrandr is but I've seen them on other posts so here's mine:

pockets@pockets-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 2048 x 768
LCD connected 1280x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x768       60.0*+
   1280x720       60.0 +
   1024x768       60.0 +
   800x600        60.0 +
   720x480        60.0 +
   640x480        60.0 +
   640x432        60.0 +
   640x400        60.0 +
   512x384        60.0 +
   400x300        60.0 +
   320x240        60.0 +
   320x200        60.0 +
CRT1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
COMPONENT_VIDEO disconnected (normal left inverted right x axis y axis)

pockets@pockets-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

pockets@pockets-laptop:~$ sudo lshw -C display
[sudo] password for pockets: 
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:28 memory:c0000000-cfffffff(prefetchable) ioport:5000(size=256) memory:d2300000-d230ffff memory:d2200000-d22fffff

Please help, I'm getting a headache from the screen!

edit: I've already messed around following instructions from other threads so there might be stuff in there, not meant to be there. can't really remember what i did.

---

### Post by sgosnell on 2009-11-21
Your graphics card will output 1280x800, but your laptop screen will only display 1280x768, at least that's what your post says.  Are you certain you ever had a full 1280x800 on your laptop screen?

---

### Post by luadraman on 2009-11-21
Absolutely positive. I did a google image search previous to my problem where I used the 'Use Desktop Image Size' option and all the downloads are 1280x800. The screen now looks almost the same but has lost it's sharpness.
It happened after attaching the TV to the laptop, I had to log out and log back in but my regular resolution never came back.
Tnx!

---

### Post by sgosnell on 2009-11-21
The downloads were going to a TV, right, so it can use higher resolutions.  Your LCD screen only has 768 vertical pixels, or so your post says, so it can't display more than that.  It's possible to get virtual resolutions in some cases, but you would have to change the horizontal resolution also, I think.  I don't see how you would ever get 1280x800, and 32 more pixels vertically aren't that much.

---

### Post by luadraman on 2009-11-21
Hi, thanks, I know what you're saying, but the laptop was definitely going up to 1280x800, I have Windows on the laptop too and it works at that resolution. I know there isn't that big a difference in pixels but everything now comes across too soft/blurry.

---

### Post by sgosnell on 2009-11-22
Try reading [this post](http://ubuntuforums.org/showpost.php?p=8365785&postcount=9) and see if it helps.  His problem looks to be very similar to yours.

---

### Post by luadraman on 2009-11-23
> **sgosnell said:**
> Try reading [this post]("http://ubuntuforums.org/showpost.php?p=8365785&postcount=9") and see if it helps.  His problem looks to be very similar to yours.

Hi, that didn't work but... I removed the xorg.conf (accidentally!), restarted Ubuntu and found that the proprietary driver for the ATI card wasn't activated. When activated and Ubuntu restarted I was able to select 1280x800 resolution. I presume I can go through this rigmarole every time I want to revert after enabling the TV but what's the permanent solution?
Here's my info now:

```
pockets@pockets-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
LCD connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   800x600        60.0 +
   720x480        60.0 +
   640x480        60.0 +
   640x432        60.0 +
   640x400        60.0 +
   512x384        60.0 +
   400x300        60.0 +
   320x240        60.0 +
   320x200        60.0 +
CRT1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
COMPONENT_VIDEO disconnected (normal left inverted right x axis y axis)

pockets@pockets-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

pockets@pockets-laptop:~$ sudo lshw -C display
[sudo] password for pockets: 
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:28 memory:c0000000-cfffffff(prefetchable) ioport:5000(size=256) memory:d2300000-d230ffff memory:d2200000-d22fffff
```

If there's any more info I should put up please tell me *exactly* how to get that info. Thanks!

---

### Post by sgosnell on 2009-11-23
I don't connect to a TV, nor do I have s-video output on my computer, so I'm pretty much at the end of my ability to help you.  You shouldn't need to change anything when you connect the TV, but I can't do any actual experimentation.

---

### Post by luadraman on 2009-11-24
Thanks anyway, I'll play around with it when I have a bit more time and post back how I get on.

---

### Post by MatthewBlack on 2009-12-30
I had exactly this problem. I have subsequently found out that when I attached my laptop to a tv and played about with the settings in the gui, it generated a /etc/X11/xorg.conf file. I deleted this, as well as a file called ~/.config/monitors.xml, restarted X and it fixed the problem. Hooray.

---

