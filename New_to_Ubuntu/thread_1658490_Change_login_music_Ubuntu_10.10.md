---
title: "Change login music Ubuntu 10.10"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2011-01-02
Hello,

A while ago on 10.4 I changed my login music (not the login screen music, but when I log into my user). But I seem to have forgotten how to do it. I've searched everywhere on-line, and everyone says to go to System>Pref>Sounds> Sound tab... but those must be for earlier versions as it's not there in 10.10, nor in 10.4.

Anyway, this is what I've done so far. I've added the .ogg sound file to the /urs/share/sounds/ubuntu/stereo folder then went to System>Pref>Start up Application and edited the "GNOME login sound" command to /usr/bin/canberra-gtk-play --id="***Song Filename***" --description="GNOME Login". But it still wont work!

Please help. Is there a update or something I need to do through the terminal?

---

### Post by Light Knight 22 on 2011-01-02
Nevermind. I simply replaced the "desktop-login" file instead.

---

