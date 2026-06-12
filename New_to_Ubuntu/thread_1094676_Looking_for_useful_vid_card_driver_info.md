---
title: "Looking for useful vid card driver info"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by person8451 on 2009-03-12
Ubuntu 8.04

Compaq evo510d sff 2.0 GHz/2GB RAM

Chaintech AGP vid card

Result of lspci-aspca-naacp-idkwtfbbq-something grep  | VGA (or whatever that was) --


01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

OK...when I installed the driver as prompted, and rebooted, I was stuck with 640x480 resolution.  I have searched here for information on how to fix this, and so far have been confused by people arguing amongst themselves about how the drivers in the repos are old or something.  There seems to be no definitive answer, or if there is I have not found it.

With the suggested driver disabled, I have normal screen resolution but no desktop effects enabled.  If I attempt to enable desktop effects, it wants me to install that driver, which does not work.  So, I would like to know if there is a way to actually use my graphics card in Ubuntu 8.04.

---

### Post by Temposs on 2009-03-12
First, you are using your graphics card with Ubuntu, just not to its fullest extent. You're using the "nv" driver which is a free software driver than only has support for 2D graphics.

The nvidia proprietary drivers are what provides 3D support for nvidia graphics cards. For your card, you *must* use the nvidia driver version 173 in order to have desktop effects enabled. No other driver will give you desktop effects for your graphics card.

So, are you saying with this driver in use, you go to the System->Preferences->Screen Resolution, and you only have 640x480 available to you? What exactly happens? Does it start in safe graphics mode or is it just low resolution?

Note also, you may want to try searching the nvnews forums: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

P.S. I have a GeForce FX Go5200, so somewhat close to yours.

---

### Post by person8451 on 2009-03-12
Hmm.

Well it didn't say it was in Safe Graphics Mode, and I assume it would like, tell me that.  Anyhow, when I go to Sys/Prefs/Screen Res it only lets me set it to 640x480, or one even lower setting.

I will have a look around that link, see if I can find anything.  Thanks :)

---

