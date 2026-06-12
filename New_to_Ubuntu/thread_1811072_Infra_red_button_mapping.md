---
title: "Infra red button mapping"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by CaptainJamie on 2011-07-24
Is this even possible?
I have a remote that came with the computer but over half the buttons do nothing. Is there a way to, say, press a button and a program would say: "This button does nothing, would you like to assign a terminal command or keyboard shortcut to it?" And I would say "yes, I want the command 'vlc' to run" or "pkill -kill -u jamie" etc
Any ideas? Perhaps someone could put it in the idea thing where they're submitted to developers, because that would be cool...
Imagine pressing a button on a remote and a terminal command would run a custom made program such as one that wiggled the mouse every 5 minutes so you could press it every time you watched BBC iPlayer and the screen saver wouldn't come on.

---

### Post by bance on 2011-07-24
Hi CaptainJamie,


_L_inux_ I_nfrared_ R_emote_ C_ontrol or LIRC is what you are looking for, try google.

I think it's installed by default with most distros. Lirc has various utilities that will allow you to map buttons to various commands etc. It can be difficult to work out but I'm sure someone will help on the forums. It's usually used with media applications like VLC, mplayer & mythtv, but I suppose it can be modified to do most things. 

If your remote came with your case it's probably a HID (human interface device).... That may mean that not all the buttons will work (it's a deficiency within X).

HTH good luck,

Steve.

---

