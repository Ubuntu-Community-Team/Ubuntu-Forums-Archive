---
title: "Font artefacts Ubuntu 9.04"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by FreewheelinFrank on 2009-05-21
I'm getting font artefacts on this computer (see screen shot).

They usually only last for a fraction of a second before disappearing but sometimes persist. They've appeared in Firefox and Opera, and also in Ubuntu menus, I think, but much less frequently. The artefacts appear frequently on some web sites but never seem to appear on others.

I don't have the same problem on another computer so I assume it's hardware related.

I'd like to report the bug but I'm not sure to whom. I tried Googling but couldn't find anything similar.

Anybody have any idea who the bug belongs to?

---

### Post by kerry_s on 2009-05-21
try clearing your cache.

---

### Post by nhasian on 2009-05-21
it could be the video driver or bad video memory (less likely).  can you try a different video driver?

you can see what kind of video card you have and what driver your using with the terminal command:

```
lshw -C display
```

---

### Post by FreewheelinFrank on 2009-05-21
Here's the output. I'm using the open source driver. I forgot to mention that this problem only appeared after upgrading to 9.04.

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility U1
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=66 mingnt=8
```

---

### Post by FreewheelinFrank on 2009-05-21
> **kerry_s said:**
> try clearing your cache.

That didn't help, but thanks anyway.

---

### Post by FreewheelinFrank on 2009-05-21
Another example, this time from the BBC website.

---

### Post by FreewheelinFrank on 2009-05-21
It seems to be something to do with subpixel smoothing and or hinting.

I notice subpixel smoothing was enabled by default in 9.04.

[http://brainstorm.ubuntu.com/idea/17788/](http://brainstorm.ubuntu.com/idea/17788/)

I've just tried disabling sudpixel smoothing and hinting and re-enabling and the problem seems to have gone away- let's see if it survives a reboot.

I had subpixel smoothing and hinting enabled before, so 9.04 must have buggered up the settings somehow.

---

### Post by FreewheelinFrank on 2009-05-21
The artefacts are back!

Who do I report bugs in subpixel smoothing to????

---

### Post by nhasian on 2009-05-22
did you try the restricted driver for your ati card yet?

---

### Post by chrisod on 2009-05-22
I had the same problem with 8.10 and 9.04 and never could figure it out. I went back to 8.04 and that particular machine as the problem did not occur there.There are a couple of suggestions in this bug report. None of them worked for me. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)

---

### Post by FreewheelinFrank on 2009-06-02
> **nhasian said:**
> did you try the restricted driver for your ati card yet?

This is a very old machine and there is no option to use a restricted driver.

---

### Post by FreewheelinFrank on 2009-06-02
> **chrisod said:**
> I had the same problem with 8.10 and 9.04 and never could figure it out. I went back to 8.04 and that particular machine as the problem did not occur there.There are a couple of suggestions in this bug report. None of them worked for me. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)

This bug doesn't seem exactly the same as mine- I'm submitting a new bug report.

---

