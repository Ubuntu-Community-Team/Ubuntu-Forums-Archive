---
title: "cant choose 1280*1024 resolution"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Neutrosider on 2011-07-26
Hello. I'm quite new to ubuntu and have a problem google wastn't able to solve.
I've got a Geforce 8500 GT (if that matters) and because the picture on my tft is a little bit blurry if i choose any other resolution than 1280*1024 i tried to choose it, but its not in the resolution-list.

i already googled some hours and managed to install the latest nvidia geforce driver, using this guide: [http://wiki.linuxgaming.de/index.php/NVidia_Treiber_Installation_%28Ubuntu%29](http://wiki.linuxgaming.de/index.php/NVidia_Treiber_Installation_%28Ubuntu%29)
(i'm german) and this driver: [http://www.nvidia.de/object/linux-display-amd64-275.21-driver-de.html](http://www.nvidia.de/object/linux-display-amd64-275.21-driver-de.html)

my ubuntu is a quite fresh installed 64 bit 11.04, the only change is the nvidia driver i installed.
and btw. i read a lot about the xorg.conf, but i dont have this file, a also read i don't need it.

hope you can help me and excuse my english :)

---

### Post by LowSky on 2011-07-27
if you have  the nvidia driver installed, then open a terminal and use this comaand
```
gksu nvidia-settings
```

you should be able to pick all available resolutions,.

dont forget to save changes to the xorg file before exiting. yes you do need it

---

### Post by samstreet101 on 2011-07-27
You may have to add it to the 'xrandr' list.

Check this link out: [http://www.arunviswanathan.com/node/53](http://www.arunviswanathan.com/node/53)

---

### Post by 007casper on 2011-07-27
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Neutrosider on 2011-07-27
i frst tried what samstreet told me to, so i entered xrandr | grep maximum in my console. it says my maximum framebuffer size would be 1024*768, althoug im able to get to 1152*864 using NVIDIA X Server settings. when i change to 1152*864  xrandr | grep maximum suprinsingly tells me that the maximum framebufer size is now 1152*864

I will now try the other things you posted.

and thanks for the help, finaly a community that is _really_ helpful :)

EDIT: btw. im able to coose 1360*768 in the NVIDIA X server settings, but my display is unable to use this resolution. it seems the only important resolution for me is missing, will contonue trying what you posted

EDIT2: i now checked every link.
@Lowsky: i have some resolutions to choose there, but as already said the preferred resolution is not in the list ...
@samstreet101: look at the top of the post ^^
@007casper: these seem to be really helpful tutorials if you have problems with the graphics in the bootloader or while booting, but it sadly seems to be unhelpful while trying to use the right resolutin in the XServer. but thx anyway

---

### Post by Neutrosider on 2011-07-28
*push*
still couldn't fix the problem :(

---

### Post by realzippy on 2011-07-28
Run
```
sudo nvidia-bug-report.sh
```

...script creates file in your home folder,contains relevant infos like
Xorg.0.log,xorg.conf aso.
Post created file so we might get a clue...

---

### Post by Neutrosider on 2011-07-28
everything you guys need to help me :)
here is the bug report: _[http://zload.file4u.net/ax/nichtaxdateien/nvidia-bug-report.log](http://zload.file4u.net/ax/nichtaxdateien/nvidia-bug-report.log)_

---

### Post by realzippy on 2011-07-28
Run
```
sudo nvidia-xconfig
```

and reboot or restart Xserver.

(according to log:
[I]-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: N
   o)[/I]
you have *not* during driver installation;dunno if you did manually?)

After you have run nvidia-xconfig,can you post the new
/etc/X11/xorg.conf file ?

Also the driver cannot read your monitor's edid data:
*[    20.079] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0*

Which monitor do you use?

---

### Post by Neutrosider on 2011-07-28
after i typed sudo nvidie-xconfig in my terminal, he regognized that there is no xorg.conf and created one. after i rebooted the computer, the highest resolution i now can choose is 640*480

i choosed no in the installation because the tutorial to install the nvidia driver told me so, but its an old tutorial...

my monitor is an Targa Visionary LCD 17-2 (Model L70S)

here is the xorg.conf (its quite hard tu use filezilla with this resolution XD): [http://zload.file4u.net/ax/nichtaxdateien/xorg.conf](http://zload.file4u.net/ax/nichtaxdateien/xorg.conf)

---

### Post by realzippy on 2011-07-28
*...the highest resolution i now can choose is 640*480*

that's ok since the driver misses the monitor data.
It now uses the "vanilla" Hsync which limits the available resolutions.

Give me a few minutes to search the web for your monitor's valid Hsync
frequency....will then edit xorg.conf and post it.

Or do you have a manual for it with proper Hsync/Vrefresh values?

---

### Post by realzippy on 2011-07-28
Is it this monitor:
[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.prad.de%2Fpdf%2Ftarga_visionary_lcd17-2.pdf&rct=j&q=Targa%20Visionary%20LCD%2017-2%20hsync&ei=AGAxTt7tCIij-gaejvWADQ&usg=AFQjCNGzZ2Ymwsci68vIabC4LeEP7V-cqg&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.prad.de%2Fpdf%2Ftarga_visionary_lcd17-2.pdf&rct=j&q=Targa%20Visionary%20LCD%2017-2%20hsync&ei=AGAxTt7tCIij-gaejvWADQ&usg=AFQjCNGzZ2Ymwsci68vIabC4LeEP7V-cqg&cad=rja)
?

---

### Post by Neutrosider on 2011-07-28
a friend gave me this screen, so i have no manual.
but im really glad that you help me :)

EDIT: No i have a 17-3, not a 17-2 ^

---

### Post by realzippy on 2011-07-28
..see post #12   ;-)

---

### Post by Neutrosider on 2011-07-28
see post #13 ^^

---

### Post by realzippy on 2011-07-28
lol
see post #10
you wrote "2"   ;-)
..anyway,will search for it.Wait a minute..

---

### Post by Neutrosider on 2011-07-28
oh, i really wrote 17-2 -.-
take it as special effect of my keyboard :D

---

### Post by realzippy on 2011-07-28
So it is
[http://www.targa.de/index.jsp?SID=0&NAV=236&DOC=&PAGE=392&PCAT=2&PROD=89&PTUBE=18&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined](http://www.targa.de/index.jsp?SID=0&NAV=236&DOC=&PAGE=392&PCAT=2&PROD=89&PTUBE=18&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined)

Run

```
gksudo gedit /etc/X11/xorg.conf
```

..and change:

HorizSync       [COLOR="Red"]28.0 - 33.0[/COLOR]
VertRefresh     [COLOR="Red"]43.0 - 72.0[/COLOR]

to

HorizSync       31.0 - 80.0
VertRefresh     56.0 - 75.0

...close file saving changes.
Reboot or restart Xserver.
Normally your native resolution 1280x1024 should be available then...

---

### Post by Neutrosider on 2011-07-28
yeah, i now have a lot of new resolutions to choose, and 1280*1024 is one if it :)
but i can't choose it within the screensettings windows, but only with NVIDIA Display settings.

the highest i can choose in the normal dsiplay settings windows is 1024*768

---

### Post by realzippy on 2011-07-28
You **should** use nvidia-settings instead of the gnome-GUI.
Normally the "Monitors" tool gives a warning and should ask
to use graphic card's vendor tool (i.e. the nvidia-tool) instead...
Didn't it?

Note,
when setting the resolution (or other stuff) with nvidia-settings
you should hit "SaveToXconfigurationFile" to make changes persist a reboot.

**BTW**
Why did you install the nvidia driver manually and did not
use the System-Administration-HardwareDrivers tool?

---

### Post by Neutrosider on 2011-07-28
thx for the info. now my problem is really solved and i can enjoy ubuntu with beautyful graphics :)

if you mean whats called zusätzliche treiber in my german ubuntu then the answer is that this tool seems to give me outdated drivers. (version 173)
i downloaded the newest driver for linux 64 bit from the nvidia website and installed this one (version 275)

---

### Post by realzippy on 2011-07-28
Ok.
Trouble ahead:

If you manually install a nvidia-driver,you will have to repeat
this every time when a kernel-update comes..
So don't be surprised when your resolution/driver is gone some day...

Better solution is to add eg the
[xswat ppa]("http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=natty#") to your sources.
The "current" nvidia-driver offered in "zusätzliche treiber" will
then be up-to-date (also 275.xx in the moment) , and you won't have to care any more when running system
updates.
Simply run:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```

then reinstall the manually installed driver with "zusätzliche treiber" or wait until the next kernel update breaks your driver and do it then.

---

### Post by Neutrosider on 2011-07-28
this site looks interesting. its nearly the newest version (275.19 vs 275.21)
i typed these lines in my terminal and he did something, but there are still the same drivers under "zusätziche treiber" (translated its additional drivers).
but there is a new update avaliable in my update manager. do i need to install this update to work? (LP-PPA-ubuntu-x-swat-x-updates -> Video Acceleration (VA) API for Linux - runtime)

---

### Post by realzippy on 2011-07-28
Guess so.


**Edit:**

*Sure* that there is no "nvidia-current" offered in additional drivers?

---

### Post by Neutrosider on 2011-07-28
hm. didn't change antything in the zsuätliche treiber menu. are you sure  we're taling about the same driver menu? mine looks lie this (just took  this screenshot):
[http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto.png](http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto.png)

---

### Post by realzippy on 2011-07-28
Yep.
There are 2 video drivers offered in your screenshot...
one might be 173.xxx,the other should be
275.xx  ("current")..
Can you check this out?

---

### Post by Neutrosider on 2011-07-28
its not directly telling me the version i can activate, but here are the two texts:
the first one has this text:
> The binary driver provide optimized hardware acceleration of OpenGLapplications via a direct-rendering X Server. AGP, PCIe, SLI, TV-outand flat panel displays are also supported.

This package also includes the source for building the kernel modulerequired by the Xorg driver.

GPUs ranging from GeForce series 5 to GeForce series 9 are supported.

See /usr/share/doc/nvidia-173/README.txt.gz for a complete listof supported GPUs and PCIIDs

because at the end the path includes nvidia-173, i think this would install the outdatet driver.

and this is the second text:
> The binary driver provide optimized hardware acceleration of OpenGLapplications via a direct-rendering X Server. AGP, PCIe, SLI, TV-outand flat panel displays are also supported.

This package also includes the source for building the kernel modulerequired by the Xorg driver, and provides NVIDIA's implementation ofthe Video Decode and presentation API. The latter enables accelerationfor GeForce 8 and later series cards for h264 video.

GPUs such as GeForce series 6 or newer are supported.

See /usr/share/doc/nvidia-current/README.txt.gz for a complete listof supported GPUs and PCIIDs


wait a moment... this is the first time i read the second text to the end, where the path says something about nvidia-current (as you can see).

you think this might work?

---

### Post by realzippy on 2011-07-28
Yes.
nvidia-current
now is 
-after you have added xswat ppa to your sources-
the driver from xswat.
To verify this,you could open
"Synaptic Paketverwaltung" (or similar)
in System/Administration...
In synaptic,search for nvidia-current.
If you right-click this,you can see the version in 
properties (Eigenschaften).

You could also sort the packages on the left with sources (Ursprung),
where you could click the xswat ppa and see nvidia-current on the right
side.
You could install it from synaptic also,but you should prefer
jockey  (the "zusätzliche treiber" tool)...

---

### Post by Neutrosider on 2011-07-28
ok. i now just tried the nvidia-current thing in the additional drivers manu.

before the NVIDIA settings told me i've got version 275.21 installed, wich was correct :)
now that i activated the nvidia-current thing in the additional drivers menu, it shows me that i got version 275.19 installed wich is perfectly right :)

[http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-1.png](http://zload.file4u.net/ax/nichtaxdateien/Bildschirmfoto-1.png)

everything seems to work just fine :)

---

### Post by realzippy on 2011-07-28
Btw,the message:

*driver is activated but not in use*

(treiber aktiviert aber nicht in benutzung)

is a BUG.
Simply ignore it.
If the driver was not in use,then nvidia-settings would complain
and refuse to start...
So,as everything seems ok,have fun!


One more thing:
Since updates sometimes (not very often) break a system,
and cannot be re-done easily,I suggest (if your system runs fine)
to de-activate the update-manager in system-settings-startup applications
and check for updates manually (Once a week eg; a "bad" package
normally gets fixed fast by the community)..

---

### Post by Neutrosider on 2011-07-28
ok, thanks for the advice :)
does this forum has something like a thanks button or somethink like this? i would rape it :D
you really helped me a lot :)

---

### Post by realzippy on 2011-07-28
No thanks-button.
You want my bank details?

Kidding,of course.
If you have fun with Ubuntu,you might help
someone else some day.
This is how "Ubuntu" works...

---

