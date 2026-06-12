---
title: "MIDI in Firefox: should I install Gecko Media Player or MPlayer-Plugin for Mozilla?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by VgnStirfry on 2009-06-03
I'm using Ubuntu 9.04 (Jaunty) and Firefox 3.0.10.  

While using Firefox, I came to a web page contained a MIDI file. 

The choices I was offered for plugin downloads are Gecko Media Player, and MPlayer-Plugin for Mozilla.  

Which is preferable, and why?

---

### Post by prvteprts on 2009-06-03
I'm not so sure about Gecko, but MPlayer seems popular. From posts online, it seems the MPlayer Mozilla plugin is the preferred replacement for flash. But I think you would have to uninstall the Totem plugin first, as it is the default.

Personally I use Mplayer. I checked the supported types, MIDI is one of them, however I haven't come across MIDI files using MPlayer yet. Also, in Firefox, MPlayer seems to be better than Totem in playing media streams as it shows the percent of media loaded, while Totem does not.

---

### Post by billgoldberg on 2009-06-03
Neither.

Just open up synaptic and install totem-mozilla  and restart firefox.

---

### Post by L a r r y on 2010-03-04
> **VgnStirfry said:**
> I'm using Ubuntu 9.04 (Jaunty) and Firefox 3.0.10.  

While using Firefox, I came to a web page contained a MIDI file. 

The choices I was offered for plugin downloads are Gecko Media Player, and MPlayer-Plugin for Mozilla.  

Which is preferable, and why?

I have Firefox 3.0 in Ubuntu 9.04, and the only thing I have found to play embedded midi files is this:

```
sudo apt-get install timidity mozplugger
```

I already have totem-mozilla installed; I re-installed it and restarted Firefox with no effect, and I installed mplayer plugin for firefox (mozilla-mplayer and all of its dependencies) with no effect.

I had to run this timidity install under Ubuntu 8.04 as well to get embedded midis to play.

---

