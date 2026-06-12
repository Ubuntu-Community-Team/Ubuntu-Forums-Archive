---
title: "Black Screen when logging out or running full screen apps"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by SirDucky on 2009-02-03
Hello all,

I'm a fairly new linux user.

I've been getting this bug (ever since the initial installation):

Very frequently (I would say 80% of the time), I just see a black screen when I: 
[LIST]
[*]press MENU->SYSTEM->LOG OUT (USER)
[*]run a full screen app
[/LIST]

The sound still works, I can hear the little 'logout' sound and if I type in a new username and password it will make the 'login' sound as well, but the screen will stay black.  Same thing with full screen apps.  I can hear any sounds that they play, I just can't see anything.  Some apps this has happened with are:
[LIST]
[*]Saeurbraten
[*]Vega Strike
[*]gl-117
[/LIST]

I can press 'ctrl-alt-F#' and successfully switch to a terminal window.

I usually fix the problem by restarting from a terminal window.

Between the sound and the being able to switch to the terminal window, I've pretty much concluded that it's some problem with gnome and/or my graphics card driver.

Computer specs:
Ubuntu 8.10 fully updated
Intel X86 dual-core processor
NVidia 9300 built-in motherboard GPU
full desktop effects enabled
Dust theme

A little note on my NVidia driver:  I tried first to use the nvidia driver distributed on synaptic.  However, I was never able to get that to work, so I downloaded a driver from nvidia.com that did the trick.  It only installs when the X terminal isn't running, but was is a pretty straightforward process.

Any suggestions on what to try guys?

---

### Post by primaxx on 2009-02-03
This is just a wild shot, but have you tried to set "Visual Effects" to *none*? (You'll find it under System->Preferences->Appearance And then the tab "Visual Effects".)

---

### Post by SirDucky on 2009-02-03
Yes, I've tried that but the problem still persists with the same symptoms.

---

### Post by rybaxs on 2009-02-03
wooh.. its 64bit x86 dual core right?

try to install 64bit installer, what version of xbit your installer had?

---

### Post by SirDucky on 2009-02-03
you're right.  I used a 32 bit installer.  Didn't even think of that.  Could that cause the symptoms?

---

### Post by SirDucky on 2009-02-05
Bump.  I don't want to reinstall on the 64bit unless I have to, and I'm skeptical that this is what's causing the problem.  Don't 64 bit processors come with a 32 bit compatibility mode?

---

