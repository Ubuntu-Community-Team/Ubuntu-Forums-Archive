---
title: "[SOLVED] Resolution/Low Graphics mode Problems"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by DeLaney on 2008-12-31
Alright, so for Christmas I got a 22 inch Philips Brilliance monitor, and it's beautiful. My only problem is that I can't get a resolution that works. At first it used my old screen's resolution which was 1024 x 720 (I think?). I tried various methods to fix this problem (anything I could find on the forums) and after a couple methods I ended up stuck in Low Graphics mode, at a 800 x 600 resolution. Can anyone help? Here's a list of things I've done so far...

System->Preferences->Screen Resolution
gksu displayconfig-gtk (from command line)
sudo xrandr (from command line)
gksu gedit /etc/X11/xorg.conf (Alt-F2)

It's possible I screwed something up somewhere on those above methods, although I think I followed the instructions correctly. I am relatively new to Linux, as I've used it for a while, but know little about it, besides the extreme basics.

---

### Post by mikewhatever on 2008-12-31
Try <sudo dpkg-reconfigure -phigh xserver-xorg> without the brackets. What resolution do you want to use?

---

### Post by DeLaney on 2008-12-31
Do I put that into a command line or Alt F2? Also, I'd like to use 1680 x 1050.

---

### Post by mikewhatever on 2008-12-31
> **DeLaney said:**
> Do I put that into a command line or Alt F2? Also, I'd like to use 1680 x 1050.

Applications->Accessories->Terminal.
Can you also post the outputs of <sudo xrandr -q>,
and <sudo lshw -C display>.

---

### Post by DeLaney on 2008-12-31
sudo dpkg-reconfigure -phigh xserver-xorg comes out with a message saying: xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081231232417

The results of sudo xrandr -q are: Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        73.0* 
   640x480        73.0 

And the results of sudo lshw -C display are:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list
       configuration: latency=64 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8

---

### Post by Bigbob22 on 2008-12-31
Reboot.
Boot into Recovery Mode.
It will boot on and give you the list of choices.
Choose the option to fix your X-server.

Try using the screens and graphics program if that doesn't work. Go to System>Preferences>Main Menu
Then go select other and check screens and graphics, if downloaded.
If it isn't downloaded go to add/remove and search screens and graphics and download.

---

### Post by mikewhatever on 2008-12-31
What version of Ubuntu do you use? Try checking under System->Admin->Hardware Drivers for a graphics driver for you card. Is Radeon 9600 the correct model?

---

### Post by DeLaney on 2008-12-31
Alright, I'll give recovery mode a shot. 

I run Hardy Heron, and Radeon 9600 is the correct model.

---

### Post by DeLaney on 2008-12-31
Thanks! Booting into recovery mode did the trick. I clicked fix Xserver, and got this message; xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20081231232417 

After trying it a couple of times I just decided to try to let it boot and try something else. When it loaded, it did so at the correct resolution. I restarted and booted from normal, and it's still at the correct resolution, so I think it's fixed. Thank you! 

Out of curiosity, what did all of this do/mean?

---

