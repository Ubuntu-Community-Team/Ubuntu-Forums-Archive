---
title: "Problems installing MPLAYER"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Beaker Boy on 2010-12-20
Guys

I tried to install MPLAYER, but when running

[COLOR="Red"]./configure --enable-gui[/COLOR]


I got the error

[COLOR="Red"]Error: The GUI requires libavcodec with PNG support (needs zlib).[/COLOR]

What's going on?  Am I missing something?

And then how do I compile and run the code??  This seems flipping difficult!!

Beaker Boy

---

### Post by Surkow on 2010-12-20
Why are you attempting to compile your own version of MPlayer? If you want to install the missing libavcodec file you will need to search in Synaptic.

---

### Post by Beaker Boy on 2010-12-20
I'm trying to get MPLAYER to work with an online radio station.  When I attempt to listen, I get an error saying the 'MMSH protocol source' plugin isn't availabe and am trying to figure out why not

Any ideas?

---

### Post by Surkow on 2010-12-20
Maybe you'll have more luck with GStreamer based software (Totem for example). See [this]("http://ubuntuforums.org/showthread.php?t=1137833") thread for more information.

---

### Post by Beaker Boy on 2010-12-20
Sweet  Sorted pretty much.  The sound is playing but the player isn't showing the information normally dispayed when the online player opens.

But thank you for your help

Alex

---

### Post by davidmohammed on 2010-12-20
your issue sounds very much like [this one]("http://ubuntuforums.org/showthread.php?t=1137833") - install the suggested codec.  Then mplayer will stream it OK.

---

