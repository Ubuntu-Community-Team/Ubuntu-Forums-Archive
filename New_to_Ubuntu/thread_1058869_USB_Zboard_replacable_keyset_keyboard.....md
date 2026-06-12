---
title: "USB Zboard replacable keyset keyboard...."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Geemy on 2009-02-03
Hi guys,
Before I switched to Ubuntu I was using the USB Ideazon/Steel Series Zboard pictured here:
[IMG]http://www.steelseries.com/web/assets/products/gaming_keyboards/wotlk-gk/wotlk-gk-product-image.jpg[/IMG]
I'm having a hard time trying to figure out how to get this keyboard to work in Ubuntu and Wine. I downloaded the latest Windows Drivers from here:

[http://www.steelseries.com/downloads/Drivers/keyboards/Zengine/ZEngine_25023_NA.exe](http://www.steelseries.com/downloads/Drivers/keyboards/Zengine/ZEngine_25023_NA.exe)

And then tried opening with Wine. It then starts some sort of file check, I think it's looking for the .NET framework or something, then it tries to install whatever it missing and fails. Not sure what to do from here.

If you need the exact error messages, I can get them to you later today. (I'm at work on my lunch break at the moment)

Anyone else use this keyboard? If so can you tell me how you were able to install the drivers?

I was able to find one person who uses this keyboard and Ubuntu through a Google search, but their question seemed specific to making the media buttons work, which I don't really care about. I'm more concerned about the special macro buttons on the interchangeable key sets.

Thanks,
~Geemy

---

### Post by Temposs on 2009-02-03
You might try installing the .NET framework yourself. It seems like this is a pre-requisite for using the keyboard's software.

---

### Post by phr0ze on 2009-02-03
I use the keyboard (I have the butterfly keyset on it) It seems to work fine in ubuntu, though 1. I have never tried to use a particular keyset in wine. 2. I have never tried to switch the keyset. 

Most of the games I play are FPS which all run natively and the default butterfly keyset is good enough.

---

### Post by SqRt7744 on 2009-02-03
don't install drivers with wine... it's not the way to go. Wine just fakes a windows install for programs so that they think they are running in windows when in reality they aren't. If the hardware isn't supported in linux, then installing the drivers in wine will *not* help - guaranteed.

see [http://ubuntuforums.org/showthread.php?t=522994](http://ubuntuforums.org/showthread.php?t=522994)

If the scancodes can be read then they can be set to launch whatever you want...

---

### Post by Norwal on 2009-12-29
Hello,

I was thinking of getting a WOW Zboard and was wondering if anyone has got these USB keyboards working.

---

