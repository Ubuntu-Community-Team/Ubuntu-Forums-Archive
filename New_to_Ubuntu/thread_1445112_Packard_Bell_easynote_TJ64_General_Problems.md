---
title: "Packard Bell easynote TJ64 General Problems"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Evoluate on 2010-04-02
Hello all,

I am completely new to Ubuntu. 
I have spoken to a friend who has been using Linux for ages, he said that Packard Bell usually produces laptops that are incompatible with Linux OS which is down to the hardware they come with.

Currently I am running Karmic 9.10 64-bit.

As I installed this version of Ubuntu for me to experiment on I think I might have wrecked this installation a bit. Yesterday I had issues getting my sound to work ( I think mplayer changed the drivers from alsamixer to pulseaudio). So I trawled the internet for about six hours but I never stumbled upon the same problem. In the end I decided to do the following:

Killall pulseaudio
alsamixer -forcereload
Pulseaudio -D

Then as that did not completely fix the problem I thought I should purge it, just to make sure. So I did. It worked a charm, my sound is back, although it lags a bit at login.
By doing this I somehow must have deinstalled the volume control applet.
It has disappeared from the task bar and the keys on my keyboard that control the volume don't work at all. The only way of controlling the volume is opening alsamixer and turning it up or down by using the mouse. This is extremely irritating.
Any ideas?

This might sound ridiculous since it's such a minor issue but I'm trying to make this laptop work with ubuntu so I hope someone can help me.
Please no replies telling me how irresponsible it is to work on a system without knowing what you're doing. I know that, it's just for experimental and self-educational purposes.

Thanks.

---

### Post by mikewhatever on 2010-04-02
There are various suggestions on how to mitigate the issue, the most common among which is installing gnome-alsa-mixer.
Check out the link below for more info.
[http://ubuntuforums.org/showthread.php?t=1368141](http://ubuntuforums.org/showthread.php?t=1368141)

---

