---
title: "NvTv: no supported video card found"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by maryalesia on 2010-04-02
Aaaaaand I'm back. 

Okay, so I think that Nvidia might have an evil plan to ruin my life, BUT I could be wrong. 

Here are my symptoms, doctors:

1. When setting up my monitors in Nvidia X server settings, I am unable to save my settings to X config file. I get this error message : "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

2. While trying desperately to stop screen tearing (only happens when I have my desktop cloned onto my LCD), I downloaded NvTv (I'm not sure if it would have helped, but I try). NvTv TV out will not open. In terminal, all I get is this:
"mary@ubuntu:~$ nvtv
Fatal: No supported video card found."

3. SO I checked the Nvidia website to see what the new driver is, and it is not the one that Ubuntu recommended in hardware drivers (version 185). The one online is, like, 196.-something. That's why I downloaded EnvyNG, thinking that maybe it would give me the option to download the new driver. Lo and behold, EnvyNG won't open, either. Not from clicking on it, not from using terminal. No error message from this one. 

And, In case you need it, this is the code that I got from my Xorg.config file:

mary@ubuntu:~$ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


-- I'm sensing that this is way shorter than it should be.

Thankyou all for being awesome and linux-savvy, and I apologize if this is a common problem you hear all the time.

---

### Post by maryalesia on 2010-04-02
Aaaaaand I'm back. 

Okay, so I think that Nvidia might have an evil plan to ruin my life, BUT I could be wrong. 

Here are my symptoms, doctors:

1. When setting up my monitors in Nvidia X server settings, I am unable to save my settings to X config file. I get this error message : "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

2. While trying desperately to stop screen tearing (only happens when I have my desktop cloned onto my LCD), I downloaded NvTv (I'm not sure if it would have helped, but I try). NvTv TV out will not open. In terminal, all I get is this:
"mary@ubuntu:~$ nvtv
Fatal: No supported video card found."

3. SO I checked the Nvidia website to see what the new driver is, and it is not the one that Ubuntu recommended in hardware drivers (version 185). The one online is, like, 196.-something. That's why I downloaded EnvyNG, thinking that maybe it would give me the option to download the new driver. Lo and behold, EnvyNG won't open, either. Not from clicking on it, not from using terminal. No error message from this one. 

And, In case you need it, this is the code that I got from my Xorg.config file:

mary@ubuntu:~$ cat /etc/X11/xorg.conf

Section "Screen"
Identifier	"Default Screen"
DefaultDepth	24
EndSection

Section "Module"
Load	"glx"
EndSection

Section "Device"
Identifier	"Default Device"
Driver	"nvidia"
Option	"NoLogo"	"True"
EndSection


-- I'm sensing that this is way shorter than it should be.

Thankyou all for being awesome and linux-savvy, and I apologize if this is a common problem you hear all the time.

---

### Post by cariboo on 2010-04-04
Please don't create multiple threads on the same subject, I have merged your two threads.

---

