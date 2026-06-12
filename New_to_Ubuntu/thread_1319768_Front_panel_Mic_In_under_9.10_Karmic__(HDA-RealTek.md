---
title: "Front panel Mic In under 9.10 Karmic  (HDA-RealTek ALC889A audio chip)"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by LarryJ2 on 2009-11-08
My front panel microphone input refused to function after I installed Karmic Koala 9.10 -64 bit amd version using this kernel.( uname -a => 2.6.31-14-generic #48-Ubuntu SMP).   This is what I did to fix the problem.  

1.  Install Alsa Utiltiies.  So in a terminal...
lj@lian:~$ sudo apt-get install alsa-utils

then in a terminal start the AlsaMixer utility.
lj@lian:~$ alsamixer

2. Look at the screen shot below titled AlsaMixer.png. Press  Tab  so that [Capture] (shown on the line labeled View)  is highlighted.

3. Then use the right arrow key to move right stopping at Front Mi(c) and Mic Boos(t) long enough to use the up/down arrow key to set each one to say 67. 

4.  Similarly, key right arrow to each of the three sliders labeled <Capture> (The sliders are labeled on the Item line (top left) as Capture, Capture 1 and Capture 2)  If at the bottom of each of these three sliders, the word CAPTUR is not showing in red,  hit the space bar when the <Capture> immediately below it is red.  This will unmute that slider.  When done, your alsa mixer display should resemble the screen shot below  AlsaMixer.png

5.  At the top right of your gnome desktop, you should see an icon that slightly resembles a speaker.  Right click on it and select Sound Preferences.  Refer to the screen shot below named  Sound Preferences-Input.png

6. Select the Input tab in the Sound Preferences window, Uncheck the box by Mute to the right of the Input Volume horizontal slider. 

7. In the Connector: Drop Down select Microphone 2. Apparently, Microphone 2 is the same as Front Mi in the AlsaMixer.  When you change the Connector selection, the first Front Mi/Input So slider in the AlsaMixer's  label changes to  Mic. Change it to Line-In and the first InputSo slider in AlsaMixer changes to Line. Try it.

8. Now bang or tap the microphone you have plugged into the front panel jack (The top stereo jack is the mic and the bottom is the headphone jack on my box).  Hopefully will see some response in the "Input Level" fake led display indicating your microphone is now functioning.  

All this pertains to my equipment detailed below. The other SoundPreference screen shots are just for reference. YMMV!

Larry

My equipment:
lj@lian:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f9100000-f9103fff

lj@lian:~$ sudo lshw -class system
[sudo] password for lj: 
lian                      
    description: Desktop Computer
    product: EP35-DS3R
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001D

---

### Post by vk7aaa on 2010-03-20
Thanks a lot, it was  great help. I did use only GUI and my microphone was working very intermittently. After re-adjusting it in terminal I gained full control of it.
Regards Andrew

---

