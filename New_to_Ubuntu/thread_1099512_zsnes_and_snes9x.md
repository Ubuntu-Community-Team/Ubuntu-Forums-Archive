---
title: "zsnes and snes9x"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-03-18
well, I tried to install zsnes on xubuntu and the sound doesn't work... what the hell? I also tried gsnes9x and I can not find where the hell to specify my keyboard. all I can find is where to specify my controller and that doesn't even offer the direction pad for some ****** up reason.

---

### Post by richaoj on 2009-03-18
for zsnes, have you gone in the settings and clicked "enable sound".  It also depends on the particular rom.  Some roms have different sound settings.  I would suggest trying a different rom and/or tweaking the sound settings.

---

### Post by LunaticHiatus on 2009-03-18
I have sound enabled, I have tweaked the sound settings as mch as I could see and got nothing.

---

### Post by benmoran on 2009-03-18
Zsnes has command-line options to change the sound system. Just run the command once and it will update in the config. 
You can use:
zsnes -ad pulse
zsnes -ad alsa
zsnes -ad oss
zsnes -ad sdl
etc. etc. 

Try zsnes --help for a complete list.

---

### Post by allen payne on 2010-03-29
Man can somebody plz tell me how to even install zsnes on that xubuntu i tried every thing and im tired of reading

---

### Post by JoelOFH on 2010-03-29
> **allen payne said:**
> Man can somebody plz tell me how to even install zsnes on that xubuntu i tried every thing and im tired of reading

sudo apt-get install zsnes

---

### Post by allen payne on 2010-03-30
NO NO NO NO!!!! that sudo apt what ever ain't workin i have xbuntu 9.10 it has snes9x but i dnt know how to run it

---

### Post by kiddykoff on 2011-08-10
type in snes, then hit tab and it should autocomplete.

for me i'm getting snes9x-gtk

---

### Post by jtarin on 2011-08-10
> **LunaticHiatus said:**
> well, I tried to install zsnes on xubuntu and the sound doesn't work... what the hell? I also tried gsnes9x and I can not find where the hell to specify my keyboard. all I can find is where to specify my controller and that doesn't even offer the direction pad for some ****** up reason.I'm confused.....are you asking about installing or locations in hell to find applications?:rolleyes:

---

