---
title: "Monitor powering off during install - Probably an easy fix"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by rob &lt; on 2010-05-23
I'm having trouble installing the latest Ubunto I downloaded from the Ubunto homepage. 

I'll load it into my CD tray, the loading screen will come up (the Ubunto animation with orange/white dots) and then my monitor conks out. It feels like it's being put into power save mode, or that it's searching for a certain resolution that it can't achieve or something. 

It's an old CRT monitor on a fairly powerful desktop that used to run XP, but lately hadn't been able to boot up properly so I figured I'd install Ubunto and try to learn it.

When the monitor dies, it won't come back on like you'd think it would. It just sits. I can hear the CD drive working for a minute, and then stops. Maybe there's a command I can enter?

If anyone can help I'd very much appreciate it. If you need to know more about my system I'll try to answer.

---

### Post by Ozymandias_117 on 2010-05-23
Do you have an ATI Radeon HD 5xxx series gfx card?

---

### Post by rob &lt; on 2010-05-23
ATI Radeon X1200

The monitor is a MAG DX-700T if that matters.

---

### Post by Ozymandias_117 on 2010-05-23
During boot, on the purplish screen, press esc. Then it will pull up a menu press "f6" for other options and try installing with "nomodeset"

---

### Post by rob &lt; on 2010-05-23
Cool, I'll give that a shot in a minute. Upgrading my video drivers. I turned it on and expected it to die, but to my surprise, Vista loaded up. 

Ideally, it'll be the last time.

edit: had to burn a new disc, trying now.

---

### Post by rob &lt; on 2010-05-24
Seems to be working. 

You sir have my vote of awesomeness.

---

### Post by rob &lt; on 2010-05-24
Bah, it won't install now because I have a RAID drive. 

"the ext4 file system creation in partition 1 failed"

Or some such. I think my HDD is wonked.

---

### Post by Ozymandias_117 on 2010-05-24
I've never tried to set up a RAID in *nix but I thought it supported them out of the box...

You should probably make a new post, if you haven't already, and hopefully you can find someone who can help you. :)

---

