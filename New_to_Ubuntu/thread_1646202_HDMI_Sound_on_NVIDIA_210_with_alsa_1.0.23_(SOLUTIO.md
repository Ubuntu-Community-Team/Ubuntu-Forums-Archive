---
title: "HDMI Sound on NVIDIA 210 with alsa 1.0.23 (SOLUTION?)"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by stirri_pibo on 2010-12-15
I've been trying for days now to get my sound working over hdmi, I'm running ubuntu 10.10.
 
After scavenging around forums, I didn't find this solution in plain text suitable for a Linux newbie like myself.
 
1.
Check if running the code ```
alsamixer
``` and unmuting could solve problems before beginning to tamper with other things.
 
2.
Make sure your card was listed in ```
lspci | grep Audio*
``` (for me it stated: "Audio device: nVidia Corporation High definition Audio Controller")
 
3.
Found out what version of ALSA I was running using ```
cat /proc/asound/version
``` Should be 1.0.23, if not then you have to google either a update script or how to compile.
 
4.
Check to see if the module snd_hda_intel is loaded using ```
lsmod | grep snd
```5.
Check what device number and card number your HDMI is using ```
aplay -l
``` this gave me that my card was 0, and device was 7
 
6
open gedit with the gksu gedit command, and Check to see if there is a file named asound.conf in your /etc/ folder, if it does, look for the pcm!default line, and change according to the code below.
if no such file exists write the following in an empty file:
```
pcm.!default {
type hw
card 0 #This is where you have to use the card number you got from step 5
device 7 #Use device number from step 5
}
```8.
Now save this file as asound.conf in /etc/

Reboot and hope it works :P (If not, you could try to run alsamixer again, and try unmuting the four channels that appear under HDA Nvidia card again.)
 
I'm new to both Linux and posting stuff on forums, so just bear with me:)
Hope this might help someone away from the agony I've experienced the last two weeks.

---

### Post by BarryDocks on 2011-10-08
I have used the simple fix to get sound over HDMI for my GF210 on ubuntu 11.04:

[http://whyareyoureadingthisurl.wordpress.com/2011/09/17/nvidia-geforce-210-on-ubuntu-11-04/]("http://whyareyoureadingthisurl.wordpress.com/2011/09/17/nvidia-geforce-210-on-ubuntu-11-04/") 
Remove old drivers:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

Here's a summary:
Download Nvidia from Ubuntu X Swat and keep them upto date by adding the ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get -y install nvidia-current nvidia-settings
```

Then reboot:
```
sudo reboot
```
 
Every thing should work if you select the correct ouput source from the sound preferences.:P

---

