---
title: "Bluetooth no longer works"
date: 2023-01-06
forum: Networking &amp; Wireless
---

### Post by physicsisfun on 2023-01-06
Hi everyone, 

I need some advice on fixing my Bluetooth.

I run Ubuntu 18.04 on a laptop and usually use wireless headphones for sound.

One day the volume output of my headphones was strangely low even at max, and I could not get it back to the usual max levels. The sound output of the laptop itself remained normal. 
If I connect the headphones to another medium, say my phone, the sound works fine.

First, I followed the hints on this site:
[https://www.oodlestechnologies.com/blogs/how-to-fix-low-sound-issue-in-ubuntu-os/](https://www.oodlestechnologies.com/blogs/how-to-fix-low-sound-issue-in-ubuntu-os/)
The first two steps consisted of checking and re-installing Alsamixer (did not help).
In step 3, they recommend to install Ubuntu Audio Development Team Driver, so I entered the given commands:
```

sudo add-apt-repository ppa:ubuntu-audio-dev
sudo apt-get update
sudo apt-get dist-upgrade
```

Not only did this not help, but after a reboot, I could no longer connect any Bluetooth devices to the laptop. The devices are still visible in the Bluetooth settings, and even listed as "paired", but they can't be connected. Well, in the case of my smartphone, the connection lasts for a couple of seconds and then terminates. The headphones won't connect at all, the grey connection slider in the GUI will always slide back to the "off" position instantly.

Any help would be deeply appreciated!

PiF

---

