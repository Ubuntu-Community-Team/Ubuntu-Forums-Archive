---
title: "nVidia Graphics card unusually loud"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Clampdown on 2011-03-08
Hey everyone! I just installed Ubuntu 10.10 today and ran into a  problem with my graphics card. 

The card is an nVidia Geforce 9800 GT, and runs on the desktop at about 70-75 degrees Celsius from the moment I log in. The temperature, along with the fans running consistently at 100%, has me a little concerned. Is this normal, and if not, are there any fixes? I'm currently using the driver version 260.19.06, if that's any help.

Thanks!

---

### Post by GWBouge on 2011-03-08
How long have you had the card?  What temperatures was it running in the previous OS?

I had an 8800GT and an 8600GTS for a while, and they both ran around that temperature with the fans at 30% - 40% or so, which actually made a bit of noise.  And for whatever reason, Ubuntu liked to keep my fans running higher than Windows did.  Those model nVidia's (or nVidia in general, rather, until the newer ones) run a bit hotter than others, but you don't really have any issues until you get 95+ for a period of time.

I *think* the nvclock utility works with that card ... you can try:
```
sudo apt-get install nvclock
nvclock -i
```
to see what's going on with it.

---

### Post by Clampdown on 2011-03-08
> **GWBouge said:**
> How long have you had the card?  What temperatures was it running in the previous OS?

I don't quite remember. It's been about two months since the card's actually seen any use whatsoever. I want to say that the card used to run about the same, if not a little hotter, but was significantly quieter. I'm not positive, though.

And I think I've had the card since about... June? Maybe farther back.

---

### Post by Clampdown on 2011-03-08
I just tried the nvclock thing you suggested, and found something pretty interesting.

> -- General info --
Card:         nVidia Geforce 9800GT
Architecture:     G92 A2
PCI id:     0x614
GPU clock:     555.428 MHz
Bustype:     PCI-Express

-- Shader info --
Clock: 1350.000 MHz
Stream units: 112 (01111111b)
ROP units: 16 (1111b)
-- Memory info --
Amount:     1024 MB
Type:         256 bit DDR3
Clock:         899.996 MHz

-- PCI-Express info --
Current Rate:     16X
Maximum rate:     16X

-- Sensor info --
Sensor: GPU Internal Sensor
**GPU temperature: -362C**

-- VideoBios information --
Version: 62.92.84.00.51
Signon message: PNY Verto GeForce 9800 GT Energy Efficient PCIe 2.0
Performance level 0: gpu 550MHz/shader 1375MHz/memory 900MHz/1.00V/100%
Performance level 1: gpu 550MHz/shader 1375MHz/memory 900MHz/1.00V/100%
VID mask: 3
Voltage level 0: 0.95V, VID: 0
Voltage level 1: 1.00V, VID: 2
Voltage level 2: 1.05V, VID: 3


You'd figure that the fans would take a break once the GPU's gone *below Absolute Zero*.

---

### Post by GWBouge on 2011-03-08
Ha!  Your air conditioning must be fantastic!

Someone with a bit more knowledge on this feel free to pipe up, but you might need to install lm-sensors to get it to read the temperature and fan speeds properly (I didn't see the fan info in that output?).

```
sudo apt-get lm-sensors
sensors-detect
```

You can use nvclock to manually adjust the fan speeds, but if you were to, say, turn the fans down to 30% to keep the noise down, then start playing a game and forget to adjust the fans, the fans would **stay at 30%**, and your card will overheat.  It also has an 'auto' option, though, to let the drivers automatically control the fan.

```

# Throttle down to 30%
nvclock -f -F 30

# Automatic
nvclock -f -F auto

```

I never liked the way Ubuntu handled the fan on my 8800GT, so I made [this little utility]("http://sourceforge.net/projects/nfo/") to do just that.  But again, I think you'll need the lm-sensors to read the temps/fans right, and you'll need python-wxversion (a GUI toolkit for Python) installed to run the app.

On a simpler note ... does the fan sound like it's hitting something, or is it just loud?  I assume you made sure it wasn't plugged up with dust or anything ...

---

### Post by Clampdown on 2011-03-08
> **GWBouge said:**
> Ha!  Your air conditioning must be fantastic!

Someone with a bit more knowledge on this feel free to pipe up, but you might need to install lm-sensors to get it to read the temperature and fan speeds properly (I didn't see the fan info in that output?).

Well I've been using the NVIDIA X Server Settings thing to monitor the temp and fan speeds. 

I *did *find [this other thread regarding fan-speeds]("http://ubuntuforums.org/showthread.php?t=1678374"). I followed the instructions, and tested out the fan controls in the server settings. 

But this reminds me of a detail that I guess I didn't make clear in the OP. 

I started having this problem after I went into "Additional Drivers" and activated the driver (Version 260.19.06), which I resorted to after I couldn't figure out how to install the very latest driver (version 260.19.44).

I know there's an open source nVidia driver called Noveau or something, and I can only assume it was installed (I kept getting an error that said that I would have to disable Noveau to install driver 260.19.44), but it didn't work well at all and I couldn't even run Gratuitous Space Battles with it :p

I don't know. I'm really at a loss here. At first I thought, "well, maybe the fans are just running higher than they did on windows", but I'm pretty sure the card itself is way hotter than it used to be. I know these cards run hot but I think 75-78 C is a little much for no-load.
 
> On a simpler note ... does the fan sound like it's hitting something, or is it just loud?  I assume you made sure it wasn't plugged up with dust or anything ...

Went through it with dust cleaner just before I came here :D

---

### Post by Clampdown on 2011-03-15
Bumping this because I'm still having problems with the temperature of my card... Playing WoW on the lowest settings gives me temperature readings of 85 and sometimes up to 90 degrees Celsius. I'm thinking that maybe the software isn't getting the temperature right, but I don't want to risk it.

I have the latest drivers. Has anyone had this problem before?

---

