---
title: "Help With touch pad"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by rtw860 on 2009-05-24
Hello everyone its been a year since I have been able to use linux on a regular basis since my laptop would never run any distros tried them all, well good news ubuntu 9.04 works perfect just some minor issues here and there. Its been so long and so much has changed and improved in linux that im kinda rusty but its great to be working a comandline again I forgot how much control it truly gives you hehe and how easy it is to break things if you don't pay attention.

Anyways I have a gateway mt6707 and the touchpad has the side scroller which works great its just when your using the main part of the touchpad and you move your finger just before you hit the side scroller it also moves the page up and down. This is driving me crazy since I am thinking I have not hit the side scroller and the page moves up and down lol, sorry guys I wish I new how to fix this but its just I have forgot so much about linux and almost feel like a noob all over again.

---

### Post by Locutus_of_Borg on 2009-05-24
Gateway MD series here

this is my xorg mouse section and all works perfectly:
```
 Section "InputDevice"
         Identifier  "Mouse0"
         Driver      "synaptics"
         Option      "Protocol" "auto"
         Option      "Device" "/dev/psaux"
         Option      "ZAxisMapping" "4 5 6 7"
         Option      "HorizEdgeScroll" "1"
 EndSection

```

try that?

---

### Post by rtw860 on 2009-05-24
I no I am going to sound like a idiot when I ask but where are the mouse settings again, sorrys its been a while I am relearning a lot of stuff.

---

### Post by Locutus_of_Borg on 2009-05-24
First make a backup just in case, open a terminal and enter:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then enter:

sudo gedit /etc/X11/xorg.conf


and look for the section "InputDevice" that has "mouse" under it.

replace that whole section with what i posted, save, then restart X (ctrl+alt+backspace)

---

