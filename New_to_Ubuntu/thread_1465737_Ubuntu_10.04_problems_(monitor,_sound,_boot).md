---
title: "Ubuntu 10.04 problems (monitor, sound, boot)"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Loki57701 on 2010-04-29
Hey guys, I'm using ubuntu 10.04 and I'm having a few small problems.

1) External Monitor:

I use a laptop with an external monitor for the primary display. When Ubuntu starts up it recognizes the external monitor, but uses it as an extended desktop instead of the primary display. I have to manually set it to twin-view every time. Is there a way to change this so its starts with the external monitor as the primary display?

2) External Speakers:

I've googled this issue but couldn't find a fix. My laptop speakers work but when my external speakers are plugged in I get no sound. In Preference>Sound under the Hardware tab I've gone through all the options in the drop down profile menu with no results. 

3) Slooooow boot:

I'm using Ubuntu 10.04 on a desktop and laptop. On my desktop the boot time is very fast. On my laptop however, the system boots up to the default login screen background, but the actual login prompt doesn't appear for another 2-3 minutes. Anyone know why that would be?

---

### Post by Teber on 2010-04-29
apparently some thingy needs to save a thing or two whilst booting. after a couple of reboots booting will take far less time. at least that happened to me.

check out this thread [http://ubuntuforums.org/showthread.php?t=1465661]("http://ubuntuforums.org/showthread.php?t=1465661")

---

### Post by Loki57701 on 2010-04-29
I've been using 10.04 for awhile now and I've rebooted way more than twice, so thats not the issue. Thanks though.

---

### Post by aljoriz on 2010-04-29
are you using the Net book edition for laptops? They say it has some special configuration for lap/netbooks.

---

### Post by Geoff918 on 2010-04-29
Have you checked your boot logs?

My best guess given no real information would be that some device is perhaps failing to initialize either a) in a timely fashion or b) at all

You should look for some "fail" of some sort in your boot logs.

---

### Post by randumnumber on 2010-04-29
> **Loki57701 said:**
> Hey guys, I'm using ubuntu 10.04 and I'm having a few small problems.

1) External Monitor:

I use a laptop with an external monitor for the primary display. When Ubuntu starts up it recognizes the external monitor, but uses it as an extended desktop instead of the primary display. I have to manually set it to twin-view every time. Is there a way to change this so its starts with the external monitor as the primary display?

2) External Speakers:

I've googled this issue but couldn't find a fix. My laptop speakers work but when my external speakers are plugged in I get no sound. In Preference>Sound under the Hardware tab I've gone through all the options in the drop down profile menu with no results. 

3) Slooooow boot:

I'm using Ubuntu 10.04 on a desktop and laptop. On my desktop the boot time is very fast. On my laptop however, the system boots up to the default login screen background, but the actual login prompt doesn't appear for another 2-3 minutes. Anyone know why that would be?

On the external speakers, i had this problem when i installed 9.04 for the first time, i had to download the lsa drivers and unmute the headphones output... it was muted and the system had no way to unmute or change volume on it without the lsa drivers....dont know if this is your problem but it might help

on the monitors:
[http://ubuntuforums.org/showthread.php?t=782249](http://ubuntuforums.org/showthread.php?t=782249)

you may need to change a default setting in your xorg.conf to tell it which monitor to use.

---

### Post by kit1980 on 2010-04-29
Mic (ASUS Laptop internal) stopped work for Skype.

 Mic worked perfectly in Karmic, but in 10.04 I have only very-very low volume distorted sound in Skype. 

Mic still works for playback (I can clearly hear my own voice from speakers in real-time, and if I raise the volume I got audio feedback) but not for capture.

I tried to adjust various settings in alsamixer with no success. Also I no longer have "capture source" switch in mixer - maybe this is a cause...

---

### Post by Loki57701 on 2010-04-29
I'm using a regular laptop, not a netbook. 

What specifically would I need to check in my boot logs?

I will check out the lsa drivers guide.

Thanks

---

### Post by wolfmaniac on 2010-04-30
OK...for mic with skype.....install pavucontrol from synaptic.

Then Alt+F2 ... pavucontrol.... 

go to "Input Device" tab. Click on the lock to unlock the sliders. Then set the input levels of both the sliders to different value. 
Remember...do not keep the sliders locked.

Now you should be able to all using skype.

You can also install "linux-backports-module-alsa-lucid-generic" in addition to the above step.

I  tried it on Asus eeep 1005HA and it worked for me

This is an irritating bug in ubuntu. I have Arch Linux on the same netbook and everything works fine there.

---

### Post by facemelter12 on 2010-06-26
I tried upgrading to Ubuntu 10.04 and I got a black screen once prompted to restart. Everytime I start my computer now it does the same thing: It goes through the normal Toshiba intro, then it starts the Ubuntu intro and then goes black right when it should start up and show my desktop. I tried burning it to a CD and booting from the CD but no dice. Any suggestions?
I have an older laptop, this could be the cause of my problems but I'm not sure why.
My computer:
Toshiba Tecra A1 (canadian laptop)
Pentium 4   2.2 GHz
RAM 1 GB

Its runs Ubuntu 9.10 just fine...

---

