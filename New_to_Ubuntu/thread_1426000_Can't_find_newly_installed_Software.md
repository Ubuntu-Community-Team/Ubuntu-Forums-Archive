---
title: "Can't find newly installed Software"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Aster-Phoenix on 2010-03-09
Hello i recently downloaded a program from the synaptic package manger named "RTK Recordmydesktop" i went to find it and test it and i could not find it so i went to the Ubuntu Software Center and it couldn't find it either.
where is my new program?

---

### Post by Enigmapond on 2010-03-09
That will probably be in Applications/Sound & Video or Accessories.....sometimes they don't show right away and will be there when you reboot..

---

### Post by mechro on 2010-03-09
It runs in a Terminal with command **recordmydesktop**. I should do **man recordmydesktop** first to see how you use it.

---

### Post by mechro on 2010-03-09
... Ah! You meant to say GTK recordMyDesktop which is the graphical front-end for recordmydesktop.

Is it not under Applications > Sound & Video?

If it's not there you can create a Launcher and/or a Menu item using the command **gtk-recordMyDesktop**

---

### Post by Aster-Phoenix on 2010-03-09
Hey i got it working but it came to another problem after recording i get my video file in ogv format and none of my players will play it i have VLC And Mplayer it loads up and shuts down in the blink of an eye.
Whats going on?

---

### Post by mechro on 2010-03-09
Is it complaining about your soundcard? Try recording without sound.

Does Movie Player work?

---

### Post by Aster-Phoenix on 2010-03-09
> **mechro said:**
> Is it complaining about your soundcard? Try recording without sound.

Does Movie Player work?
No its not and i did and no diffrence.
Movie player works fine on other stuff but not this

---

### Post by andrew.46 on 2010-03-09
Hi Aster-Phoenix,

The .ogv files produced by this program are made up of theora video and vorbis sound which most players can handle. If vlc is shutting down abruptly without error the chances are that you have an incorrect video out device set. Have a look in Tools --> Preferences --> Video --> Output and perhaps select something like x11.

All the best,

Andrew

---

### Post by Aster-Phoenix on 2010-03-10
> **andrew.46 said:**
> Hi Aster-Phoenix,

The .ogv files produced by this program are made up of theora video and vorbis sound which most players can handle. If vlc is shutting down abruptly without error the chances are that you have an incorrect video out device set. Have a look in Tools --> Preferences --> Video --> Output and perhaps select something like x11.

All the best,

Andrew
Hey it worked thanks!

---

### Post by andrew.46 on 2010-03-10
Hi Aster,

> **Aster-Phoenix said:**
> Hey it worked thanks!

My pleasure :). There will be a similar setting for MPlayer...

Andrew

---

### Post by mechro on 2010-03-10
> **andrew.46 said:**
> Hi Aster-Phoenix,

The .ogv files produced by this program are made up of theora video and vorbis sound which most players can handle. If vlc is shutting down abruptly without error the chances are that you have an incorrect video out device set. Have a look in Tools --> Preferences --> Video --> Output and perhaps select something like x11.

All the best,

Andrew

I didn't know that. Mine was set to Default which works so I'd never tweaked it before. Thanks for the tip. :D

---

### Post by daniel@deckersok.com on 2010-03-25
Me too. I installed a ftp program and it just is not there. Am rebooting. Why would the system not reboot then as part of the install or what causes the need for reboot? Daniel

---

