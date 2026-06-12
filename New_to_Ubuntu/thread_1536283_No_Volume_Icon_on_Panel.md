---
title: "No Volume Icon on Panel"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-22
The volume icon on my top panel has disappeared. I tried: Add to Panel | Notification Area. But that didn't work. Then I tried resetting my panels completely by using $ rm -r ~/.gconf/apps/panel. Also didn't work. How can I get it back?

For some reason the sound stopped working about the time the icon disappeared, but then I ran $ alsamixer, and it worked again.

---

### Post by kmsalex on 2010-07-22
The sound applet is contained in "Indicator Applet", try adding that from the "add to panel" option.

---

### Post by cjv8888 on 2010-07-22
try installing gnome-volume-control from synaptic.

---

### Post by EnigmaticCoder on 2010-07-22
I added the indicator applet to the panel, but it just duplicated the email icon. The volume icon is still missing. I also tried installing gnome-volume-control from synaptic, but it didn't show up in the search (also, I'd prefer the volume manager that comes with Ubuntu, although I'd settle with it if it worked).

---

### Post by lidex on 2010-07-22
Try this 
Make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session
```
Now reset your panels:
```
gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Next right-click on your panel and select 'Add to panel' and add back items that are missing. Indicator applet I believe should have volume control, but you may need to play around as there are three indicator entries in my add list. You may want to search synaptic for 'applet' to find any that are not in the list as they have to be installed to appear there.

---

### Post by EnigmaticCoder on 2010-07-22
Followed your instructions, lidex, but the volume icon is still missing.

---

### Post by lidex on 2010-07-22
OK. Now this. Re-install pulse:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```

Remove config:
```
rm -r ~/.pulse
```

**Reboot**

---

### Post by Elfy on 2010-07-22
Try adding indicator-sound 

```
sudo apt-get install indicator-sound 
```

Might need a logout.

---

### Post by lidex on 2010-07-22
> **forestpiskie said:**
> Try adding indicator-sound 

```
sudo apt-get install indicator-sound 
```

Might need a logout.
Good eye.

---

### Post by EnigmaticCoder on 2010-07-22
> **forestpiskie said:**
> Try adding indicator-sound 

```
sudo apt-get install indicator-sound 
```

Might need a logout.

That worked!

---

