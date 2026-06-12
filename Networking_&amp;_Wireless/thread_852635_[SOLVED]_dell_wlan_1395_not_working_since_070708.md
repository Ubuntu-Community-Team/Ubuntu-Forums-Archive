---
title: "[SOLVED] dell wlan 1395 not working since 07/07/08"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Hoaxe on 2008-07-07
so i'm having a very peculiar problem with my wireless card.

the card is a dell minicard wlan 1395
it's inside a dell vostro 1500

it was working for many weeks until i had installed updates this morning, the updates are: 
```

Commit Log for Mon Jul  7 04:26:56 2008


Upgraded the following packages:
gstreamer0.10-plugins-ugly (0.10.7-3) to 0.10.7-3ubuntu1
language-support-writing-en (1:8.04+20080410) to 1:8.04+20080630
libblas3gf (1.2-1.3ubuntu3) to 1.2-1.3ubuntu4
libcairo2 (1.6.0-0ubuntu1) to 1.6.0-0ubuntu2
libpurple0 (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42) to 2.6.24.13-19.44
linux-restricted-modules-common (2.6.24.13-19.42) to 2.6.24.13-19.44
nvidia-glx-new (169.12+2.6.24.13-19.42) to 169.12+2.6.24.13-19.44
openoffice.org-base-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-calc (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-draw (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gnome (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gtk (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-us (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-impress (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-za (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-style-human (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-writer (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
pidgin (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
pidgin-data (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
python-uno (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
tomboy (0.10.1-1) to 0.10.2-0ubuntu1
ttf-opensymbol (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
x11-common (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xbase-clients (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xlibmesa-gl-dev (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-input-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-amd (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-geode (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-nsc (1:2.8.3-2) to 1:2.8.3-2ubuntu0.1
xutils (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2

Installed the following packages:
openoffice.org-hyphenation-en-us (2.3.1-2ubuntu1)

```

i suspect the linux updates to be my problem and i can not roll back to my version, they simply aren't available in the repo.

so i followed this post to get my wireless working: 
[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)
all the steps went through with no errors

yet the wireless is still not wokring. HOWEVER my wireless icon on the right side of my laptops' keyboard is now lit.

furthermore, when i type lspci, the wireless is detected:
```

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

yet i still can not connect through my wireless. if any one can help me with figuring this out, i would appreciate. i feel very close, and yet...

also, i beleive this guy has the same problem as me: 
[http://ubuntuforums.org/showthread.php?t=850365](http://ubuntuforums.org/showthread.php?t=850365)

EDIT: the wifi light next to my keyboard is not on anylonger. i don't know what that was about.

---

### Post by Ayuthia on 2008-07-07
> **Hoaxe said:**
> so i'm having a very peculiar problem with my wireless card.

the card is a dell minicard wlan 1395
it's inside a dell vostro 1500

it was working for many weeks until i had installed updates this morning, the updates are: 
```

Commit Log for Mon Jul  7 04:26:56 2008


Upgraded the following packages:
gstreamer0.10-plugins-ugly (0.10.7-3) to 0.10.7-3ubuntu1
language-support-writing-en (1:8.04+20080410) to 1:8.04+20080630
libblas3gf (1.2-1.3ubuntu3) to 1.2-1.3ubuntu4
libcairo2 (1.6.0-0ubuntu1) to 1.6.0-0ubuntu2
libpurple0 (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42) to 2.6.24.13-19.44
linux-restricted-modules-common (2.6.24.13-19.42) to 2.6.24.13-19.44
nvidia-glx-new (169.12+2.6.24.13-19.42) to 169.12+2.6.24.13-19.44
openoffice.org-base-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-calc (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-core (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-draw (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gnome (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-gtk (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-help-en-us (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-impress (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-common (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-gb (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-l10n-en-za (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-style-human (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
openoffice.org-writer (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
pidgin (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
pidgin-data (1:2.4.1-1ubuntu2) to 1:2.4.1-1ubuntu2.1
python-uno (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
tomboy (0.10.1-1) to 0.10.2-0ubuntu1
ttf-opensymbol (1:2.4.1-1ubuntu1) to 1:2.4.1-1ubuntu2
x11-common (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xbase-clients (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xlibmesa-gl-dev (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-input-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-all (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2
xserver-xorg-video-amd (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-geode (2.8.0-7) to 2.9.0-1ubuntu2.4
xserver-xorg-video-nsc (1:2.8.3-2) to 1:2.8.3-2ubuntu0.1
xutils (1:7.3+10ubuntu10) to 1:7.3+10ubuntu10.2

Installed the following packages:
openoffice.org-hyphenation-en-us (2.3.1-2ubuntu1)

```

i suspect the linux updates to be my problem and i can not roll back to my version, they simply aren't available in the repo.

so i followed this post to get my wireless working: 
[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)
all the steps went through with no errors

yet the wireless is still not wokring. HOWEVER my wireless icon on the right side of my laptops' keyboard is now lit.

furthermore, when i type lspci, the wireless is detected:
```

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

```

yet i still can not connect through my wireless. if any one can help me with figuring this out, i would appreciate. i feel very close, and yet...

also, i beleive this guy has the same problem as me: 
[http://ubuntuforums.org/showthread.php?t=850365](http://ubuntuforums.org/showthread.php?t=850365)

This is a guess, but I am thinknig that the wl driver was loaded.  That was found in linux-restricted-modules.  You can see if that is loaded by going to the Terminal and typing:
```
lsmod|grep wl
```If it is there, you can blacklist it by going into the Terminal and typing:
```
echo blacklist wl|sudo tee -a /etc/modprobe.d/blacklist
```
To restore it for this session you should be able to do it by going to the Terminal and typing:
```
sudo modprobe -r b43 b44 ssb wl bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
```

Hope that helps.

---

### Post by Hoaxe on 2008-07-07
nope, sorry,

interestingly, i can never enable the WL driver. everytime i go into the restricted drivers menu, i look and there is a check next to WL, but status is always not in use. even i uncheck, then recheck, the reboot.

it's always the same.

also, ```
sudo iwlist scanning
``` returns no positive results.

also, the wifi light isn't on anylonger, i don't know what it was about

---

### Post by Ayuthia on 2008-07-07
Sorry.  I have been away for a few days and just realized what is happening.  I am now understanding that you are probably using the wl driver instead of the NDISwrapper option.  If that is the case, you will need to go and edit /etc/modprobe.d/blacklist and remove the 'blacklist wl' line.  You can do this by going to the Terminal and typing:
```
gksu gedit /etc/modprobe.d/blacklist
```

You will probably be interested in this link:
[http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)
From what I am reading, the wl driver was changed in the recent linux-restricted-modules release.  According to the link, a new update should be coming soon that will fix this.  They also post a couple of workarounds that might help.

---

### Post by Hoaxe on 2008-07-07
if i wait, will the fix come and fix it on it's own?

i have a tendency to use many work arounds on my pc, but my laptop however, i like to keep more dependant/more pristine [depends how you look at it] towards the distro.

thank you so much Ayuthia

PS: how do we make a thread solved now? it's different than before...

---

### Post by Ayuthia on 2008-07-08
> **Hoaxe said:**
> if i wait, will the fix come and fix it on it's own?

i have a tendency to use many work arounds on my pc, but my laptop however, i like to keep more dependant/more pristine [depends how you look at it] towards the distro.

thank you so much Ayuthia

PS: how do we make a thread solved now? it's different than before...
The fix should be coming soon and it should fix it on it's own.  As for marking a thread solved, it should be under Thread Tools.  You should find it at the top of the page and right below the Networking & Wireless title.

---

### Post by stats on 2008-07-10
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

