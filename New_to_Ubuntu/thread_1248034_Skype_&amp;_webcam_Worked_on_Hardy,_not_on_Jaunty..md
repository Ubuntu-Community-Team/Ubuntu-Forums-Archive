---
title: "Skype &amp; webcam: Worked on Hardy, not on Jaunty. Setup wrong?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-23
My webcam worked first time without any problems with Skype on Hardy.

Now, I've made a fresh installation of Jaunty (dual-boot with Hardy) on the same computer. The webcam doesn't work with Skype.

On Hardy: *Skype > Options > Video Deevices > Select webcam* reports that I have "Pixart PAC7311 (/dev/video0)".

On Jaunty: Skype reports that I have "USB Camera (093a:2600) (/dev/video0)". When I press the Test button, either nothing happens or Skype crashes.

I tried to test my webcam with cheese. Cheese starts up, thinks a bit, then crashes.

So, I'm guessing that somehow Jaunty has not recognised my webcam properly.

Any advice, anyone?

---

### Post by Codix121 on 2009-08-23
I don't think it's jaunty,
I think it's Skype,
The new version of Skype (Skype 2 I think) has had a lot of issues,
I also had to work around to get my Camera to work..

Is the model of your camera Pixart PAC7311?

Type in 

```
lsusb
```

in your terminal,
and post the results.
Thanks:)

---

### Post by Codix121 on 2009-08-23
Also, sorry for the double post do you have libv41-0 installed?
Search in your Synaptic and see if it's installed.

---

### Post by brookie on 2009-08-23
Here's what I had to use to get my webcam working in skype on intrepid. Hope this helps.
[http://ubuntuforums.org/showthread.php?t=1026188]("http://ubuntuforums.org/showthread.php?t=1026188")

---

### Post by Codix121 on 2009-08-23
Yeah I also had the same work around as brookie that works,
that's usually the problem since many Cameras use V4l but
Skype doesn't recognize v4l by default, so you need to create a seperate
bash file to load Skype using v4l.

The tutorial and link show you how to fix it,
however if this doesn't fix the issue,
Post your results on lsusb,
and I'll try my best to help.

---

### Post by Paddy Landau on 2009-08-24
> **Codix121 said:**
> Is the model of your camera Pixart PAC7311?
It says it's PCLINE, but I guess *lsusb* below will tell.

> **Codix121 said:**
> do you have libv41-0 installed?
Yes, it's installed.

> **brookie said:**
> [http://ubuntuforums.org/showthread.php?t=1026188](http://ubuntuforums.org/showthread.php?t=1026188)
Sadly, no luck with that. The results were identical.

> **Codix121 said:**
> I'll try my best to help.
Greatly appreciated!

For completeness, I've posted my lsusb below. However, I've decided that I'm getting too many errors with Jaunty, including slow response time. Thus, **I'm going to stay with Hardy until the next LTS (Karmic) is released.**

Thank you both for your time!

```
*$ lsusb*
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 093a:2600 Pixart Imaging, Inc. Typhoon Easycam USB 330K (newer)/Typhoon Easycam USB 2.0 VGA 1.3M/Sansun SN-508**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

