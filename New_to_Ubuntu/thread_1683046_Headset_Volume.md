---
title: "Headset Volume"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2011-02-06
I'm running Ubuntu 10.10 Desktop Version.
I plugged in my Logitech ClearChat Pro USB Analog Stereo headset. At first it didn't work, but then I got it to work via PulseAudio Volume Control. However, now the volume is seriously low, even if Volume Control has it set to max. When I open sound preferences and switch to my computer's speakers, every thing's much louder.
The headset has a switch for selecting between music, gaming, or online calls, but it has not made a difference.
It would be very nice if someone can help.

The attachment is the screenshot of my Output volume on Sound Preferences and Volume Control.

---

### Post by 123456789123456789123456 on 2011-02-06
have you tried taking the volume for the usb device up to 200%?  that may work.  plus even though it seems that ubuntu reconizes the device, see if there is a newer driver out on the web for it.

---

### Post by AlvitrValkyrie on 2011-02-06
I can only set them to 130%
The headset works perfectly fine on the Windows computer in the house. What could the problem possibly be?

---

### Post by xayto on 2011-05-31
Hope you got this sorted, but I thought since I had the same issue I would post the solution I found here as this popped up first in google.

USB volume is dependent on ALSA and Pulse audio, so sudo apt-get gnome-alsamixer and adjust your USB Volume to suit.

---

### Post by Christopher V. on 2011-06-10
Hey xayto:

I've been having the same maddeningly frustrating problems with my Logitech Wireless G930. 

I have an extremely difficult time blocking out audible stimuli from other people of any kind while I'm working and without something of my own control playing in the background to block out any other noise (it turns into neutral white noise for me, making concentration possible). 

Your fix that you've provided has saved me a great deal of further frustration. Just wanted to let you know that thanks, as well as to add a public post that can be found through search for anyone else experiencing the same problem with this specific headset.

---

### Post by JrRRr on 2011-09-22
Yeah! That really solved my problem too.. ..thanks a bunch!

---

