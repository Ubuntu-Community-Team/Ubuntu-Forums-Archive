---
title: "sound not working"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by sumeshgupta on 2009-08-13
I am using Hardy Heron. The install went smoothly. However the sound doesnt work. My soundcard is intel G33 onboard (ICH7) series. When I boot the card is recognised i.e humming sound starts in the speakers. However there is no sound in mplayer or vlc either. Am I to configure something to get these applications make the speakers work? Any help will be highly appreciated. I am yet to listen to a song on Hardy.:(
Thanks in advance.

---

### Post by pi4r0n on 2009-08-13
Hello **sumeshgupta**

My suggestions would be as follow:


[LIST]
[*]Check to see if you card drivers were loaded
[/LIST]
> [SIZE=2]aplay -[/SIZE]If it says 

> [SIZE=2]aplay: device_list:221: no soundcard fo[/SIZE][SIZE=2]und..[/SIZE][SIZE=2]
[/SIZE]
then install you drivers. Search how on **[GOOGLE]("http://www.google.co.uk/")**


[LIST]
[*]If you do get a list of your sound card then what I would do next would be to upgrade[COLOR=Black] your alsa drivers, lib and utilities to the newest one (version 1.0.20). 
[/COLOR]
[/LIST]

[LIST]
[*]If this does not fix your issue then I would go through this tutorial [SIZE=2][[COLOR=navy]_**[B]Comprehensive Sound Problem Solutions Guide** v0.5e[/B]_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")[/SIZE]
[/LIST]
Cheers

pi4r0n

---

