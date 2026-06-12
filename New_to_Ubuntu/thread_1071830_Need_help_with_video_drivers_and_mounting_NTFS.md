---
title: "Need help with video drivers and mounting NTFS"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by jarhead8286 on 2009-02-16
So I finally took a plunge and installed Ubuntu using Wubi on my old Dell Dimension 4550.  I have 2 questions:

1. I want to mount an NTFS partition automatically each time I boot.  I have Googled the question and entered a line into fstab file but the partition does not mount.  Running the command manually from terminal works.

mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

This is how I added it to fstab file:
/dev/sda1 /media/windows ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0

2. I can only go as high as 800x600 for resolution.  My guess is that I have to install the drivers for ATI Rage 128 Ultra video card.  Can someone please point me to where to get the drivers and how to install them.

I am a complete newbie and will require a step-by step.  TIA.

---

### Post by malathion on 2009-02-16
To install drivers:

```
$ sudo apt-get install envyng-gtk
$ sudo envyng -t
```
And follow the instructions.

---

### Post by jarhead8286 on 2009-02-17
malathion,
Thanks for answering one of my questions; I will give it a go once I get home.

Can anyone please help with my 1st question.

---

### Post by jarhead8286 on 2009-02-17
Followed malathion's instruction and the package was installed.  From the menu I selected to install ATI drivers and restarted as was recommended.  Still the display is crappy and won't go above 800x60.

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

---

### Post by jarhead8286 on 2009-02-18
Anybody can offer assistance?

---

### Post by element_G on 2009-02-18
for ntfs:

```
sudo apt-get install ntfs-config
sudo ntfs-config 
```

and follow the instructions ;)

---

### Post by jarhead8286 on 2009-02-19
> **element_G said:**
> for ntfs:

```
sudo apt-get install ntfs-config
sudo ntfs-config 
```

and follow the instructions ;)

element_G,
Thanks for the help with NTFS question.

Still having problems with my display though.  Is my ATI video card not the best choice for Ubuntu?  If I were to swap it out, which one should I choose (considering the age of the PC)?

---

### Post by element_G on 2009-02-19
backup your xorg.conf first

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

in your /etc/X11/xorg.conf (open as root :  sudo nano /etc/X11/xorg.conf  OR gksu gedit /etc/X11/xorg.conf )

under the called Screen insert this

```
Option "metamodes" "1920x1600; 1680x1050"
```and use the appropriate resolutions for your monitor

then save the file, and restart X ( Ctrl Alt Bcksp )

---

### Post by jarhead8286 on 2009-02-19
element_G,
Thank you for your quick reply; I will try it later tonight.

---

### Post by egalvan on 2009-02-19
> **jarhead8286 said:**
> So I  installed Ubuntu **using Wubi** on my old Dell Dimension 4550.  I have 2 questions:

2. I can only go as high as 800x600 for resolution. I have to install drivers for ATI Rage 128 Ultra.

I am a complete newbie 

First, Welcome to the club. :)

Second, Wubi at times has problems with video. 
This may be one of them.

Third, how much RAM does that dinosaur video have? :)
Yes, I have and use some of those... and even older video cards.
My favorite is a Rendition card.
Stunning, gorgeous colors.
Crisp, crystal-clear text.
At 800x600. :)
It's all the RAM it has.

Rage 128 is a fine platform, but it IS dated.
You may be asking too much.
I think 1024x720 (or so) should be possible.
I DON'T think it has the RAM for **"1920x1600; 1680x1050"**

---

### Post by egalvan on 2009-02-19
Hey, I just remembered, the ATI Rage 128 Ultra video card has hardware-based mpeg acceleration.
Meaning you can watch DVD's with it, with great results.
CPU does not matter.

And for those who do not believe,
I used to watch commercial DVD's on an ancient computer;
300A CELERON :biggrin:, 128M, hardware-based mpeg decoder card, and a pre-RPC DVD drive.
Sound-Blaster audio, with headphones.
21" Sony Trinitron CRT.
No skips, artifacts, or other problems.

---

### Post by jarhead8286 on 2009-02-19
> **egalvan said:**
> First, Welcome to the club. :)Thanks and hope to stick around.
> **egalvan said:**
> Third, how much RAM does that dinosaur video have? :)Not sure... will check when I get home.
> **egalvan said:**
> Rage 128 is a fine platform, but it IS dated.
You may be asking too much.
I think 1024x720 (or so) should be possible.
I DON'T think it has the RAM for **"1920x1600; 1680x1050"**If I can get it to display 1024x768, I'll be happy. ;)

Not sure if it's worth buying a new (used) video card for this system.

---

### Post by jarhead8286 on 2009-02-19
> **egalvan said:**
> ... how much RAM does that dinosaur video have? :)

Rage 128 is a fine platform, but it IS dated.
You may be asking too much.
I think 1024x720 (or so) should be possible.
I DON'T think it has the RAM for **"1920x1600; 1680x1050"**

OK... I checked the video card and it has 32MB RAM.  I tried everything suggested here to change the resolution, but nothing has worked so far.

Question:  Do I have to specify the monitor brand in the xorg.conf file?

---

### Post by element_G on 2009-02-20
> **egalvan said:**
> First, Welcome to the club. :)

Second, Wubi at times has problems with video. 
This may be one of them.

Third, how much RAM does that dinosaur video have? :)
Yes, I have and use some of those... and even older video cards.
My favorite is a Rendition card.
Stunning, gorgeous colors.
Crisp, crystal-clear text.
At 800x600. :)
It's all the RAM it has.

Rage 128 is a fine platform, but it IS dated.
You may be asking too much.
I think 1024x720 (or so) should be possible.
I DON'T think it has the RAM for **"1920x1600; 1680x1050"**

sometimes I amaze myself with how smart I am
#-o:-#\\:D/:lol:

---

