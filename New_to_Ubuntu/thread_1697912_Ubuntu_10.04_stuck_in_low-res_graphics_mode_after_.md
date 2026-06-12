---
title: "Ubuntu 10.04 stuck in low-res graphics mode after messing with nvidia drivers"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Uhura on 2011-03-01
Hi, would appreciate any suggestions on how to fix the following;
   
  Brief summary; After messing about with the nvidia drivers in ubuntu 10.04, I’m now stuck in low graphics mode and can’t get back to normal graphics. 
   
  I’ve spent 2 solid days trawling the forums and have found several similar threads but they all differed on key points like they were booting from a CD, or were using a different OS. I tried several of the similar suggestions but nothing worked. I’m a complete noobie to linux so need idiot-proof explanations please. 
   
  More detail; Last week I got a zotac zbox hd-id11 and installed ubuntu 10.04 as the only OS. Installed xbmc and everything was working fine. However, the user manual for the zbox says “before you can make full use of the features of the zbox you need to update the drivers”, and they include a CD of drivers, which isn’t very helpful because a) its only valid for windows and b) I don’t have a CD drive installed and don’t have an external one either. But I was bugged by the idea that perhaps it would work even better if I updated the drivers.
   
  So after trawling the web for instructions on how to do it, I came across the following; 
  [http://www.contentwhores.com/wordpress/?page_id=484](http://www.contentwhores.com/wordpress/?page_id=484)
  which seemed perfect because they describe almost exactly the same hardware setup (except I don’t have an SSD). So I followed the instructions for “updating the drivers and patches”, skipped the bit about “enabling TRIM support for your SSD” and followed the instructions under “configuring the video”. After the final reboot, I got a message saying something about there being no graphics driver (sorry, I can’t remember the exact message, I’ve messed about with it so much since then) and did I want to start in low graphics mode. I clicked OK, then spent the last 2 days trying to fix it but just can’t get it back to normal.
   
  Things I’ve tried; 
  1) I tried undoing what I’d done by uninstalling and reinstalling the nvidia drivers several times via the hardware drivers screen, and using synaptic package manager. The hardware drivers screen tells me that “nvidia-current is activated but not in use”. I don’t know how to make it be in use. 
   
  2) I followed some instructions to update the nvidia drivers via the terminal, and also to reinstall ‘nouveau’. 
   
  3) The nvidia configurations page accessed from the admin menu jumps around all over the place when I try to click on things, and the highest option it has for setting the resolution is 600 x 400. 
   
  The strange thing is, at one point when I tried to start xbmc, I got the error message that xbmc needs a graphics driver that supports 3D, and couldn’t run without one. But the above fixes have obviously fixed something because xbmc now starts fine, and when I watch a movie using xbmc, the picture is ok (I don’t think its any different from before I messed with the drivers). But the rest of ubuntu is in permanent low-res mode, with big chunky letters and windows that don’t fit on the screen etc. This makes me think that the graphics driver IS working, but something’s wrong with the settings in ubuntu. I think I need a way of telling ubuntu to stop booting in low graphics mode, or to start using the nvidia driver????
   
  Hope this gives enough detail for somebody to suggest a solution. Obligatory system info below. Many thanks.
   
  Zotac Zbox HD-ID11
  NVIDIA ION2 chipset
  Intel ATOM D510 processor
  WD scorpio blue 2.5” 500GB HDD
  Kingston value DDR2 RAM 2GB
  Ubuntu 10.04 
  Connected to LCD TV via VGA cable and audio-out. 
  (hope this covers everything, please ask if I left something out)

---

### Post by nerdy_kid on 2011-03-01
that seems like a solid guide, perhaps the new kernel is giving you trouble.  Reboot the computer, and as soon as the screen goes black (after POST and all that, directly before the Ubuntu logo shows up) Start hitting <shift>.  Keep tapping it until the GRUB menu pops up.  You should see a long list of "Ubuntu Linux 2.6.35-25-generic" or something similar.  Hit the down arrow key twice, and then hit enter.  Let me know if it works then.

---

### Post by Uhura on 2011-03-01
Hi, thanks for responding so quickly. Well, hitting shift while its rebooting doesn't do anything so I tried delete instead; that got me to a list of 4 options including ubuntu linux generic etc. Hitting the down arrow twice gets me to the third option, which is a memory test. Is that right? Its running now, but seems to be taking a while (luckily i have the laptop as an alternative).

---

### Post by nerdy_kid on 2011-03-01
> **Uhura said:**
> Hi, thanks for responding so quickly. Well, hitting shift while its rebooting doesn't do anything so I tried delete instead; that got me to a list of 4 options including ubuntu linux generic etc. Hitting the down arrow twice gets me to the third option, which is a memory test. Is that right? Its running now, but seems to be taking a while (luckily i have the laptop as an alternative).

no, not the memory test.  Just turn the pc off via the power button to cancel that.  Strange, you should have several kernel versions installed.  Using synaptic, uninstall the 4 kernel .debs that the guide had you install. Dont reboot.  Then, install the "linux" package in synaptic, and make sure that "linux-headers-generic" and "linux-image-generic" are all installed.  Double check that you have a kernel install, you should have a package "linux-image-2.6.32-somenumber-generic" installed.  Make sure that it is!  Then open a terminal and do "sudo update-grub".  It should say "Found linux image" on the command line.  make sure that it does, wouldn't want to reboot without a kernel.  Reboot, and see if the nvidia driver is working.

---

### Post by Uhura on 2011-03-01
> **nerdy_kid said:**
>  Using synaptic, uninstall the 4 kernel .debs that the guide had you install. .

I don't think I actually installed the 4 kernel .debs, because they were in the "updating the kernel and enabling TRIM support for your SSD" section of the guide, and the guide says " If you’re using a standard hard disk then you can skip this section and go straight to ‘Configuring the video’", which I did. So if I'm right in thinking that's what youre talking about, then I didn't install any kernels.

Its really hard to do anything in synaptic because the window hops around all over the place whenever I try to click on anything, but linux headers generic and linux image generic are both installed. Linux-image-2.6.32-28-generic is also installed. I did sudo update-grub and got 'found linux image' like you said. I restarted, but it hasn't made any difference to the graphics. nvidia_current is still showing up as 'activated but not currently in use'.

---

### Post by nerdy_kid on 2011-03-01
> **Uhura said:**
> I don't think I actually installed the 4 kernel .debs, because they were in the "updating the kernel and enabling TRIM support for your SSD" section of the guide, and the guide says " If you’re using a standard hard disk then you can skip this section and go straight to ‘Configuring the video’", which I did. So if I'm right in thinking that's what youre talking about, then I didn't install any kernels.

Its really hard to do anything in synaptic because the window hops around all over the place whenever I try to click on anything, but linux headers generic and linux image generic are both installed. Linux-image-2.6.32-28-generic is also installed. I did sudo update-grub and got 'found linux image' like you said. I restarted, but it hasn't made any difference to the graphics. nvidia_current is still showing up as 'activated but not currently in use'.
ok, you mentioned the "enabling TRIM support for your SSD" in your first post so I thought you did it.

Please post /var/log/Xorg.0.log and /var/log/Xorg.1.log, if they are too big to upload them pastebin them:  [http://pastebin.com/](http://pastebin.com/)
Also, please post the resulting ~/modprobe.zip file:
```

zip ~/modprobe.zip -r /etc/modprobe.d

```

and lastly, please post the output of
```

lsmod

```

Thanks!

---

### Post by Uhura on 2011-03-01
Okay, here's the pastebin links:
[http://pastebin.com/ckC4crJB](http://pastebin.com/ckC4crJB)
[http://pastebin.com/qgge0Myh](http://pastebin.com/qgge0Myh)

No idea how to post the modprobe.zip file. I have a file called modprobe.d? Is that it? How do I post it? I didn't seem half as thick on windows!!!

The results of the other two are below:


zip ~/modprobe.zip -r /etc/modprobe.d
  adding: etc/modprobe.d/ (stored 0%)
  adding: etc/modprobe.d/blacklist-oss.conf (deflated 70%)
  adding: etc/modprobe.d/alsa-base.conf (deflated 73%)
  adding: etc/modprobe.d/blacklist-framebuffer.conf (deflated 60%)
  adding: etc/modprobe.d/blacklist-firewire.conf (deflated 44%)
  adding: etc/modprobe.d/blacklist.conf (deflated 50%)
  adding: etc/modprobe.d/blacklist-ath_pci.conf (deflated 27%)
  adding: etc/modprobe.d/nvidia-graphics-drivers.conf (deflated 46%)
  adding: etc/modprobe.d/blacklist-watchdog.conf (deflated 68%)
  adding: etc/modprobe.d/blacklist-modem.conf (deflated 35%)
  adding: etc/modprobe.d/libpisock9.conf (stored 0%)


 lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22005  2 
arc4                    1153  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
ath9k                 306138  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
joydev                  8740  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9961216  38 
psmouse                63245  0 
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
intel_agp              24375  0 
softcursor              1189  1 bitblit
usbhid                 36110  0 
hid                    67064  1 usbhid
serio_raw               3978  0 
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126528  3 ath9k,mac80211,ath
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31724  2 nvidia,intel_agp
led_class               2864  1 ath9k
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34108  0 
mii                     4381  1 r8169

---

### Post by Uhura on 2011-03-01
.

---

### Post by nerdy_kid on 2011-03-01
ok, so currently your nvidia driver 195.36.24 is being loaded by the kernel, and X11 is picking it up as well.  So, are you sure that that the driver is not "working"?  Try running 

```

nvidia-settings

```

That should give you access to the NVIDIA driver's settings, if it is loaded, which it looks like it is.  Check your resolution while you are in there, make sure it is what you want.

Other then that, run
```

sudo mv /etc/X11/xorg.conf
sudo nvidia-xconfig

```
(dont worry if the first command throws an error)

and reboot.  From the log files and outputs you posted, it looks like everything is working.

If you still want to post the modprobe.zip file, reply to this thread, and before you submit your message scroll down to "Additional Options" and hit manage attachments.  Then choose the file "modprobe.zip" in your Home folder.

---

### Post by Uhura on 2011-03-01
```
[QUOTE=nerdy_kid;10510024]ok, so currently your nvidia driver 195.36.24 is being loaded by the kernel, and X11 is picking it up as well.  So, are you sure that that the driver is not "working"?  Try running 

[CODE]
nvidia-settings

```That should give you access to the NVIDIA driver's settings, if it is loaded, which it looks like it is.  Check your resolution while you are in there, make sure it is what you want.[/CODE]Well, yes, its like I said, when I run xbmc, the picture seems fine. Its just everything else in ubuntu that's low res. The nvidia xserver settings , under server display configuration, only has the options of auto, 640x480, or 320x240. Nothing else. 

```
Other then that, run
[CODE]
sudo mv /etc/X11/xorg.conf
sudo nvidia-xconfig

```(dont worry if the first command throws an error)

and reboot.  From the log files and outputs you posted, it looks like everything is working.[/CODE]One of the times I rebooted, I was given the option to boot in low res  mode, or safe graphics mode or whatever, and it just seems to have stuck  on that option. 
Is there any way to tell ubuntu to boot in normal graphics mode? Or perhaps from BIOS?

---

### Post by Uhura on 2011-03-01
```

If you still want to post the modprobe.zip file, reply to this thread, and before you submit your message scroll down to "Additional Options" and hit manage attachments.  Then choose the file "modprobe.zip" in your Home folder.
```Here's the modprobe file, and a screenshot of the nvidia settings screen.

---

### Post by nerdy_kid on 2011-03-01
ah ok, so the problem is that you are using a CRT monitor which is not reporting its supported sizes to the NVIDIA driver.  Quick fix:
```

gksu gedit /etc/X11/xorg.conf

```

then search for the line " SubSection     "Display" ". 


You need to know the resolution that you want the system to run at.  So, say if it is 1280x800, then stick 1280x800 instead of RESxRES in the code below.
```

Modes      "RESxRES" "800x600" "640x480"

```

Stick the above in between the line you found and  "EndSubSection" in the file.  Hit save, and reboot.  It should work now.

---

### Post by Uhura on 2011-03-01
Just tried that but it hasn't made a difference! Its an LCD TV as opposed to a monitor, don't know if that makes any difference? Also, how do I know what res I want it to run at? I just went for 1280x800 like you said. The nvidia settings options are still same as before though, max 640x480. 
Before I messed with everything, it was recognising the TV with no problems and working fine. Right now it looks a bit like when you change the display settings in windows and get big clunky fonts and windows that don't fit on the screen.

---

### Post by nerdy_kid on 2011-03-02
> **Uhura said:**
> Just tried that but it hasn't made a difference! Its an LCD TV as opposed to a monitor, don't know if that makes any difference? Also, how do I know what res I want it to run at? I just went for 1280x800 like you said. The nvidia settings options are still same as before though, max 640x480. 
Before I messed with everything, it was recognising the TV with no problems and working fine. Right now it looks a bit like when you change the display settings in windows and get big clunky fonts and windows that don't fit on the screen.


Please post your /etc/X11/xorg.conf file

---

### Post by mick8985 on 2011-03-02
Just a thought. He installed the X-Swat ppa. Probably installed the brand new xserver and ended up with the same issue natty users were dealing with last week.

---

### Post by Uhura on 2011-03-02
> **nerdy_kid said:**
> Please post your /etc/X11/xorg.conf file

Hi thanks for sticking with on this problem!  :)  Thexorg.conf file isnt huge so I'll copy&paste below:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
Modes    "1280x800" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Uhura on 2011-03-02
> **mick8985 said:**
> Just a thought. He installed the X-Swat ppa. Probably installed the brand new xserver and ended up with the same issue natty users were dealing with last week.

I just did a search on those terms but didn't see anything that looked like my problem. If this is the problem, what would the solution be? Did it get resolved? 
(btw, she not he. understandable assumption tho!)

---

### Post by Uhura on 2011-03-02
Still not getting anywhere with this; I've now spotted a couple of threads with resolution issues in 10.04 and monitors not being detected. How can I get ubuntu to recognize the monitor? And is it possible there's an issue with the updated drivers, given that it was working fine before I made the changes? Does anyone have any other ideas??

---

### Post by nerdy_kid on 2011-03-02
> **Uhura said:**
> Still not getting anywhere with this; I've now spotted a couple of threads with resolution issues in 10.04 and monitors not being detected. How can I get ubuntu to recognize the monitor? And is it possible there's an issue with the updated drivers, given that it was working fine before I made the changes? Does anyone have any other ideas??

hmm, I missed the natty troubles.  I was hoping to get this working for you with the updated driver, but oh well.  To downgrade the driver and any other packages affected by your upgrade:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig

```
and reboot yet again.  That should do the trick, hopefully :D

---

### Post by Uhura on 2011-03-02
Thanks, I tried that but it hasn't made any difference :(. The only thing untoward that happened was, after the last command, i got the message; 

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

Dont know whether that matters at all?

Wouldn't it be quicker to drag all my files into a partition, and reinstall ubuntu using the disc image I used before, when everything was working? I spent all of last week copying all of my media to the HDD so not keen on losing it all.

---

### Post by nerdy_kid on 2011-03-02
Don't worry about your data, it's not going anywhere.  You also don't have to reinstall, you just need someone more experienced with the Xorg config/workings then I am.


One last thing you can try, and then I'm stumped and you'll have to wait for someone else to help.
Run:
```

gksu gedit /etc/X11/xorg.conf

```

and paste this:

```

Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
Option "DPMS"
EndSection


Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x800" "800x600" "640x480"
EndSubSection
EndSection

```



Does anyone else have any insight?

---

### Post by Uhura on 2011-03-02
IT WORKED!!!!!  Phew, I was close to giving up!

Nerdy_kid, you're a star! :KS   Thanks so much for sticking with it and figuring it out, I really appreciate the time you've spent. Its been a baptism of fire for me with ubuntu...hopefully things will go more smoothly now.

 I'm not really very clear on what it was that finally fixed the issue, whether it was just that last step or a combination of everything? I presume it was more than just changing the modes 1280x800 line because we did that before and it didn't work. Maybe the combination of undoing the previous updates and then changing the config file? Anyway hopefully if anyone else has the same issue they'll be able to make some sense of it all. 

Thanks again :)

---

### Post by nerdy_kid on 2011-03-02
> **Uhura said:**
> IT WORKED!!!!!  Phew, I was close to giving up!

Nerdy_kid, you're a star! :KS   Thanks so much for sticking with it and figuring it out, I really appreciate the time you've spent. Its been a baptism of fire for me with ubuntu...hopefully things will go more smoothly now.

 I'm not really very clear on what it was that finally fixed the issue, whether it was just that last step or a combination of everything? I presume it was more than just changing the modes 1280x800 line because we did that before and it didn't work. Maybe the combination of undoing the previous updates and then changing the config file? Anyway hopefully if anyone else has the same issue they'll be able to make some sense of it all. 

Thanks again :)


Great!  Phew, that was a close one, that was my last idea :D

I read in some googling that setting the horizontal sync in the Xorg file caused issues for other people with valid resolutions not showing, so thats what I removed in the config file I gave you.  When you updated your nvidia driver, it must have generated a new config file for you with horizontal sync values included, which messed things up.  You *should* be able to re add the xswat ppa and update the nvidia driver with no problems.  It might ask you if you want to overwrite any config files, just make sure you say NO :lol:

Have fun with Ubuntu, experiment, mess stuff up, and learn how to fix it!  Good luck!

---

### Post by Uhura on 2011-03-03
> **nerdy_kid said:**
>   When you updated your nvidia driver, it must have generated a new config file for you with horizontal sync values included, which messed things up.  You *should* be able to re add the xswat ppa and update the nvidia driver with no problems.  It might ask you if you want to overwrite any config files, just make sure you say NO :lol:

Have fun with Ubuntu, experiment, mess stuff up, and learn how to fix it!  Good luck!

Thanks! At least we now know what went wrong and what fixed it.  I think I'll save a backup copy of the config file, just in case. 

Just to check, IF i dare to update the nvidia driver again, what code should I use? Wouldn't like to risk following that guide again.

---

### Post by nerdy_kid on 2011-03-03
> **Uhura said:**
> Thanks! At least we now know what went wrong and what fixed it.  I think I'll save a backup copy of the config file, just in case. 

Just to check, IF i dare to update the nvidia driver again, what code should I use? Wouldn't like to risk following that guide again.

```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade

```
will give you an updated driver, if there is one available.

---

### Post by Uhura on 2011-03-03
> **nerdy_kid said:**
> ```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade

```will give you an updated driver, if there is one available.

Great stuff, I will try that.

Thanks again!

---

