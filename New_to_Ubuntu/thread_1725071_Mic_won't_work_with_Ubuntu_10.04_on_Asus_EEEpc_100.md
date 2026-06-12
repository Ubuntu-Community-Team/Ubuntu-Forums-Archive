---
title: "Mic won't work with Ubuntu 10.04 on Asus EEEpc 1001pxd"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by kirbyw on 2011-04-09
[COLOR=Black]OK, I know there are lots of posts online about this. And I've searched through the[/COLOR][COLOR=Black] **[COLOR=Blue][bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183")[/COLOR]** on Launchpad, and I've tried installer hda-verb, nothing is working for me. I'm posting this here because I'm new to Ubuntu and I need step-by-step instructions in the Terminal. 

I cannot get the microphone to work at all. Not in Skype, not in Sound Recorder. Nothing. And when I put in headphones the sound doesn't work at all. I've tried some work-arounds which leave me with sound out of the speakers and the headphones at the same time. Obviously useless for me. I've tried this little trick :"options snd-hda-intel model=lifebook" and it won't work for me. Whether it's lifebook or fujitsu. [/COLOR] [COLOR=Black]

I tried to get the latest stable kernel and compile it using these[/COLOR] [COLOR=Black]**[COLOR=Blue][instructions]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html")[/COLOR]** (although I have to admit that I have no idea what all that means) and the terminal kept coming up with "No file or directory." So that's not working for me. I have Alsamixer and also the sound mixer for PulseAudio because some people said messing with the left/right controls on that would work. It doesn't.

I wouldn't be so desperate, but I actually live in China at the moment, and Skype is the only access I have to family besides email. It'd be nice to actually talk to them. I'm seriously going crazy. [/COLOR] [COLOR=Black]

PLEASE HELP.[/COLOR]

---

### Post by Daveth on 2011-04-09
are you using the on-board microphone, or a jack, or usb mic? Does the bios have a setting for audio; I recall the original eeepc 701 had the webcam turned off in the bios and you had to turn it on. Just some thoughts.

---

### Post by Nytram on 2011-04-09
This could be stating the obvious, but you say you're new to Ubuntu so.. I've got an EEE 1005 and by default the microphone volume levels were set very low, so as to be be inaudible. You can check this, or try changing the levels, in **System/Preferences/Volume Control.**

---

### Post by kirbyw on 2011-04-10
Oh yay! Replies! Thanks guys :)

I'm using the onboard microphone. But I've also tried using one through the jack, and that doesn't work either. All I get is a hissing noise, sometimes. And I double-checked, everything is turned up. I also went into Alsamixer and made sure everything was turned up there. I checked the BIOS and everything is enabled. 

I did a fresh install of 10.04 last night..turned everything up, double-checked the BIOS, still have the microphone issue. So.. now I'm at anyone's mercy as to what other little contraptions I should download to try to fix this problem.

---

### Post by Daveth on 2011-04-11
a similar post on Fedore suggested using dmesg to explore whether the system actually recognises the mic. So, in a terminal, type 3 separate commands, and come back with the output. I don't know how the system would see a mic, so these look like generic searches rather than specifying it as being, say, a usb device. If you wanted also to plug in the jack mic, and then re-run this, it might show something. 

```
dmesg | grep -i audio
dmesg | grep -i error
dmesg | grep -i fail
```

the post was solved, and might be worth reading anyway
[HTML]http://www.linuxforums.org/forum/red-hat-fedora-linux/167019-solved-having-issues-laptop-mic-detection.html[/HTML]

---

