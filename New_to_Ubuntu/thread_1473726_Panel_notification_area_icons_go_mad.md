---
title: "Panel notification area icons go mad"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by pi24 on 2010-05-05
Hello!

Sometimes the icons on the notification area gets mixed up, as you can see on the attached screenshot. The icons (applets) don't even work when this happens.

Does anybody know why?

I've got an Acer Extensa 5635Z, Intel Graphics Media Accelerator 4500M, 1Gb RAM.
Ubuntu 10.04 runs on 1366x768 pixels wide desktop, refresh rate is 60Hz.
The graphical options are set to extra, plus in the compizconfig the rotating cube and the window-pre-view effects are turned on.

Thanks in advance,
PI

---

### Post by Cowboybebop79 on 2010-05-05
I had the same problem as this after my first reboot of lucid however the problem hasn't reoccurred since then I had a quick look on launchpad and found this bug [https://bugs.launchpad.net/ubuntu/lucid/+source/indicator-messages/+bug/549096]("https://bugs.launchpad.net/ubuntu/lucid/+source/indicator-messages/+bug/549096") which is similar to the problem you are having as far as I can see from the bug report the problem has been fixed and an update will fix the package on your system.

viszontlatasra!

;)

---

### Post by John Bean on 2010-05-05
Yes, I get this sometimes too. In my case I removed and reinserted the applets in s slightly different order and with added spacers. The indicator applet seems to be the offender, corrupting adjacent applets randomly (which is why I tried a spacer either side of it). So far the new arrangement seems to be behaving normally.

---

### Post by pi24 on 2010-05-06
Thanks for your answers, guys!

The strange thing is, since I have posted this issue, it didn't happen again... 
So I think it's solved :)

Cheers,
PI

---

### Post by John Bean on 2010-05-06
There's just been an update that may have helped, it certainly improved the Network Manager applet by restoring and adding to the right-click functionality - I can finally get rid of the annoying wi-fi notifications :-)

It's very early days for Lucid, it can only get better... hopefully.

---

### Post by wilee-nilee on 2010-05-06
In the terminal.
```
nautilus -q
```

---

### Post by pi24 on 2010-05-06
I'm already very satisfied with Lucid, there are only small glitches... It's already far more powerful and faster and reliable and friendly than W!

What does the "nautilus -q" command do?

---

### Post by wilee-nilee on 2010-05-06
> **pi24 said:**
> I'm already very satisfied with Lucid, there are only small glitches... It's already far more powerful and faster and reliable and friendly than W!

What does the "nautilus -q" command do?

It is a command I found on the forum that fixes the panel glitches, for me, that occur on occasion in Lucid. I think it is a restart of nautilus, or something. I does no damage and resets the desktop and panel, to looking correct.

---

### Post by pi24 on 2010-05-07
Okay, thanks! I learn new commands every day since I'm using Ubuntu! :) Currently the icons look all right.

---

