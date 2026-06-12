---
title: "Latest version installed but older one shows - Flash plugin"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-05
OK, so I'm confused.

According to Synaptic Package Manager, my current Flash (adobe-flashplugin) is version 10.0.32.18-1hardy1. That's as it should be, according to [Firefox's warning]("http://support.mozilla.com/en-US/kb/Firefox+Help").

But according Firefox > Tools > Add-ons > Plugins > Shockwave Flash, I only have version 9.0 r124.

What am I missing?

---

### Post by Bigtime_Scrub on 2009-08-05
I think you need to turn the old flash off to be able to use the new flash player 10. What I would do is open up firefox -> Tools -> Add Ons 

Then right click shockwave flash and disable it. Then you are going to want to stick that new flashplayer plugin in the mozilla plugin folder.  

The file you are looking for should look something like this:  libflashplayer.so

You want to put that *.so file in 
Places-> Home-> .mozilla-> plugins or in /usr/lib/mozilla/plugins/

What I did to get flash player ten is this:
cp /usr/lib/flashplayer-mozilla/libflashplayer.so /usr/lib/mozilla/plugins/

---

### Post by Paddy Landau on 2009-08-06
Here's what I started with:

[LIST]
[*] /usr/lib/flashplayer-mozilla/ -- Directory doesn't exist.
[*] /usr/lib/adobe-flashplugin/ -- Contains libflashplayer.so.
[*] /usr/lib/mozilla/plugins/ -- Contains flashplugin-alternative.so, which is a link to /etc/alternatives/mozilla-flashplugin, which is a link to /usr/lib/adobe-flashplugin/libflashplayer.so.
[*] ~/.mozilla/plugins/ -- Contains libflashplayer.so.
[/LIST]
 So, following your instructions and with a little experimentation, I had to do the following.

[LIST]
[*] Disable Shockwave Flash v9.0 r124
[*] Rename /usr/lib/mozilla/plugins/flashplugin-alternative.so to libflashplayer.so
[*] Delete ~/.mozilla/plugins/libflashplayer.so
[*] Link /usr/lib/adobe-flashplugin/libflashplayer.so as /usr/lib/mozilla/plugins/libflashplayer.so
[*] Restart Firefox at least twice
[*] Enable Shockwave Flash v10.0 r32
[/LIST]
 I think the thing that got me flustered was the fact that Firefox had to be closed and restarted at least twice whenever making a change. It wasn't making sense without that.

I also don't understand why it didn't work when I had flashplugin-alternative.so, which linked (indirectly) to /usr/lib/adobe-flashplugin/libflashplayer.so, whereas when I have libflashplayer.so linking to the same file, then it works.

Anyway, it works now, so thank you for your help.

---

