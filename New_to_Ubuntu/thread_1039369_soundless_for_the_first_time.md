---
title: "soundless for the first time"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by tekne on 2009-01-14
Hello again,

10 minutes ago i was in a coffee shop listening to music on my computer while studying. When i finished, i shut it down, came home and when i tried to listen to some music my Rythmbox started to jam every time i pushed play on a song without even starting to play it. then i tried youtube.com to check if it could be just rythmbox or something else. it looks like it is something else because the videos play but there is no sound.. plus rythmbox always needs killing. 
There is something else, before anyone asks that question: i DID NOT install anything between the "it plays sound" and the "it doesn't play sound" moments.

Any suggestions?
Thank you

---

### Post by Bölvaður on 2009-01-14
To begin to rule out possible faults.

Hardware: Try running on livecd or something else that should give you sound.

Pulse audio: Switch all to OSS. (System &#8594; Preferences &#8594; Sounds)
Also try different devices on there and ALSA also.

*this is not... uh.. it is stupid tbh*
Further more install PulseAudio Device Chooser (padevchooser) and play with it.... no wait.. waiiit.. that makes no sense at all, it is a great program that can let you listen to 1 song in usb headphones while listening to another one in your speakers... but probably is not good for you atm.

---

### Post by kansasnoob on 2009-01-14
Not sure you're on Intrepid, but if so read Note #1 here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by tekne on 2009-01-14
Bölvaður, looks like switching everything to OSS worked, thank you.
But still, it is strange why it suddenly turned soundless without me making any change, installation or whatever.
thank you anyway =)

---

### Post by tekne on 2009-01-14
actually no, sorry! now rythmbox has sound, but not firefox... lol
again, any suggestions?

---

### Post by Bölvaður on 2009-01-14
You really should look into what is wrong, you may learn from it ;)
For an example. Try the padevchooser (man this looks weird when they shorten it down that much) and pick different settings for vlc and totem.. and then try see how it acts. there is a config file under ~/.pulse where you can manually change it also.

*added*
you can try purge (remove) pulse out.. hunt down for all config files left on your system and then reinstall.
also there is a new version of OSS that may be interesting...

---

### Post by WitchCraft on 2009-01-14
> **tekne said:**
> actually no, sorry! now rythmbox has sound, but not firefox... lol
again, any suggestions?

Yes: switch off automatic updates, compile the latest alsa drivers and restart

---

### Post by tekne on 2009-01-14
sorry but i don't know what "compile the last alsa drivers" means nor how it is done

---

### Post by Bölvaður on 2009-01-14
> **tekne said:**
> sorry but i don't know what "compile the last alsa drivers" means nor how it is done

Google will help you find a whoto. but I'd try set everything on pulseaudio and try to find out if you can set everything up. I assume you have tried the program I suggested...

---

### Post by WitchCraft on 2009-01-14
> **tekne said:**
> sorry but i don't know what "compile the last alsa drivers" means nor how it is done

latest, not last.

You find detailed instructions on how to compile the latest advanced linux sound architecture driver here:
[http://ubuntuforums.org/showthread.php?p=4011326](http://ubuntuforums.org/showthread.php?p=4011326)

---

