---
title: "Vnc and leopard"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by oromisthewise on 2007-11-17
Ok guys, ive got a brand new imac which i have just upgraded to leopard with up-to-date and i noticed that when i connected to my network it found my ubuntu pc and offered to share the screen. but when i click this is goes on forever an never actually connects. i have remote desktop enabled in ubuntu so why doesnt it work?

 also i would be really REALLY interested in viewing my mac desktop from my ubuntu pc so i can start dvd rips, downloads and other tasks, or maybe even get something done or use front row, if its fast enough. 
 
i dont mind getting programs for either computer as long as it works ( 'cept im kinda not wanting any programs for the mac as i keep it minimalistic as apple intends)

 thanks!

---
{edit}
oh and by the way, does anyone know of an ubuntu equivalent of front row, i love that app but its a bit codec-lacking and my ubuntu pc is linked up to my big screen in my room so i want it for my large collection of dvds which i have ripped with handbrake

---

### Post by btrvalik on 2007-11-17
I'm having the same problem..  I can VNC to my Leopard machine,  I can VNC from my Leopard maching using jollysfastvnc.  If I try to use Leopard's Desktop sharing it just hangs.  This is also true if I try to connect to my Tiger machine.  It drives me crazy every time I read how easy it is..

---

### Post by futurepublic on 2007-11-18
Same here: I can't get the screen sharing client in Leopard to connect properly to my Ubuntu (Gutsy) server.  

Bit bizarre: the leopard screen sharing client has no problem finding my ubuntu box, and ubuntu actually says that its being controlled by my leopard laptop.  So some sort of connection is being made.  But that's as far as it gets: leopard just says its 'connecting' - and never presents me with a window of ubuntu's desktop.  

I know that vnc works - becuase i've just tried it successfully with 'chicken of vnc' - but I'm a fan of the built in mac service, and v. keen to get it working properly.  Any ideas?

---

### Post by banewman on 2007-11-18
Don't use macs but had a problem with my router changing the ip address of each comp - seting static ip addresses made vnc so much freindlier. Hope that helps. :)

---

### Post by btrvalik on 2007-11-18
It's a security problem..  I deliberately turn the display password off on my ubuntu machine.. turns out, Leopard does not like that.. would be nice to put up a simple warning!  Once I enabled a password on my Ubuntu machine, it prompted me, and I'm using it now.. It also warned that the VNC on Ubuntu does not support key press encryption.. just say OK..

---

### Post by bigken on 2007-11-18
front row  equivalent mythtv

---

### Post by futurepublic on 2007-11-18
> **btrvalik said:**
> It's a security problem..  I deliberately turn the display password off on my ubuntu machine.. turns out, Leopard does not like that.. would be nice to put up a simple warning!  Once I enabled a password on my Ubuntu machine, it prompted me, and I'm using it now.. It also warned that the VNC on Ubuntu does not support key press encryption.. just say OK..

Perfect - thanks! Once I'd check the 'require the user to enter this password' option in ubuntu's remote desktop preferences and filled in a password, leopard's screen sharing client  worked perfectly - nice and fast too. Thanks for the tip.

---

### Post by Blutack on 2007-11-18
Media centres...
MythTV as suggested
Freevo - light but a pain to set up
Elisa, pretty, easy but again a bit of a pain to set up (easier than the above though)
[http://elisa.fluendo.com/](http://elisa.fluendo.com/)

---

### Post by oromisthewise on 2007-11-29
> **Blutack said:**
> Media centres...
MythTV as suggested
Freevo - light but a pain to set up
Elisa, pretty, easy but again a bit of a pain to set up (easier than the above though)
[http://elisa.fluendo.com/](http://elisa.fluendo.com/)


 Thanks for elisa that looks really nice. ill try to set that up as soon as i can

---

### Post by bigken on 2007-11-30
hmmm just tried elisa not a patch on mythtv

---

