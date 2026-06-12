---
title: "multimedia player"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by khatikbbdn72 on 2010-11-22
hie everyone..

well since when i decided to learn, my life is miserable, my wireless is not working. already started thread regarding that but no solution till now, but i can't wait anymore fro my wireless to work and only then start working on linux, coming to point

i am a newbie on linux..
i want to view some videos that i mount from other drive specially for windows..
those are  * .avi * files...  so plz help me to find some of the players on ubuntu that can view these * .avi * files.

NOTE-> i am offline on ubuntu so plz give me complete description for packages and library required for that player

i have UBUNTU 10.10 MAVERICK

thanx in advance

---

### Post by eriktheblu on 2010-11-22
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I'm assuming AVIs are one of the restricted formats.

---

### Post by kelvin spratt on 2010-11-22
vlc will play anything almost they do both linux and windows players and its in the ubuntu repositories

---

### Post by bookcrazy on 2010-11-22
> **kelvin spratt said:**
> vlc will play anything almost they do both linux and windows players and its in the ubuntu repositories
VLC works for me.

---

### Post by marl30 on 2010-11-22
p, li { white-space: pre-wrap; } > **eriktheblu said:**
> https://help.ubuntu.com/community/RestrictedFormats
 
 I'm assuming AVIs are one of the restricted formats.
 
 Do as Eriktheblu suggested and install these: ubuntu-restricted-extras, w32codec, libdvdcss. You can open up the software center or synaptic to install them.

This allows you to use other players besides just VLC.

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]*SM-player is not bad *;)[/SIZE] , [SIZE=2]I usually use it for many Formate's...[/SIZE]

---

### Post by lobralleo on 2010-11-22
Sad to hear that you are having problems: wireless has always been sort of messy for me too under linux :(

If you want to install w32codecs and libdvdcss (assuming the latter is allowed in your country), you will have to add the Medibuntu repository; you can find all relevant information here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

In my personal experience, VLC is possibly the easiest solution to play video content: if not for some very specific codec, it basically plays everything (I only had some little problem with very old and badly packaged Real media).
If you want to follow this road, you can also install mozilla-plugin-vlc, which will provide Firefox a nice plugin to play streaming video using VLC itself (here I am assuming you use Firefox or another Mozilla-based browser).

I you want to go for a different solution, I would recommend to install mplayer, gnome-mplayer and gecko-mediaplayer for an equivalent solution (mplayer will provide the engine, gnome-mplayer the frontend and gecko-mediaplayer the plugin to play video in your browser). If you are using KDE, you can instead install kaffeine.

Wish you luck! :)

---

### Post by NightwishFan on 2010-11-22
If you are an offline user (is that what you had meant?) you might find these links helpful. I would suggest you perhaps use Ubuntu 10.04 if you are an offline user as it is more well tested and longer supported.

You can use this to download and manage updates:
[http://keryxproject.org/](http://keryxproject.org/)

This is a package search for manual downloads:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

This allows you to make a CD repository:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)


Here is the Ubuntu package and required packages for VLC, which I recommend as well. Note you also will likely need the "dependencies of its dependencies", so using something like keryx is recommended.
[http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc)

---

### Post by khatikbbdn72 on 2010-11-22
thankyou all for such useful and kind suggestion, and congratulate you all for maintaining this sea of knowledge that makes beginers like me life's simpler..

i checkout all above links and let u know.

@nightwishfan, thanx for such useful links.. you could assess my offline problem bettar.

---

### Post by tajiknomi on 2010-11-23
[SIZE=2]If the Problem is solved ,Plz mark **thread as solved** in Forum-tools...[/SIZE]:p

---

