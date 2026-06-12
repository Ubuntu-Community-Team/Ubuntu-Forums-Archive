---
title: "Monitor not being detected"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by flyingdutchbird on 2009-05-27
Hi,

I'm a brand new user of Ubuntu and Linux as well for that matter. I installed ubuntu with practically no interference (had to set it to use basic graphics whilst installing) but I am facing an issue with my second monitor.  I have two monitors connected to my ATI X1300 graphics card (which has 1 VGA and 1 DVI output). When I go to System > Preferences > Display I only see one monitor. The smaller monitor, which is a bit rubbish, is the only one detected. Ideally I would love to use both, but even if there were a way for me to just use the DVI monitor I would be grateful... 

I understand the latest Catalyst driver does not support my card, due to the new xorg version, so I am running the Radeon driver. It works fine on my VGA monitor, correct resolution and everything, right out of the box, but the other monitor is not detected at all.

I am not looking to do any fancy stuff, just using this for web development (HTML, CSS, test web server), email and web browsing, so I don't need fast fps rates or 3D performance, just two screens...

Any help anyone could give would be much appreciated.

Thanks,
Karin

---

### Post by Jeff250 on 2009-05-27
This is a shot in the dark, but there is actually a third driver that you can try with your ATI card model.

Install the xserver-xorg-video-radeonhd package by typing:

```
sudo apt-get install xserver-xorg-video-radeonhd
```

Then, in /etc/X11/xorg.conf, type

```
sudo gedit /etc/X11/xorg.conf
```

and change where it says:

```
Section "Device"
        ...     
        Driver   "radeon"
```

to:

```
Section "Device"
        ...     
        Driver   "radeonhd"
```

Sadly, these drivers are beta quality, but it's worth a shot.  If they don't work out, you just have to change radeonhd back to radeon in xorg.conf.  Hopefully someone with more experience with ATI cards can comment on this thread.

---

### Post by flyingdutchbird on 2009-06-18
Hi Jeff,

Thanks for trying to help me with this issue. In my xorg.conf file the Devices is set to vesa. As soon as I change it to radeon and reboot, neither monitor works. I had to reboot again and get it to 'fix' my graphics driver, so it is now back as vesa. Really not sure why this is not working for me. The packages seem to all be installed, but I don't seem to be using the ATI driver at all? 

Very confused... am now thinking I should perhaps switch to a NVIDIA card...

Thanks again, if you or anyone else has any further ideas on what I could try please let me know.

Cheers,
Karin

---

