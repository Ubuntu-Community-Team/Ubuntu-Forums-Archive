---
title: "installed ubuntu 10.04 and lost Volume"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by hatridge on 2010-04-30
Hello, I updated from ubuntu 9.01 to 10.04 and lost my volume and mater volume on panel. I have lost volume control before and added it back by adding to panel and including notification. This time it is not working and I have lost all sound. Any suggestions?

---

### Post by Sealbhach on 2010-04-30
Go to System/Preference menu, right-click on Sound and select "Add this launcher to panel".

That's what I did.

.

---

### Post by nash black on 2010-04-30
I've had the same issue. Adding the above 'sound' to the panel does not seem to allow for adjustment of the sound directly from the icon. If you use AWN, then you could install its volume applet which acts the same as the old one you're referring to

---

### Post by pbateman on 2010-04-30
When I upgraded it seemed I had lost sound as well (although the volume icon was there). Turns out that the sound preferences had been reset. I just had to go to System>preferences>sound and make sure that the right sound card was selected under the 'output' tab (it wasn't so therefore I had no sound). Once i selected the right card sound came back...

Just something to look at...

---

### Post by Xoanan on 2010-04-30
Same here; no sound at all; I checked the card and I am running the Alsa mixer; The driver is the same. I can hear white noise but nothing else

---

### Post by gophergun on 2010-04-30
I'm in the same boat, my volume applet is gone upon updating, and since I'm on Netbook Remix, I can't find a way to put it back. For whatever reason, my volume hotkeys also don't work.

---

### Post by ugm6hr on 2010-05-01
For everyone posting here: Each of you would be best advised to start your own threads.

And clarify whether the problem is that you have no sound, or are unable to change the sound volume.

The simplest way to maximise all volumes is by using:
```
alsamixer
```

---

### Post by Paul T. on 2010-05-01
> **Sealbhach said:**
> Go to System/Preference menu, right-click on Sound and select "Add this launcher to panel".

That's what I did.

.

Thx for that :P

---

### Post by hatridge on 2010-05-01
solved thank you very much.

---

### Post by damormino on 2011-04-24
[LIST=1]
[*]1. Right-click on the panel where you'd like the volume controller to appear and select "Add to panel"
[*]2. Choose "Indicator Applet" from the list and click on "Add" and you're done. The volume control should be back.
[/LIST]

---

