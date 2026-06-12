---
title: "Quiet Sound"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by pyong on 2009-04-21
Hi, I just recently installed Ubuntu 8.10, and I have been looking around for help for my problem of the sound being quiet.
I set alsamixer to the highest, and i turned my volume up to the max on my speakers and on the keyboard volume button, it is managable, just not quite as loud as on windows.
I have the Intel D975XBX motherboard With a Pentium D 3.20ghz Quad core processor Extreme Edition
I have an Ati HD4870 Graphics card, and I would like to know if there is any way to make my sound louder
Thanks :)

---

### Post by unutbu on 2009-04-21
If you do not have a speaker icon on your gnome panel:
Right-click on your gnome-panel and "Add to Panel...". Add the "Volume Control" applet to the panel. A speaker icon should appear on your panel. Now follow the instructions below.

If you have a speaker icon on your gnome panel:
Right-click on the speaker icon 
Select "Open Volume Control"
Increase the Master and PCM channels.
If that doesn't help, click Preferences and enable all channels.
Increase them all.

---

### Post by Michael.Godawski on 2009-04-21
hi,

so you say your sound is working fine, but it is more quiet than in Windows?

For movies I would try VLC. The digital amplifier is stronger than in other programs.

Also have a look at:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=878878](http://ubuntuforums.org/showthread.php?t=878878)
[/LIST]

You are not alone ;)

---

### Post by pyong on 2009-04-21
Thanks!
It works now, I was actually kinda shocked at first though, I wasn't expecting it to be that loud, its now much louder than windows too!
Thank you very very much! Much appreciated :)
On some games input lag occurs, generally when a button is pressed alot, most specifically my mouse button, I fixed it with ```
export SDL_VIDEO_X11_MOUSEACCEL="1/1/1"
export SDL_VIDEO_X11_DGAMOUSE=0
``` but I was wondering if i could have that be a default for all programs, including firefox, which also gives me the problem without having to edit the sh file for them all
Thanks :)

---

### Post by unutbu on 2009-04-21
Open a terminal and type
```

gedit ~/.profile
```

Add these lines
```

export SDL_VIDEO_X11_MOUSEACCEL="1/1/1"
export SDL_VIDEO_X11_DGAMOUSE=0
```

to the end of the file. Save and exit. Log out. Log back in.
The environment variables will be set for all programs you launch.

---

### Post by pyong on 2009-04-21
Wow, Thanks alot, :)
Your a really helpful persoun, thanks :D

---

### Post by unutbu on 2009-04-21
Glad I could help! :)

---

### Post by pyong on 2009-04-21
Me too! :D
Is there a way to +rep in this forum?
Because it is quite due :)
A friend of mine, who just installed Ubuntu is unable to connect to the internet, I told her to do the sudo lshw command to find out what motherboard she has, and it reported as PROD00000000, what should she do?

---

