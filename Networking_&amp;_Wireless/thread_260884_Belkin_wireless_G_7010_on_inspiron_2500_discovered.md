---
title: "Belkin wireless G 7010 on inspiron 2500 discovered something odd..."
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-09-19
Merely an odd observation, 

I finally got my belkin wireless G working using interfaces file with WPAPSK and static IP.

It was working for ages without issue until i tried to get my I810 video to support hardware open GL. I modified my Xorg.conf from this:

```
Section "Module"
	Load	"dri"
	Load	"extmod"
	Load	"ddc"
	Load	"i2c"
	Load	"GLcore"
#	Load	"dbe"
	Load	"glx"
	Load	"bitmap"
	Load	"freetype"
	Load	"type1"
	Load	"vbe"
	Load	"int10"
EndSection

```
to this:
```
Section "Module"
	Load	"ddc"
	Load	"GLcore"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	#Load	"pex5"
	#Load	"record"
	#Load	"xie"
	Load	"bitmap"
	Load	"freetype"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
	Load	"int10"
EndSection

```
also in screen section:
```
	Option		"Accel"

```

Ive tried this three times, and the same results each time. I dont get it though as i would have thought the video hardware is absolutely nothing to do with the pcmcia/network system??? 

However, the network card will not work with the second one. I dont know if its the accel line or the order in which im loading stuff but its definitely a problem on my laptop.

Thought id share this info incase anyone else has my laptop & card. I dont want to narrow it down/experiment any more than this incase i cock it up again!!

---

