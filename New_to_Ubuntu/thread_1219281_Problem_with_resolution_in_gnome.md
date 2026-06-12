---
title: "Problem with resolution in gnome"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by KakDela on 2009-07-21
I booted up Ubuntu for the first time yesterday off of a live usb, and found that there was a problem with the resolution; the only options offered in System>Preferences>Display were 800x600 and a lower one, while my display in 1280x800 (There are no problems with the driver, and it works fine in vista). I tried looking for help online, but didn't really get anywhere, since this is my first experience with linux and I don't know terminal commands. I tried editing the xorg.conf file, but the only thing below the comments at the top were section headings. I was thinking about installing kde, but decided to go the the forum first.

I'll be learning how everything works a bit later on; for now i just need the steps to fix my resolution so that I can use ubuntu without my eyes hurting.

---

### Post by devildoc5 on 2009-07-21
ok what version of Ubuntu are you using?  What video card do you have?  Have you tried going to System>Preferences>Appearance?

---

### Post by Temposs on 2009-07-21
It's likely an issue with your video card. Please tell what kind it is, and also go to System->Administration->Hardware Drivers and tell what it says there.

We are here to help, and welcome to Ubuntu :-)

---

### Post by KakDela on 2009-07-21
I am using the latest Ubuntu version, 9.04. My video card is NVIDIA GeForce 7150M / nForce 630M. I have gone to System>Preferences>Appearance; there are no resolution settings there. I'll check System->Administration->Hardware Drivers in a sec; I am using vista right now and have to reboot.

---

### Post by devildoc5 on 2009-07-21
sorry I was mistaken about that earlier post it should be System>Preferences>Display.  However since you have an NVIDIA card you need to go to System>Administration>Hardware Drivers and ensure that you have the NVIDIA Restricted Drivers active.

---

### Post by KakDela on 2009-07-21
Yes, System>Preferences>Display was the first place I went, but, as I said, it only offers two resolutions (800x600 and a lower one). In System>Administration>Hardware Drivers, it is offering me to activate a "NVIDIA accelerated graphics driver (version 180)" among others; I tried to activate it, and it told me that I needed to reboot for it to take effect, but when I rebooted it said that the driver was still not active.

---

### Post by devildoc5 on 2009-07-21
well that is weird...try running this in a command line and see if that makes any difference:

```

sudo /usr/bin/jockey-gtk

```

try changing it that way.....maybe it has some weird root priveleges or somethign attached to it.  Although I did not have to do this for mine.

---

### Post by KakDela on 2009-07-21
I managed to activate the driver (not sure how, it activated when I just waited instead of rebooting. I didn't need to use the terminal.). Now, if I go to System>Preferences>Display, I get the following message:

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?If I push "no", it brings me back to the normal display properties, but with those same two choices for resolution. If I push "yes", it says: 

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by devildoc5 on 2009-07-21
ok so the driver itself is active correct?  

if this is the case you need to make sure that you also have the nvidia-settings verify this by going to >System>Administration>NVIDIA X Server Settings

if you do not have this then make sure that you have the restricted repositories enabled in System>Administration>Synaptics Package Manager click on Settings and go down to Repositories click on the tab marked "Third-Party Software" and check the box that says "Officially Supported" once that is done open a terminal and run 
```


sudo apt-get update && install nvidia-settings

```

---

### Post by KakDela on 2009-07-21
I have realized that all settings and data is reset when I restart ubuntu. I'm sure this has something to do with the fact that I am running ubunto off of a live USB, but I have no idea what to do. This should probably be sorted out first, since further changes may require rebooting.

---

### Post by devildoc5 on 2009-07-21
ok now we are getting beyond my level of knowledge (if I ever really had any to begin with).  I know there is an option in DSL and Puppy linux that will save a SMALL configuration file to your hard drive and allow the live cd to interface with that when booting to allow you to keep your system configuration.  I do not know if this is possible, nor how to do it in Ubuntu though........

Just out of curiosity, is there a reason for not installing it to dual-boot, or even just completely get rid of the other os?

Not trying to force you into anything but that still is a viable option, especial dual-booting.

Also I could have sworn that I saw somewhere when I was first messing around with ubuntu, something that would allow you to "remaster a live cd" or something to that effect.  I am fully installed and dont even have a live cd anymore (all my friends took mine) so I couldn't tell you how to get there or anything like that.........

OR live USB as the case may be

Sorry for the lack of help.......................

---

### Post by KakDela on 2009-07-21
Although I intend to switch over to Linux eventually, I don't want to get rid of windows until I am sure I can get around Linux, and have installed all of my programs on Linux (and have gotten the display to a non-eyesore state). I didn't want to dual boot yet because several people told me that dealing with partitions is a hassle and that there is a chance of system failiure, and I was having problems with creating a recovery disc for vista.

So I just decided to boot from USB for now. I'll make a separate thread about this new problem, which seems to be more straightforward than the first one. I'll try what you suggested for now, and see if I can get away with not rebooting.

And thanks a lot for your help anyway.

---

### Post by devildoc5 on 2009-07-21
Yeah I heard all about those same problems.  What I did was to burn anything I absolutely COULD NOT live without on a thumb drive and a DVD (lots of stuff) and then defragged and try a "guided install" or something like that from the live cd.  It worked fine as far as the install goes, still had a few kinks I had to work out of th Ubuntu side, but my vista side has been fine ever since.

Then again I also have a complete partition that is off limits somehow to almost everything, that has a restore image on it, so if I needed to restore my system to factory I just had to push f9 plus f4 during bios load screen.  Like I said though everything went good.  I have not even used vista once, except to get some of my photoshop brushes moved over to GIMP and to play BattleField2..........

---

### Post by Crunchy the Headcrab on 2009-07-21
You might give Fedora 11 a try.  Unlike Ubuntu it automatically uses my default (strange) resolution.  1366 x 768.  I think they offer a live disk.  (of course I installed Nvidia anyway so that I can use compositing, but that's a whole different matter).

---

### Post by KakDela on 2009-07-21
AHAHAHAHA!!! It works!!!

The hardware drivers window had told me that I needed to restart again, but for some reason I chose to log out; when I logged back in, tada! the resolution is fine, plus there are some cool minimizing animations.

now, if I go to the System>Preferences>Display window, it offers a lot of resolutions, including the right one which was set automatically when I logged in. However, the driver still says that i need to restart for it to activate...

Edit: I realized what happened, sort of. when i open "display" now, it still tells me that the driver doesn't have the right extension or whatever, but I I say yes, it no longer tells me about the X server, and when the settings window opens there are a lot of settings pertaining to the X server which weren't there before. So I guess the problem with the X server is fixed...

I'll reboot and see what works.

---

### Post by Crunchy the Headcrab on 2009-07-21
> **KakDela said:**
> AHAHAHAHA!!! It works!!!

plus there are some cool minimizing animations.

Those are called Desktop Effects.  System > Preferences > Appearance > Desktop Affects
You can enable a whole bunch if you install Compiz Manager (compiz is already on your disc, but the manager enables more control/effects).  That's probably a bit much for a live boot to handle though.

---

### Post by KakDela on 2009-07-21
thanks, but i'll deal with ubuntu first before deciding to install a different distro.

---

