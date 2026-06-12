---
title: "Well Pleased"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Thameslink on 2008-12-20
I've switched my laptop over to Ubuntu 8.10 now and I'm very happy with the results. I ran a live CD off the front of a magazine, saw that I could connect to the wireless network and tried a dual boot windows install. It didn't quite work out, I'm not sure why but I had 0 bytes HD space available in ubuntu despite having plenty of disk space anyway. I thought screw it and got rid of windows altogether.
Good call.
Pretty much everything worked straight off. despite not being able to run windows aero, I can use all the features of compiz and my desktop is a lot smarter. It's got a crappy Intel GMA still and runs up to 25 desktops in a deformed cube without breaking sweat. it boots up in under 2 minutes and shuts down in under 1 minute.
It's got 2gb of ram in it I've not seen it go over 30 percent usage yet.
And It runs almost every program I need.
I've got a couple of minor issues if anybody could point me in the right direction it would be appreciated.

It's one of these.

[COLOR="DarkOrange"]Sony Vaio VGN-N38Z/W Full Specification
Processor
Clock speed 	1.66 GHz
Processor type 	Core 2 Duo T5500
Processor manufacturer 	Intel
RAM
RAM installed 	2048 MB
Max supported RAM 	2 GB
RAM technology 	DDR2
Storage Hard Drive
Hard drive type 	SATA 5400 rpm
Hard drive size 	160 GB
Optical Storage
CD / DVD type 	DVD±RW Super Multi Double Layer
CD / DVD read speed 	CDx24, CD-Rx24, CD-RWx24, DVDx8, DVD-R DLx6, DVD-Rx8, DVD-RWx6, DVD+R DLx6, DVD+Rx8, DVD+RWx8, DVD-RAMx5
CD / DVD write speed 	CD-Rx24, CD-RWx16, DVD-R DLx4, DVD-Rx8, DVD-RWx6, DVD+R DLx4, DVD+Rx8, DVD+RWx8 , DVD-RAMx5
Interfaces / Networking
USB 	2
Firewire 	1
PC Card 	1
Ethernet 	Yes
Infrared 	No
Bluetooth 	No
Wireless networking 	Yes
Modem 	No
Video Output
Graphics processor 	Intel GMA
Video outputs 	VGA
Display
Display technology 	X-Black TFT
Display diagonal size 	15.4 in.
Maximum resolution 	1280x800 pixels
Audio
Soundcard 	Realtek High Definition Audio
Audio inputs/outputs 	Headphone, microphone[/COLOR]

When the laptop goes to sleep after being inactive for a while it is unable to reconnect to the wifi without a full power off and restart. It can see the network and attempts to connect but it just keeps aking for the key and dosn't work.
It's no biggie as it's so quick to restart but still....

Umm it won't auto detect the headphones, I ve worked out how to get sound through just the headphones but I want it to just know when I've plugged them in.

Wicked software.:guitar:

Jake

---

### Post by matmatmat on 2008-12-20
When it asks you for the key do you just click ok, accept or whatever or do you re type the key?

---

### Post by Thameslink on 2008-12-20
I just click OK, I guess I should try retyping it huh?

---

### Post by matmatmat on 2008-12-20
Yep!
If that doesn't work then I have no idea! :o

---

### Post by mapes12 on 2008-12-20
Sometimes, the default wifi handler in Ubu, **Network Manager**, throws up some issues. Although to be far it is much better these days than it used to be. As an alternative try out [WICD]("http://wicd.sourceforge.net/") and see if that helps.

---

### Post by MaindotC on 2008-12-20
I've had similar issues w/ my T60.  I just disable sleep and if you want to suspend, use:
```

sudo ifdown wlan0

```
or
```

sudo ifconfig wlan0 down

```
or whatever is the name of your network interface.  When you resume from suspend, use the same command but replace "down" with "up".  I haven't had any problems w/ suspend since the latest kernel.

---

