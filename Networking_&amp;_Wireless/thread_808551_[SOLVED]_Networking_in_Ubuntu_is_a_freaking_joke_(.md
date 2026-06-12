---
title: "[SOLVED] Networking in Ubuntu is a freaking joke (bcm43xx/rtl8139 not working)"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Bitch-Face Jones on 2008-05-26
Okay, so I'm trying to install Hardy Heron on an old HP dv1000 laptop.  I'd like to say that the installation went smoothly, but that's another thread (here's a hint - don't try to install from Windows, they haven't really worked the bugs out yet.)

After I finally managed to get everything installed, I noticed that I have no network functionality.  This laptop has a Realtek 8139 Ethernet adapter, and a Broadcom bm4306 Wireless adapter.  The Ethernet adapter is supposedly supported, the kernel module loads fine, but I can't even get a link-light from the thing when I plug it into my switch.  Okay, whatever, no biggie - instead of screwing with that I try to get the wireless connection working.  Several posts on the internet led me to believe that getting this to work would be as simple as enabling the non-free broadcom driver in the Hardware Drivers administration section.  Now, the Broadcom wireless adapter apparently needs some sort of proprietary firmware that can't be distributed with Ubuntu in order to operate.  OK.  The only problem is that when trying to enable the driver in Hardware Drivers, it tries to grab the firmware from the internet, which I currently don't have access to.  Great.  Well, b43-fwcutter is installed, anyway, so I just looked at /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh, downloaded the required files onto a usb drive, and just ran the commands from that script on the files on the usb drive.  I reboot, I see that the little light comes on for my wireless adapter (that wasn't happening before) and that the "Broadcom b43 wireless driver" is showing up as enabled and in-use in the Hardware Drivers.  Great!  I've done it!  But now it isn't finding any wireless networks, (don't get me started on how much the wireless setup interface sucks) and when I try to connect to my network manually by going to "Connect to Other Wireless Network", it just sits there saying it's getting 0% signal, basically the same **** that the wired ethernet connection was pulling.  Any ideas as to how I can fix this?  I'm pretty much at the end of my rope here.

---

### Post by Bitch-Face Jones on 2008-05-26
Okay, I got it working.  Even though the little wireless light was on, the wireless adapter was turned off.  I just hit the wireless button on my laptop again, and it started working.

---

### Post by Cap'n Skyler on 2008-05-26
glad you got it worked out.:popcorn:
how's the blood pressure? 

:lolflag:

---

### Post by Bitch-Face Jones on 2008-05-26
Oh, it's fine.  I manage it with medicatHHHHHHHHHNNNNNNNNNGGGGGG

---

### Post by Ripfox on 2008-05-26
This is exactly why people should do a little research before posting thread titles like this. This forum gets indexed by Google quite rapidly and it spreads fud when it was just ebkac.

---

