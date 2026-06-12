---
title: "help installing graphics drivers... on intel chipset."
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ja660k on 2009-03-07
hey guys,
i have a compaq cq60 laptop and i cant play videos on it.
and i dont know how to get them to work.

i havnt done anything to install graphics drivers.

lspci of my VGA card is:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

please help

---

### Post by Redache on 2009-03-07
Intel Drivers should be installed automatically as they are Open Source (to an extent).

What Video's are you having trouble playing? Could it be a codec problem rather than a Graphics problem?

---

### Post by ivanvajar on 2009-03-07
I had problems 2 days ago while installing Ubuntu on a friend's computer. For drivers run: 

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel

Keep in mind that Compiz won't work (probably). I'm downloading Sabayon Linux right now. I'll see if that distribution supports Intel VGAs. Best of luck.

---

### Post by ja660k on 2009-03-07
im not sure, just any extension except for .flv

what happens is i open the video. it plays for a second then my screen goes black. keyboard & mouse is unresponsive,
i have to ctrl+alt f6 and restart the
computer before it goes back to normal.

if it helps, i can play games? i have diablo 2 installed along side some linux games?

```

root@FluxXx:~#apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.

```

---

### Post by ivanvajar on 2009-03-07
For codecs, run: sudo apt-get install ubuntu-restricted-extras

---

### Post by ja660k on 2009-03-07
```

root@FluxXx:~#apt-get install ubuntu-restricted-extras 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded
```

i allready have it. i dont know what the problem is?

---

### Post by ivanvajar on 2009-03-07
Also, Look in System/Preferences/Multimedia system selector in 'Video' tab. What is your default output plugin?

---

### Post by ja660k on 2009-03-07
> **ivanvajar said:**
> Also, Look in System/Preferences/Multimedia system selector in 'Video' tab. What is your default output plugin?

i dont have that?

---

### Post by ivanvajar on 2009-03-07
Right-click on Applications menu and select Edit Menus. Find Preferences at the bottom of the branch and select Multimedia Systems Selector. In Multimedia Systems Selector, Video tab, as output plugin Autodetect is probably selected. Try **X Window System (No Xv)** or **X Window System (X11/Xshm/Xv)**

---

### Post by ja660k on 2009-03-07
oh. thanks
thats handy =)

i get this (attatched)

---

### Post by ivanvajar on 2009-03-07
OK. Now you should see Video tab in that window. Try different plugins.

---

### Post by ja660k on 2009-03-07
so its now a trail and error, until the computer wont die?

---

### Post by ivanvajar on 2009-03-07
It should work with X Window System (No Xv). If not, I'm out of ideas. I never needed to customize those settings.

---

### Post by ja660k on 2009-03-07
damn, maybe im not meant to have video. lol

everything i test the default output ... the same thing happens. i dont understand.

when i go to X Window System(X11/Shm/Xv)
the device is intel(R) video overlay. but then it still wont work.

thanks for trying.

---

### Post by ivanvajar on 2009-03-07
Let's see one more thing...

---

### Post by ivanvajar on 2009-03-07
Open System/Administration/Hardware drivers. Do you see any propriatry drivers in use?

If you don't have it installed go to Add/Remove Programs, look in System tools and find Hardware Drivers (Configure third-party and proprietary drivers)

---

### Post by ja660k on 2009-03-07
none for video drivers.

atheros Hardware Layer (HAL)
support for atheros 802.11 wireless lan cards.

both of them unchecked and not in use

---

### Post by ivanvajar on 2009-03-07
I'm so sorry. Intel Graphics Controllers are just pain in the ... eye. I had so much trouble configuring them on another computer few days ago. I'll see if Sabayon Linux supports Intel chipsets better. ([www.sabayonlinux.org](www.sabayonlinux.org) - if you're interested) I've been told that maybe some other Linux distributions have better support for your chipset and Sabayon is great distribution. Best of luck!

---

### Post by ja660k on 2009-03-07
no no, nevermind its all good
again. thanks for trying =)

---

### Post by 3rdalbum on 2009-03-07
Well, what video player are you using?

Totem Movie Player won't work with certain video files. Try installing VLC or gnome-mplayer as these are good, reliable video players.

---

### Post by ja660k on 2009-03-08
i have a host of video players. i dont think its that though, when i go to system > admin > hardware test

the video one fails. my computer dies from it

---

### Post by st33med on 2009-03-08
WOAH WOAH slow down.  Intel drivers are already installed on your machine, there should be no problems.  However, a few of the newer ones may have problems.

Please post the output of:
```
lspci | grep VGA
```

---

### Post by ja660k on 2009-03-08
yeah, i have them installed... but somehow it dies when i try play any video, any format except .flv

output:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

---

### Post by st33med on 2009-03-08
Could you do this in the terminal

```
lspci -k
```

This will tell us what driver your card is using.

---

### Post by ja660k on 2009-03-08
i dont have that flag
```

ja660k@FluxXx:~$lspci -k
lspci: invalid option -- k
Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging


```

---

