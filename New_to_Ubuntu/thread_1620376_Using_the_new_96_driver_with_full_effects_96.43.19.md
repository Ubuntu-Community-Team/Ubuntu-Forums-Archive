---
title: "Using the new 96 driver with full effects 96.43.19"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by JohnCUbu on 2010-11-13
I just wanted to help out others who wanted to get 3d effects working and need the 96.43.xx(96.43.19) driver to do it. I read so many posts and got such good help I want to try to help some other noob like myself.
I added deb [http://ppa.launchpad.net/dajhorn/nvidia-96/ubuntu](http://ppa.launchpad.net/dajhorn/nvidia-96/ubuntu) maverick main to my repositories. and downloaded everything that had a 96 in it :)
I removed nouveau with
sudo apt-get --purge remove xserver-xorg-video-nouveau I also took some steps I may have not needed to like I added blacklist nouveau to my blacklist file. I also did 
sudo nvidia-xconfig.
 I rebooted. and the driver was active but not in use. Plus right clicking the desktop wouldn't bring up a context menu. But I could see settings in my nvidia Settings app for once. So I looked further and found out I had to add :
Option "AddARGBGLXVisuals" "True"
 to my screens section of my xorg.conf file with 
sudo gedit /etc/X11/xorg.conf
 (remember the capital X11 or you get an empty file opening) I also read I could add it to devce section but I put it in my screen subsection. I then disabled and reenabled the driver in 'addition drivers' and rebooted. I started up with full effects!! Did't even have to enable them! I'm sure I added steps that may have not been needed and maybe this won't help everyone. I have an old geforece4 420 so if I can get full effects so can anyone :P
(kinda scared to reboot I've been working on this for hours everyday for weeks haha)

---

### Post by neilhnz on 2010-12-04
Thanks JohnCUbu,

I must have read through hundreds of forum messages before I stumbled onto yours.

I now have the Nvidia driver working but there is a black strip down the side of the screen. Something that I am sure can be fixed.

Thank you for your post. It was most helpful.

Neil...

---

### Post by JohnCUbu on 2010-12-05
You're welcome. Just trying to give back. I hope I did't add a step or something that caused that black stripe but I wanted to include all the steps I took to make it work for me. Good luck. Maybe its a resolution setting in the nvidia manager.

---

### Post by Graham1 on 2010-12-14
Thanks JohnCUbu

Worked a treat on my HP TC100 tablet (Nvidia GeForce4 420 Go 32M).

:)

---

