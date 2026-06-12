---
title: "Problem with mouse + xorg"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Dohee on 2011-05-28
Hi, I'm having some problems getting my mouse to work properly. I'm using a fresh install of Ubuntu 10.10. My mouse doesn't work properly (RAT 3) which I have previously fixed by creating a xorg.conf file and Xmodmap using instruction from this thread [http://ubuntuforums.org/showthread.php?t=1698482]("http://ubuntuforums.org/showthread.php?t=1698482").

This worked fine on my wubi install (I'm now using a separately partitioned install) which was also 10.10. My previous install was 32-bit and I'm now using 64-bit. My problem is that whenever I boot the problem exists but when I restart the X-server it works perfectly. Any ideas on how to make it work on boot up?

xorg.conf:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "evdev"
	Option         "Name" "Saitek Cyborg R.A.T.3 Mouse"
	Option         "Vendor" "06a3"
	Option         "Product" "0ccc"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/input/event4"
	Option         "Emulate3Buttons" "no"
	Option         "Buttons" "7"
	Option         "ZAxisMapping" "4 5"
	Option         "ButtonMapping" "1 2 3 4 5 6 7 8 9 0 0 0 0 0"
	Option         "Resolution" "3200"
	# generated from default
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Xmodmap:
```
pointer = 1 2 3 4 5 6 7 8 9 0 0 0 0 0 0 0 0 0
```

---

### Post by Dohee on 2011-06-02
Bump. Any help would be great guys. Having to log on and off every time I reboot is really sucking :(

---

### Post by climhazzard36 on 2011-06-28
I had this problem myself:

First Delete that xmodmap file.

Then re-edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
and paste in:
```
Section "InputClass" 
  Identifier "Mouse Remap" 
  MatchProduct "Saitek Cyborg R.A.T.3 Mouse" 
  MatchDevicePath "/dev/input/event*" 
  Option "ButtonMapping" "1 2 3 4 5 6 7 0 0 0 0 0 0 0" 
EndSection

```

Then either restart x-server (ctrl + alt + backspace) or reboot


I'm not sure if you will have to delete the existing mouse profile as you already set buttonmapping on it. Try it without deleting first.
:)

---

### Post by Tekno.Statik on 2011-07-15
> **climhazzard36 said:**
> I had this problem myself:

First Delete that xmodmap file.

Then re-edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
and paste in:
```
Section "InputClass" 
  Identifier "Mouse Remap" 
  MatchProduct "Saitek Cyborg R.A.T.3 Mouse" 
  MatchDevicePath "/dev/input/event*" 
  Option "ButtonMapping" "1 2 3 4 5 6 7 0 0 0 0 0 0 0" 
EndSection

```

Then either restart x-server (ctrl + alt + backspace) or reboot


I'm not sure if you will have to delete the existing mouse profile as you already set buttonmapping on it. Try it without deleting first.
:)

FINALLY! After two .Xmodmap files deleted, and three xorg.conf THIS permanently fixed my problem!

My ubuntu now feels like a beast! lol

I recommend THIS solution to all of you who have the MADCATZ CYBORG RAT 3.

---

### Post by climhazzard36 on 2011-07-15
Glad it worked for you man, took me a while to figure it out too ^^

---

