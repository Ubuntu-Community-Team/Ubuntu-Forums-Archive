---
title: "Mozilla, vlc Are slower than a snail.."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by harshpkaria on 2009-01-18
This is for the umpteenth time about my problems with Mozilla Firefox (the latest one) and VLC (again the latest one)

OS: Ubuntu 8.10
Firefox: 3.0.5
VLC 0.9.4
Pentium D Processor @ 2.80 GHz
3.5 GB RAM (upgraded from 512MB)

BUT THE PC IS SLOWER THAN EVERR!!!!!

Problem 1: Mozilla takes up my resident memory of 215 MB
The new search in Firefox 3 is terribly slow.
The tabbing and other browsing experience is as slow as it was in 8.04 and 7.10....


Problem 2: When playing in vlc fullscreen mode, options on "right click" are not available. They go when a frame changes..
Also, there is a Cairo clock on top right of the screen, without the seconds needle; but the screen of vlc flickers at every pulse, and that top right part goes blank....

I HAVE DISABLED THE EXTRA EFFECTS FROM "Extra" to "None"...

CAN I EXPECT ANY HELP FROM THE COMMUNITY????

The performance is also slow while playing streaming videos from website other than youtube; say the dailymotion.com ; and the controls - they are activated after 15/20 secs...


I hope i dont switch back to the "Common" OS.
I love linux, and ubuntu- but am all frustrated because of these probles...

---

### Post by harshpkaria on 2009-01-18
Please help soon, as the problem is making the PC really slow

---

### Post by harshpkaria on 2009-01-18
Sorry, but I am really frustrated, and sorry for bumping this thread again..

---

### Post by HavocXphere on 2009-01-18
The people posting on Ubuntuforums are mainly volunteers, hence no one is under any obligation to do anything. Asking politely and waiting patiently works wonders, attitude does not. Forum etiquette dictates that a thread may be bumped once every 24 hours, not twice in under and hour.

Switch VLC to X11 output instead of OpenGL.

Many of the FF effects you describe occur when the latency on your internet connection is high. FF's high memory usage is a know issue, but it also depends on the number of tabs open, the content of those tabs and the add-ons running.

Disabling effects does not necessarily mean that 3d acceleration of the desktop is disabled.

---

### Post by harshpkaria on 2009-01-18
@Havoxsphere:

It worked!The X11 mode.. Thanks a load Sir... Sorry for the rude tone... I will definitely maintain the forum etiquettes.

---

