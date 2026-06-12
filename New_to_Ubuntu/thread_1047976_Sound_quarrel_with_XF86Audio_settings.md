---
title: "Sound quarrel with XF86Audio settings"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by midgetwithamatch on 2009-01-22
I have a logitech keyboard that houses a scroll bar, well circle more like it, that allows me to adjust the system volume by scrolling it left or right. The exact model is Logitech mx700. Anyways the system by default works with the keyboard and everything works as far as when I scroll it, it does indeed adjust the sound. My problem is that when I reboot my computer it doesn't store what I previously had the volume set to and is set at 100%. I think this may be because my master volume always shows 100% in my Gnome Volume Control applet. 

So I went to checkout what the keyboard shortcut was for the scroller and it says XF86AudioLowerVolume, and XF86AudioRaiseVolume. 

I was wondering if there was a way to carry my XF86Audio setting from one boot to the next?

---

### Post by ibuclaw on 2009-01-23
Ubuntu should already do this with the initscripts in /etc/init.d on boot.

Do you have alsa-utils installed?
```
sudo apt-get install alsa-utils
```

Though if you want to do it manually, have a look at the following two commands:
```
sudo alsactl store
```
Saves all soundcard information to **/var/lib/alsa/asound.state**
```
sudo alsactl restore
```
Loads/resets all volume/parameters to their saved state.

Regards
Iain

---

### Post by midgetwithamatch on 2009-01-23
> **tinivole said:**
> Ubuntu should already do this with the initscripts in /etc/init.d on boot.

Do you have alsa-utils installed?
```
sudo apt-get install alsa-utils
```

Though if you want to do it manually, have a look at the following two commands:
```
sudo alsactl store
```
Saves all soundcard information to **/var/lib/alsa/asound.state**
```
sudo alsactl restore
```
Loads/resets all volume/parameters to their saved state.

Regards
Iain

It does indeed store the alsactl on system shutdown / reboot. I cat'd the contents of /etc/init.d/alsautils and browsed the script it does successfully save the state of the system volume. But I think where I am running into trouble is that the sound that is being adjusted is not the same as the one that appears on my Gnome panel. If I change the volume with my keyboard to 0% the applet on my Gnome panel will still show 100% which makes me think a secondary program is storing the sound volume, which I would assume would be XF86Audio or something referenced to XF86Audio. I have little to know experience with XF86Audio or keyboard shortcut configuration.

Maybe it would be more efficient if I found a way to change the system volume through another keyboard shortcut than 'XF86AudioLowerVolume' and 'XF86AudioRaiseVolume'?

Oh and yes I do indeed have the alsa-utils package installed.
```
alsa-utils is already the newest version.

```

---

