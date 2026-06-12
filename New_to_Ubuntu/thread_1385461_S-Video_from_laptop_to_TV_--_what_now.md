---
title: "S-Video from laptop to TV -- what now ??"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jerrynewt on 2010-01-19
Ok here goes -- I am staying in a motel here in Ft. Worth, and using their broadband internet (not as fast as it should be really. Only 100 Kb max). I have an S-Video cable attached from my laptop (specs in signature) to the motel television. I want to play a program (NCIS) on the computer and watch it on the motel television. My graphics card is NVIDIA GeForce 8400M GS.(Program plays just fine on computer so far).

---

### Post by shadow120 on 2010-01-19
i think you have to switch it under system - preffernces - display.  im not sure but its worth a try

---

### Post by tom.swartz07 on 2010-01-19
> **jerrynewt said:**
> Ok here goes -- I am staying in a motel here in Ft. Worth, and using their broadband internet (not as fast as it should be really. Only 100 Kb max). I have an S-Video cable attached from my laptop (specs in signature) to the motel television. I want to play a program (NCIS) on the computer and watch it on the motel television. My graphics card is NVIDIA GeForce 8400M GS.(Program plays just fine on computer so far).

Ive tried to get this to work with little success on my ATI radeon card.

You need to assure that you have your drivers up to date and enabled for the video card. Believe it or not, Ubuntu runs just fine without any major card doing the processing. NVIDIA drivers should be fine for you, ATI's dont have as much support.

Once the card is enabled and working all great, you could try the method that was mentioned about display options. Also, see if theres a 'hot-key' combo on your keyboard, usually its FUNCTION + F8 or something.

Hopefully thatll work!

---

### Post by LowSky on 2010-01-19
you will need an application called nvidia-settings, it in Synaptic, and will allow you to switch screens.

it will install under System > admin

---

### Post by jerrynewt on 2010-01-19
Tried the Nvidia X server settings but can't seem to make head or tails out of it. I don't even know where to start configuring the TV0 screen at all. Any insight would be greatly appreciated guys.

---

### Post by 3rdalbum on 2010-01-19
Have you tried merely rebooting with the TV on and plugged into your S-Video port?

---

### Post by fooman on 2010-01-19
try this...open nvidia settings as root by opening a terminal (applications > accessories > terminal) and type or copy paste the following:

```
gksudo nvidia-settings 
```

when it opens,  click "x server display configuration". then, on the lower right side,  under the "display" tab...click the "configure" button.  in the box that pops up,  choose "separate x screen"...click  ok.  you may see a warning that not all settings could be saved...say ok or continue to that.

then click "save to x configuration file".  log out and back in again and see if that helps.

---

### Post by jerrynewt on 2010-01-19
Ok, all goes well untill I hit "save to x configuration file". I get the following message "Failed to parse existing X config file 'etc/X11/xorg.conf'.

---

### Post by fooman on 2010-01-19
close any nvidia-settings windows that may still be open...then in a terminal again,  try running:

```
sudo nvidia-xconfig
```that should backup and create a new xorg file....then try the above procedure again and see if it works this time.

---

### Post by jerrynewt on 2010-01-19
When I hit the Save to X configuration file I get message "Cannot remove etc/X11/xorg.conf.backup".

---

### Post by jerrynewt on 2010-01-20
Bump*

---

### Post by fooman on 2010-01-20
> **jerrynewt said:**
> When I hit the Save to X configuration file I get message "Cannot remove etc/X11/xorg.conf.backup".

sorry,  were you sure to run "nvidia-settings" with the gksudo prefix? ...like this:

```
gksudo nvidia-settings
```

---

### Post by tom.swartz07 on 2010-01-20
I was just about to correct the gksudo command- glad you caught it.


If that doesnt work, try assuring everything is connected and running

```
xrandr
```
from the terminal to see if it detects that its connected. 
Most of the time its just a matter of running that and it sets itself up

---

### Post by jerrynewt on 2010-01-20
Mmmm tried the xrandr and it only shows one monitor screen 0.

---

### Post by no2498 on 2010-01-20
need to change tv itself to allow it

---

### Post by tom.swartz07 on 2010-01-20
> **jerrynewt said:**
> Mmmm tried the xrandr and it only shows one monitor screen 0.

It might be the case that you need to get a scan converter...

With my computer, the video output was too 'high' for TV's to handle. I grabbed this exact one for cheap and I have it in my bag for when i need it.

[http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac](http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac)

Hope this helps.


Im assuming your rig has a VGA out port on it, right?

---

