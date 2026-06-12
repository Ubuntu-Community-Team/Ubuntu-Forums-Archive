---
title: "Nvidia graphics problem - Can't set a high enough resolution"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by mattcs on 2009-06-04
Using the Nvidia X Server Settings, I don't have enough choices for screen resolution. The best it will do is 1360x768. However, I would like 1680x1050 if possible.
I have been down the path of editing /etc/X11/xorg.conf and setting the 'metamodes' value to something else, but that doesn't seem to get recognised even on a reboot.
Any advice welcome.

---

### Post by labinnsw on 2009-06-04
I had a similar problem as a newbie. [Here is the link]("http://ubuntuforums.org/showthread.php?p=3793051#post379305")

---

### Post by orky7 on 2009-06-04
don't forget to back up ur xorg.conf file in case u stuck or something bad happen just replace it with the original xorg.conf

---

### Post by dca on 2009-06-04
What nVidia card do you have and can it support that high pixel rate?  Mine goes to 1280x1024 but it's an older card.

---

### Post by dca on 2009-06-04
If so, the two easiest options to get nVidia properly installed w/o going the long route of d/l & fanagling (killing 'X', etc, etc) from nVidia website is the 'restricted modules' as mentioned or installing 'envy' from the repos (through Synaptic) which also installs all needed packages.

---

### Post by mattcs on 2009-06-06
Thanks to all who've provided some replies, but I guess some more back ground is required as I believe I have found the culprit.

I am using a Belkin OmniView 2 port USB KVM switch to switch between my (Ubuntu based) PC and a company laptop with Win XP. The laptop display is fine and I have a better choice of resolution for my main monitor (though not perfect).

If I remove the the KVM switch from the equation, then Ubuntu behaves as you would expect (latest drivers and all, etc) and I have a far wider choice of monitor resolution.

Obviously I will have to contact the Belkin support area, however, does anyone have any experience with KVM switches who might be able to offer some advice ?

Thanks

---

### Post by Jazzy_Jeff on 2009-06-06
Instead of using a KVM switch you could use [QuickSynergy]("http://quicksynergy.sourceforge.net/") to use the same keyboard and mouse. You would have to put the laptop next to the main screen. You would install QuickSynergy on Linux and Synergy on Windows.

This is what I use between my laptop and main pc.

---

### Post by mattcs on 2009-06-07
Thanks to Jazzy_Jeff for a nifty KM solution, but I would really like the V(ideo) as well (which Synergy doesn't support at present).
I'll see what the Belkin customer support has to say.

---

### Post by Niko Johnson on 2009-10-15
i had this same problem using a nvidia card... when i first installed ubuntu on my new computer it looked really crappy. i only had a resultion of 800 x 600 when i needed a 1600 x 900 resolution. anyway i did some googleing and found a quick fix to it. first you have to go in the terminal and download the nvidia driver ```
 apt-get install nvidia-glx-180 
``` then after you got that you have to install the settings manager. ```
apt-get install nvidia-settings
``` then after you done that run this command as root ```
nvidia-xconfig 
``` then run the nvidia settings and log out then back in and your golden

---

