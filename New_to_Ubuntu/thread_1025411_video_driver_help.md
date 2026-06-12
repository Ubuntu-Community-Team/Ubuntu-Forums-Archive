---
title: "video driver help"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by quadcam on 2008-12-30
I had some issues with the first install So I reinstalled Ubuntu 8.10 , did 3 partitions, "/ " 15 gig, 2gig swap and 20 gig "/home". Once again I tried to get my Nvidia card working this time I tried  using the apt-get install nvidia-settings method and that that seemed to work. But when I tried to chnage my screen resolution I could only get 800X600 max and unknown display. 

I found the Nvidia X server settings under the System / Admin menu and tried to use it but got an error saying that I'm not using the Nvidia Xserver and I ned to do "nvidia-xconfig" in a terminal window. 

Did that and I got 

"Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'."

I have no idea what that means...corrupt file? 

FWIW my video info is 00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
using Driver ver 177

---

### Post by igknighted on 2008-12-30
run 'sudo nvidia-xconfig', then restart X and try to run the nvidia-settings app again.

---

### Post by quadcam on 2008-12-30
hmmm, ok well...heres what happened.
it worked, kinda. it backed up my xserver config and wrote a new conig...i restarted xserver and it crashed "unable to parse config file"
so it gave me the option to boot into low res mode...I had copied the error log but now I cant find it. 

anyway, I take the low res option and it boots...full screen,high res. 1240x1024. I just bumped it back to 1024x768. tried the nvidia xserver setting but it still says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I'm not sure i want to mess with it now , this is the first time i managed to have it run at full screen instead of just what I could only call "widescreen format"

thanks for the help...I think i'm headin to bed, i'll work on this again later

---

### Post by quadcam on 2008-12-30
ok so i'm back at it, everything is working fine..until i reboot and then i get the video config error. 



Mo[COLOR="Red"]dule Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 30 10:27:44 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 12 of section Files in file /etc/X11/xorg.conf
	"RgbPath" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor"
[/COLOR]

this is the startup error log
[COLOR="Red"]

5220 5004
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log



Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Dec 30 10:27:46 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
5220 5004[/COLOR]

i tried to reinstall nvidia settings and I get :

[COLOR="Red"]Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/COLOR]

and then when i open Nvidia Xserver settings from the system >admin menu
it says:
[COLOR="Red"]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. [/COLOR]

any thoughts/suggestions?

---

