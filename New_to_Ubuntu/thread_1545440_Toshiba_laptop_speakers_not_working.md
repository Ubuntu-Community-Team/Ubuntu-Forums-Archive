---
title: "Toshiba laptop speakers not working"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by noseshark on 2010-08-03
[FONT=Arial][SIZE=2][COLOR=DarkGreen]I just installed Ubuntu 10.4 on my old Toshiba  Satellite A20 (PSA20C - 0C04D).
[COLOR=Black]My speakers or headphones are not working[/COLOR] :( I checked all the volume controls ect. everything is on. 
I googled how to try to fix it but none of it made sence to me :/ 
I just want to listen to some music,

Please help. 
thanks.[/COLOR][/SIZE][/FONT]

---

### Post by wesleybailey on 2010-08-03
I did a search for your laptop and could not find the actual hardware it uses [PSA20C-0C04D]("http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1912&part=1992#spectop")

All it mentions is this
Stereo speakers, Full duplex 16bit stereo. Direct 3D sound. External mic and headphone port. Line-in, Volume Control dial.

The first thing I would do to troubleshoot audio, is ensure that the audio card is being picked up.

In a terminal excute this command.
```
lspci
```

That will list that hardware that is recognized, ensure that something in that list mentions audio.

If you have an audio device listed there, then try playing around with alsamixer
```
sudo alsamixer
```

This program allows you to check the various audio sources and outputs.
1. Check if the sliders are all the way up.
2. Make sure all of the channels are unmuted (00) <- should be highlighted green.

Let me know

Wes

---

### Post by noseshark on 2010-08-03
[FONT=Arial][SIZE=2][COLOR=DarkGreen][COLOR=Black]some are muted :O
How do I unmute them?
I am pressing the up key but it still says[/COLOR] [COLOR=DeepSkyBlue]MM

*[COLOR=Black]edit: [/COLOR]*[COLOR=Black]I figured out to press M, but now they are all unmuted,all turned up and its still not working :([/COLOR]
[/COLOR] [/COLOR][/SIZE][/FONT]

---

### Post by beesyell on 2011-07-10
Hi, my speakers aren't working as well but I can hear sounds when I use headphones/earphones. I have followed every instruction for the alsa mixer. all the sliders are up and there's a 00 highlighted in green above the <Master>. But still the speakers aren't working. :( What do you think is happening here? :(

---

