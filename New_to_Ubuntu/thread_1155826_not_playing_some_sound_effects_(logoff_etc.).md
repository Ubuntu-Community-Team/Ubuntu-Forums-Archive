---
title: "not playing some sound effects (logoff etc.)"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by mayoban on 2009-05-11
Dear All,

While the majority of sound effects are working well on my system, I cannot get the following ones to play:

[LIST]
[*]logoff sound (working well under system>preferences>sound) but not on actual logoff, instead I get a system beep
[/LIST]

the following do not even play when clicked on under system>preferences>sound:
[LIST]
[*]window maximized/unmaximized/minimised
[*]New Email
[*]Empty Trash
[*]Long action completed
[*]Battery warning
[/LIST]

All other sounds & music are playing well (e.g. mp3 files with rythmbox, skype etc.)

Currently, devices under system>preferences>sound are checked as "auto-detect". I have also tried selecting "pulse audio", "alsa", or "oss", without success.

I tried reinstalling the ubuntu sounds package (as given as possible solution in another thread), and also installing the ubuntu studio sound effects. Neither one lead to a resolution.

Does anyone know what the problem could be?

Thanks a lot for your help, mayoban

---
I am using Ubuntu 9.04, 64-bit version
on a Lenovo Thinkpad R400, Type 7439-A85
Gnome Desktop with Compiz Window Manager and Cairo-Dock

---

### Post by haneya on 2009-05-11
Hi , 

try this package may be it will help you > sudo apt-get install gnome-session-canberra 

---

### Post by mayoban on 2009-05-11
Dear haneya,

Thanks a lot for your suggestion.

I checked in Synaptic Package Manager, whether the package gnome-session-canberra was installed. It was.

Then, I tried re-installing it, just to make sure that all the data were present.

Unfortunately, the problem remains unchanged.

Cheers, mayoban

---

### Post by lelamal on 2009-07-21
Same here. While I can preview those sounds if I browse to choose a custom one from within Sound Preferences (Sounds tab), I can't even click on the relevant play button displayed on the right, once the sound is chosen. It's as if they are unavailable, or have been disabled somehow. I can't figure out.

As for the logout sound, mayoban, you can try this: [HTML]http://www.ubuntugeek.com/howto-enable-system-sound-in-ubuntu-intrepid.html[/HTML]. The last bit helped solving the problem for me. The first part isn't going to help, for Jaunty already comes with the latest version of libcanberra.

---

