---
title: "Mouse glitch in Opera 10.10 in Flash apps"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by PunkLV on 2010-05-19
Hello. So I've upgraded my ubuntu to 10.04 smoothly and everything went cool, until I've noticed that now whenever I want to play/pause, adjust volume, click anywhere on a flash app (youtube, games, etc) mouse clicks do nothing.

Temporaly solution was to loose focus on flash-app by clicking anywhere and then I get a one more click in flash :)

My /home/../.opera had not been touched by the upgrade. So the question is: what has changed that could affect opera/mouse/flash plugins and does someone else has this issue?

---

### Post by tom.swartz07 on 2010-05-19
> **PunkLV said:**
> Hello. So I've upgraded my ubuntu to 10.04 smoothly and everything went cool, until I've noticed that now whenever I want to play/pause, adjust volume, click anywhere on a flash app (youtube, games, etc) mouse clicks do nothing.

Temporaly solution was to loose focus on flash-app by clicking anywhere and then I get a one more click in flash :)

My /home/../.opera had not been touched by the upgrade. So the question is: what has changed that could affect opera/mouse/flash plugins and does someone else has this issue?

Id be willing to bet youre running x64 Ubuntu. Right? The not-clicking thing is a common symptom. You could actually click with the middle-button at any time.

Follow the link in my signature to install the most recent version of Flash player for Ubuntu x64 computers. Its a bit of copy and paste, but once you do it, Opera will recognize it from the other browser plugin folders and use it.

---

### Post by PunkLV on 2010-05-19
Thanks for the reply.

No, I'm running x32. And 've tried middle-click right now - does not work either.

But here's a fun thingie. If I change mouse pointer style it stays the same, however, it instantly changes when I focus on flash app.

---

### Post by emanuel.b on 2010-05-19
I'm using opera 10.50 beta 32-bit and it's working just fine. I suggest you try it out. :)

[http://www.opera.com/browser/next/]("http://www.opera.com/browser/next/")

---

### Post by tom.swartz07 on 2010-05-19
> **PunkLV said:**
> Thanks for the reply.

No, I'm running x32. And 've tried middle-click right now - does not work either.

But here's a fun thingie. If I change mouse pointer style it stays the same, however, it instantly changes when I focus on flash app.

hmmm... thats really interesting. Could you verify that its not just a problem with Opera? Try using firefox or chrome to see if it also affects the flash apps there

---

### Post by PunkLV on 2010-05-19
Pfft. I was totally sure that I had 10.52 installed, but turned out - I didn't.

Everything is fine now. And everything was fine in firefox as well.

Thank you guys. I'm off to sleep.

---

### Post by emanuel.b on 2010-05-19
> **PunkLV said:**
> Pfft. I was totally sure that I had 10.52 installed, but turned out - I didn't.

Everything is fine now. And everything was fine in firefox as well.

Thank you guys. I'm off to sleep.
Good to hear that everything's better! G'night! :D

---

### Post by PunkLV on 2010-05-27
Found another and much more suitable solution:
```
gedit .startopera.sh
```
```
#!/bin/bash
#Opera Flash fix
GDK_NATIVE_WINDOWS=TRUE opera;
```
Editing the launcher to
```
sh .startopera.sh
```

Sadly, some weird iBus-anthy bug still remains. "No input window" messg in any of operas/webpage input field.

---

