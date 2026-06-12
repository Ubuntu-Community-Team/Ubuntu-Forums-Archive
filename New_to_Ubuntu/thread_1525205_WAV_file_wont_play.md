---
title: "WAV file wont play"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by sunwatt on 2010-07-06
I just bought a cheap little Sanyo voice recorder model icr b130. It comes with a USB cable and a CD for Windows. I figured no problem, but thats not the case. I made a test audio file and plugged it into my Dell Vostro A9 (Mini 9) with Linux Mint 7. I copied the file to desktop, and when I tried to play it I got this message.

Ive never had any problems playing any audio/video file. I tried this wav file on my other Mini 9 running Ubuntu 10.04lts, and nothing will play it on that machine, using any player.

Error message with MPlayer is "Cannot find codec for audio format 0x125. 

An error occurred Could not determine type of stream when I try to play it with Movie Player. Not even VLC will play it, nothing will. Nothing plays it except for Windows Media Player on my old XP laptop. AHHH!

The wav file thats got the recording on it, properties says its a audio/x-wav type, whatever that means. Maybe this is the thing that makes it only playable with XP/Windows Media Player.

So I made sure there was a good recording by playing the file on the recorder, it also plays back. It plays on the little recorder.

Then I fired up my old Dell Inspiron with Windows XP, tried to play the file and no good. The PC with XP refused to even mount the Sanyo, I had to use a flash drive with the file on it to even try playing it. But it refused to play the file also.

Then I installed the CD that came with the Sanyo, and rebooted. This time XP recognized and mounted the Sanyo 16mb and I was able to play the file ONLY with Windows Media Player!

I put that PC away, and Im back on my Vostro A90 and Linux Mint 7, and I've attached a screenshot of the properties of this audio file. A 2nd screenshot of MPlayers error message.

Is there some driver I can install with synaptic?

Thanks!

---

### Post by cariboo on 2010-07-06
Your file is more than likely a .wma file. Depending on what version you are using, 32-bit or 64-bit try installing the w32codecs or w63codecs from the [Medibuntu]("http://medibuntu.org/") repositories.

---

### Post by sunwatt on 2010-07-06
Thanks for the reply. I downloaded the Juanty deb as this is Mint 7, and when I clicked it, the installer said reinstall package on the button, so I guess this is already installed???

Should I reinstall the win32codec anyway?

On my machine with Ubuntu 10.04lts I did the medibuntu non free stuff so youtube and music works. Both my machines play wmv and avi with no problems. But neither one will play this supposed to be wav file.

Not sure I ever encountered a wma file before on Linux. I've only been gone from Windows a year.

Thanks

---

