---
title: "problem with sound"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by grobar87 on 2010-04-06
Hi!
When i listen music on xmms and try to open something on youtube...i got some soundcard error.I must first to turn off my xmms and then play video on youtube,or must first close youtube and then play mp3 on xmms.I can't play mp3 and video in same time.
Can anyone help me with this?

---

### Post by grobar87 on 2010-04-06
help anyone?

---

### Post by -humanaut- on 2010-04-06
When you click the mixer button (or whatever ubuntu calls it) make sure that proper sound card is selected.

---

### Post by CLEARviewF on 2010-04-06
First of all, i do not like XMMS, I use Exaile. Second: It could be a problem of XMMS, because I have the same Karmic and no problems with sound system. Are you using Sound System by default? I mean, using PulseAudio? Do you use surround?

---

### Post by lidex on 2010-04-06
Make sure pulseaudio is set up correctly here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

And this:
> XMMS 

To use XMMS with PulseAudio as audio server install xmms-pulse. To activate it this output plugin, edit ~/.xmms/config and change the line starting with output_plugin=:

[xmms]
...
output_plugin=/usr/lib/xmms/Output/libxmms-pulse.so
...

Alternatively use the configuration dialog of XMMS (like most sane people would probably do...). 

---

### Post by grobar87 on 2010-04-06
tnx.the problem was xmms on other player everything work fine.

---

### Post by lidex on 2010-04-06
> **CLEARviewF said:**
> First of all, i do not like XMMS, I use Exaile<snip>

Failure to see how that helps :confused:

---

