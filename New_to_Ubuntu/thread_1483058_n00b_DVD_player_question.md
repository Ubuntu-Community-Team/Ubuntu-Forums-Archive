---
title: "n00b DVD player question"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by bluesoldier007 on 2010-05-14
I am trying to play a DVD on my computer that is running lucid lynx.  When I put the DVD in, a DVD icon appears on the desktop with the correct title of the DVD, however, the built-in Movie Player cannot play the DVD - it says it is missing a DVD plugin, and then when it searches for the plugin, it says no plugin can be found.
 
I have also tried the VLC media player and the Kaffiene media player, neither of which will play the DVD.  The DVD plays in a normal DVD player, and works on my wife;s Vista laptop using Windows Media Player.
 
Does anyone have any suggestions for how to get the DVD to play correctly?
 
 
Edit:  P.S. - I am not getting any error message about codecs from VLC or Kaffiene...VLC just does nothing and Kaffiene says it cannot read from the DVD (I did an error check on the DVD and no errors were found)

---

### Post by Ms_Angel_D on 2010-05-14
Did you install Ubuntu Restricted Extra's?

Also you might wanna check [THIS]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux") Tutorial out

---

### Post by arochester on 2010-05-14
Look at "https://help.ubuntu.com/community/Medibuntu". You need the package: libdvdcss2

---

### Post by bluesoldier007 on 2010-05-14
Thank you very much.  I had not installed the Ubuntu Restricted Extras.  I had installed the GStreamer codec plugin, but not the libdvdcss2 package to allow play of encrypted DVDs.

---

