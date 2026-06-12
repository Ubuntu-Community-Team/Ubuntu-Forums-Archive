---
title: "Choppy flash"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-26
I know this topic has been discussed before but after searching I still cant fix the problem with flash being very choppy. Other threads seemed to be specific to ati video cards and flash only being choppy in fullscreen. I have an nVidia card and flash is choppy no matter what size its playing in.

-------------------------
**system details:**

[I]Intel core 2 duo 2.53Ghz
4Gb memory
nVidia 9800GS 512m[/I]b
--------------------------

I have the latest version of adobe flash.


This is the output of **/etc/X11/xorg.conf**  (I'm using a laptop, maybe thats why theres not much in there?)

```

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
```

I would really appreciate some help with this.

---

### Post by shadow120 on 2009-10-26
have you installed ubuntu-restricted-extras

---

### Post by macaholic on 2009-10-26
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
There's a Flash Optimization section, hopefully that helps!

---

### Post by Loki57701 on 2009-10-26
@shadow120: Yes I installed ubuntu-restricted-extras

@macaholic: Thanks, I'll check that out.

---

### Post by MelDJ on 2009-10-27
> **macaholic said:**
> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
There's a Flash Optimization section, hopefully that helps!

+1. there are many good solutions there

---

