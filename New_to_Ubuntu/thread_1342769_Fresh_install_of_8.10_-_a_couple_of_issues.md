---
title: "Fresh install of 8.10 - a couple of issues"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Greendan on 2009-12-01
Hi,

I just installed 8.10 and have a couple of issues:

- I can't set my screen resolution above 800 x 600. When the machine had XP on I ran it at 1074 x 768, any ideas?

- Also I have no sound, When I goto System-->Preferences-->Sound and click on one of the Test boxes I get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

I have no idea what that means!

Thanks for your help!

---

### Post by clhsharky on 2009-12-01
HI 

Have you updated since install, and what video chip do you have?

---

### Post by clive littlewood on 2009-12-01
Hi

8.10   or  9.10 ???   

Clive

---

### Post by mikewhatever on 2009-12-01
> **Greendan said:**
> Hi,

I just installed 8.10 and have a couple of issues:

- I can't set my screen resolution above 800 x 600. When the machine had XP on I ran it at 1074 x 768, any ideas?

Try checking if there is a driver for you under System->Admin->Hardware Drivers, and also, provide info about your graphics card.

> - Also I have no sound, When I goto System-->Preferences-->Sound and click on one of the Test boxes I get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

I have no idea what that means!

Thanks for your help!

You may need to select a different sound option, such as Alsa or Pulseaudio, as opposed to the default autoselection.

---

### Post by Greendan on 2009-12-01
I have updated since the install. When I hit the update to 9.04 button I get this message:

[B]This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04.
[/B]
Which is why I haven't installed that.
Under Hardware Drivers it says I have an ATI/AMD proprietary FGLRX Graphic Drivers. There is an 'Activate' Button. I hit that and it requested the admin password, says it is downloading and installing driver, doesn't actually download and then just goes back to the Hardware Drivers box, in the same state as before.

I have tried all the sound options and recieve the same error message with each one.

---

### Post by Greendan on 2009-12-01
Also, the speaker in the topright corner of the screen has a red no entry symbol on it likes it's muted, if I right click on it the Mute box in unchecked, and if I click on Open Volume Control I get a message:

**No Volume Control GStreamer plugins and/or devices found.**

---

