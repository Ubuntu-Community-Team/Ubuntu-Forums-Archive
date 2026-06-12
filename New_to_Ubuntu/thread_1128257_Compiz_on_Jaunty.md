---
title: "Compiz on Jaunty"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by theozzlives on 2009-04-17
I have a Dell Optiplex GX260 with an integrated Intel 82845G/GL[Brookdale-G]/GE GPU. On Hardy Compiz worked fine, on Intrepid I had to add the following to my xorg.conf:
```
Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

```

That code don't work on Jaunty and default dosen't let compiz work. It's my file, web, and print server so I don't use it much, but I'd like everything to work. Any ideas???

---

### Post by SketchyClown on 2009-04-17
Have you tried changing your **AccelMethod** to **"UXA"**??

Seems some people are having success with this with Intel integrated graphics.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360138](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360138)

HTH.

---

### Post by theozzlives on 2009-04-17
> **SketchyClown said:**
> Have you tried changing your **AccelMethod** to **"UXA"**??

Seems some people are having success with this with Intel integrated graphics.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360138](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360138)

HTH.

didn't work, I just get color lines before login

---

### Post by vertago1 on 2009-04-17
Is this in your xorg.conf file?

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by theozzlives on 2009-04-17
> **vertago1 said:**
> Is this in your xorg.conf file?

Section "Extensions"
Option "Composite" "Enable"
EndSection

Yes it's in xorg.conf and no that didn't work. It just goes to the wallpaper when I start compiz (all panels and windows dissapear). The only thing I can do is hard boot.

I might add my chip was blacklisted and I overrode it, but the modifications I made above in 8.10 made it work until 9.04.

---

### Post by theozzlives on 2009-04-18
Well I changed the driver from "intel" to "vesa" and took out the accel method. It booted 640x480, so I did xfix. There's gotta be a simple solution to this.... lets put our heads together.

---

### Post by theozzlives on 2009-04-18
I said before that with Intrepid I overrode compiz so it won't look at the blacklist. How do I take the chip off the blacklist, and will that help?

---

### Post by binbash on 2009-04-18
There is a thread opened by me at jaunty forums.There are a couple of ways to unblock the card.BUT THERE IS A BUG PENDING and it is blacklisted because of this.

---

### Post by theozzlives on 2009-04-18
I would like some help on this as I'll have to go back to Intrepid, and I don't want to. Jaunty is so much faster, even with ext3.

---

### Post by theozzlives on 2009-04-18
I have a Dell Optiplex GX260 with an integrated Intel 82845G/GL[Brookdale-G]/GE GPU. On Hardy Compiz worked fine, on Intrepid I had to add the following to my xorg.conf:
```
Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

```

That code don't work on Jaunty and default dosen't let compiz work. It's my file, web, and print server so I don't use it much, but I'd like everything to work. I've tried [this]("http://ubuntuforums.org/showthread.php?p=7097967#post7097967") so far. Any ideas???

---

### Post by pspsampsp on 2009-04-18
Use the Compiz-Check script and copy and paste the errors that it outputs. 

Open a terminal and use this command to get the script "wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check" (will download to your home folder)

Then use this command to make it an executable "chmod +x compiz-check".

Finally , Run the script with this command "./compiz-check"

Compiz-Check is from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) so do not thank me , thank the creator of the script

---

### Post by overdrank on 2009-04-18
Threads merged

---

### Post by theozzlives on 2009-04-18
> **pspsampsp said:**
> Use the Compiz-Check script and copy and paste the errors that it outputs. 

Open a terminal and use this command to get the script "wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check" (will download to your home folder)

Then use this command to make it an executable "chmod +x compiz-check".

Finally , Run the script with this command "./compiz-check"

Compiz-Check is from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) so do not thank me , thank the creator of the script

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

My chip was blacklisted and I overrode it

---

### Post by pspsampsp on 2009-04-18
after that did it then say something about your pci id being blacklisted ?

---

### Post by theozzlives on 2009-04-18
That was back in Intrepid, I got it working by editing my xorg.conf, but the same edits don't work with Jaunty. I think Ubuntu has something against Intel graphics (or me).

---

### Post by broecher on 2009-04-28
Hi, the only problem I have is I cant get livestation video to work at all, I don't really NEED compiz and didn't get far enough to even try it. I don't do any gaming.

Do you think my problem (below) is related to my 82845G/GL card? If I really want to use Jaunty is getting a different card a reasonable option???

[http://ubuntuforums.org/showthread.php?p=7171900#post7171900](http://ubuntuforums.org/showthread.php?p=7171900#post7171900)

---

### Post by theozzlives on 2009-04-29
I've given up on Intel chips, I got a nvidia on order.

---

### Post by broecher on 2009-04-30
so you think my problem sounds like a video card problem also??

---

### Post by theozzlives on 2009-05-01
> **broecher said:**
> so you think my problem sounds like a video card problem also??

Google compiz-check and follow the instructions to run it. If it asks if you want to see more info, say yes. If it's blacklisted, you decide if you want to override or not.

---

